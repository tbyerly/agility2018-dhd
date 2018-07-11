Lab 1 – Start Baseline Traffic Generation
==============================================

Task 1 – Create Protected Objects that the baseline traffic will be targeting
-----------------------------------------------------------------------------

The DHD device wide protection is enforced for all traffic flowing through the device. For more granular
control, we use **Protected Objects** and configure mitigation settings for those objects to be enforced.

In this task you will configure **object-level** DoS protection, and then issue an attack and review the results.

-  In the BIG-IP Configuration Utility, open the **DoS Configuration >> Protected Objects** page and in the **Protected Objects** section click the
   **Create** dropdown and select **Protected Object"**

|image212|

- Configure the Protected Object using the following information, and then click **Create**.

   +------------------------+--------------------+
   | Name                   | Server_General     |
   +========================+====================+
   | Destination Address    | 10.1.20.15         |
   +------------------------+--------------------+
   | Port                   | */ All Ports       |
   +------------------------+--------------------+
   | Protocol               | TCP                |
   +------------------------+--------------------+
   | Protection Profile:    | dos                |
   +------------------------+--------------------+
   | Eviction Policy:       | Blank              |
   +------------------------+--------------------+
   | VLAN(s):               | defaultVLAN        |
   +------------------------+--------------------+
   | Logging Profiles:      | local-dos          |
   +------------------------+--------------------+

- Click **Save**

-  This Protected Object will be used for the Auto-Thresholding lab.

Task 2 – Run Scripts to start L4 traffic generation – Good Traffic
------------------------------------------------------------------

-  Putty SSH (use the desktop shortcut) to open a shell to the **good client system**.

-  Accept the SSH Warning.

-  Enter "ubuntu" as the user. The session is preconfigured to authenticate with a certificate.

-  Start the auto-threshold baselining script with:

   .. code-block:: console

      # sudo su
      # cd ~/scripts
      # ./baseline_l4.sh

Task 3 – View the New Visibility Page
-------------------------------------

You can now use the new DHD Visibility page to view the Dashboard, Analysis, Event Logs and Debugging info.

- In the Hybrid Defender WebUI, access the Visibility tab.

.. NOTE:: DoS Visibility Dashboard defaults to not Auto-Refresh. Click the Button to set **Real-Time** to **on.**

- You should see categories as:  Attack Duration, Attacks, Virtual Severs, System Health and Countries.
Scroll through the Left Pane and explore the windows.
|image213|

- You can use the slider to shorten the time frame, or filter on the protocol, if desired when viewing attacks if needed.

|image216|

.. NOTE:: The windows will show no attack information.  We are running a L4 baseline tool.  Later labs will observe real-time attacks.

- Later when we have data and attacks, you will see the different attacks in the **Attack Duration** window. Hover over for more details.

|image217|

- Scroll down in the left-side of the page to view the **Attacks** section.

- View the details at the bottom of the **Attacks** section.

This table displays details of each attack that has occurred.

- Examples are; Attack ID, Severity, Vector, Trigger Virtual Server, Start Time, Stop Time...etc

- Scroll down in the left-side of the page to view the **Virtual Servers** section.

- You can see the details of **protected object**-level attacks.

- Examples are; Virtual Server, Server Latency, Health, Current Connections, Blocked IP's...etc

- Scroll down to the **System Health** section. This table displays the current health of the system.

- Scroll down to the **Countries** section. This table displays the attack details from each country.

Now focus on the Right Panel.

- View the various widgets in the panel on the right-side of the page. The top can be expaned and contracted visa the slider bar.

|image214|

- Click **Network** to filter out only the network-level attacks (all the attacks so far have been network-level).

|image215|

- If it’s not already expanded, expand the **Virtual Servers** widget, and then select **/Common/Server**.

- This filters the results to only attacks at this protected object-level. Notice the changes to the map on in the **Countries** section.

- Continue to Explore and Scroll down the right side.  Notice each widget supplies greater detail.

.. |image212| image:: /_static/protectedobject.png
   :width: 1641px
   :height: 366px
.. |image213| image:: /_static/dashboardoverview.png
   :width: 1666px
   :height: 599px
.. |image214| image:: /_static/image35.png
   :width: 639px
   :height: 126px
.. |image215| image:: /_static/image34.png
   :width: 639px
   :height: 126px
.. |image216| image:: /_static/image40.png
   :width: 1163px
   :height: 160px
.. |image217| image:: /_static/image41.png
   :width: 1093px
   :height: 548px
