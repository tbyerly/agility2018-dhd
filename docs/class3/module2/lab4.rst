Lab 4 – Configuring L7 Attack Protection
========================================

In this exercise we will use a protected object and enforce mitigation for low and slow/encrypted layer 7 attacks.

.. NOTE:: We will first launch attacks with no protection to see the results.  Then enable protection and compare the results.

Task 1 – Use Firefox to access Website and use Attacker to bring it down.
-------------------------------------------------------------------------

- Open the following in separate tabs in the Hybrid Defender Web UI:

- **DoS Configuration >> Dos Overview**

- **Visibility >> Event Logs >> DoS >> Application Events**

- From a the **Firefox browser** on the jumphost go to https://10.1.20.11. Ignore SSL warning and Add Exception.

.. NOTE:: This bypasses the Hybrid Defender and accesses the server directly, showing the availability and/or performance of the site directly.

Click around a few links. This is the site we will launch an attack against and mitigate.

- Verify that the configuration is providing no L7 protections by taking the server offline with a slowloris attack.

.. NOTE:: Apache will try to clean up the slow flows, but they will do so inefficiently and the server is impacted (which will show as an outage, missing objects and/or slower responsiveness).

- Run the slowloris attack from the Attacker CLI:

.. code-block:: console

  # cd ~/scripts
  # ./slowloris.sh

- The tool will rapidly show the site offline (10-15 seconds, with trivial traffic load)

- Refresh https://10.1.20.11 to show the effects of the attack. CLick links on the page.

.. NOTE::  Since we are running locally from the Win7 system in a virtualized environment, you may be able to access the site, however it will be slower and often the GIFs will not load. An Internet user would not be able to “fight through” the attack to get to the server as often as a system on the local LAN.

- Stop the slowloris attack by using CTRL+C.

Start a more effective Slow Read attack.

This attack is harder for DoS mitigation tools to mitigate and can be very effective even with a tiny number of concurrent connections trickling in very slowly to the server to fly below the radar of network detections. In our example we will open 10 connections per second and
read the response data at 1 byte / sec. The attack would be effective even at 1 cps, it would just take a bit longer to build up the connections.

- From the **Attacker** CLI/shell start the slowread attack:

.. code-block:: console

  # cd ~/scripts
  # ./slowread.sh

As soon as the site is down (service available: NO) in the Attacker CLI, refresh https://10.1.20.11 to show that it is down/slow/intermittent.

- In the |dhd| GUI access the tabs you opened previously and notice no attacks were detected.

- Stop the slowread attack by using CTRL+C.

Task 2 – Create Protection Profile for Dos HTTP Object
------------------------------------------------------

- In the BIG-IP Configuration Utility, open the **DoS Configuration >> Protection Profiles** page and click the **Create** button.

- Name the profile dos_HTTPS and **select** the HTTP Vectors. **Click** the HTTP Vector page to configure. At the far right click the "edit" pencil.
Change the settings depicted in the image below.

|image402|

Task 3 – Create Protected Object
--------------------------------

- In the BIG-IP Configuration Utility, open the **DoS Configuration >> Protected Objects** page and in the **Protected Objects** section click the
   **Create** dropdown and select **Protected Object**.

|image401|

- Configure a protected object using the following information, and then click **Save**.

  +------------------------+-----------------------------+
  | Name                   | Server_HTTPS                |
  +------------------------+-----------------------------+
  | Destination Address    | 10.1.20.11                  |
  +------------------------+-----------------------------+
  | Service Port           | 443                         |
  +------------------------+-----------------------------+
  | Protocol               | TCP                         |
  +------------------------+-----------------------------+
  | Service Profile:       | http                        |
  +------------------------+-----------------------------+
  | Protection Profile:    | dos_HTTPS                   |
  +------------------------+-----------------------------+
  | VLAN(s)                | default_VLAN                |
  +------------------------+-----------------------------+
  | Logging Profile(s)     | local-dos                   |
  +------------------------+-----------------------------+




Task 4 – Configure Protection/Mitigation
----------------------------------------

- Next we need to modify the VS we created to pass traffic.

- At the bottom of the Menu **Click** the "Show Advanced Menu"" >> Local Traffic >> Virtual Servers >> Virtual Server List >> Select the Server_HTTPS VS.

- Under ""Configuration"" Select **Advanced**
- Ensure the following are Set:
- SSL Profile (Client) to **clientssl**
- SSL Profile (Server) to **serverssl**
- Source Address translation to **none**
- Uncheck Address translation
- Uncheck Port translation
-Set Transparent Next Hop to the Internal Interface Bridge Member of the VLAN. If you have followed along, it will be the interface associated with 1.2

- To figure out interface type "tmsh list net vlan" You want the next hope to be the internal interface.

- Click **Update**

Task 5 – Attack Website notice Mitigation/Protection
----------------------------------------------------
- From the **Attacker** CLI/shell start the slowread attack:

.. code-block:: console

  # cd ~/scripts
  # ./slowread.sh

- In the |dhd| GUI access the tabs you opened previously and notice no attacks were detected.

- Stop the slowread attack by using CTRL+C.

.. |image401| image:: /_static/protectedobject.png
   :width: 1641px
   :height: 366px
.. |image402| image:: /_static/dos_http5.png
   :width: 1410px
   :height: 713px
