Lab 1 – Start Baseline Traffic Generation
==============================================

Task 1 – Create Protected Objects that the baseline traffic will be targeting
-----------------------------------------------------------------------------

The DHD device wide protection is enforced for all traffic flowing through the device. For more granular
control, we use **Protected Objects** and configure mitigation settings for those objects to be enforced.

In this task you will configure **object-level** DoS protection, and then issue an attack and review the results.

-  In the BIG-IP Configuration Utility, open the **DoS Configuration >> Protected Objects** page and in the **Protected Objects** section click the
   **Create** dropdown and select **Protected Object"

|image212|

-  Configure the Protected Object using the following information, and then click **Create**.

   +------------------------+--------------------+
   | Name                   | Server5            |
   +========================+====================+
   | Destination Address    | 10.1.20.15         |
   +------------------------+--------------------+
   | Port                   | \* All Ports       |
   +------------------------+--------------------+
   | Protocol               | All Protocols      |
   +------------------------+--------------------+
   | Protection Profile:    | dos                |
   +------------------------+--------------------+
   | Eviction Policy:       | DHD_EvictPol       |
   +------------------------+--------------------+
   | VLAN(s):               | defaultVLAN        |
   +------------------------+--------------------+
   | Logging Profiles:      | local-dos          |
   +------------------------+--------------------+

- Click **Save**

   -  This protected object will be used for the Auto-Thresholding lab.

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

You can now use the new DHD Visibility page to view the Dashboard, Anaysis, Event Logs and Debugging info.

- In the Hybrid Defender WebUI, access the Visibility tab.

.. NOTE:: DoS Visibility Dashboard is not a real-time monitoring tool. Events are displayed, much like other AVR-based reporting, in 5 minute windows. Do not expect events to be shown here immediately after running an attack. Quicker/real-time monitoring of on-going
         DoS attacks is best accomplished in the DoS Event Logs and DoS Overview areas of the WebUI.

- You should see categories as:  Attack Duration, Attacks, Virtual Severs, System Health and Countries.
Scroll through the Left Pane and explore the windows. Use the slider to shorten the timeframe if needed. You might have to hit refresh several times.

|image213|

- You should see the attacks in the timeline and a variety of details in the windows. Use the slider to shorten the timeframe if needed.

|image216|

- In the **Attack Duration** window view the attack. Hover over for more details.

|image217|

- Scroll down in the left-side of the page to view the **Attacks** section.

- View the details at the bottom of the **Attacks** section.

This table displays details of each attack that has occurred.

- Examples are; Attack ID, Severity, Vector, Trigger Virtual Server, Start Time, Stop Time...etc

- Scroll down in the left-side of the page to view the **Virtual Servers** section.

- You can see the details of protected object-level attacks.

- Examples are; Virtual Server, Server Latency, Health, Current Conections, Blocked IP's...etc

- Scroll down to the **System Health** section. This table displays the current health of the system.

- Scroll down to the **Countries** section. This table displays the attack details from each country.

Now focus on the Right Panel.

- View the various widgets in the panel on the right-side of the page. The top can be expaned and contracted visa the slider bar.

|image214|

- Click **Network** to filter out only the network-level attacks (all the attacks so far have been network-level).

|image215|

- If it’s not already expanded, expand the **Virtual Servers** widget, and then select **/Common/Server5**.

- This filters the results to only attacks at this protected object-level. Notice the changes to the map on in the **Countries** section.

- Continue to Explore and Scroll down the right side.  Notice each widget supplies greater detail.

.. |image212| image:: /_static/protectedobject.png
   :width: 1641px
   :height: 366px
.. |image213| image:: /_static/visibility.png
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
