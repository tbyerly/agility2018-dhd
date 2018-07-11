Lab 2 - Multi-vector Demo
=========================

In this simple demo you will launch a small number of network attacks and show the configuration, logging and reporting capabilities of the
F5® DDoS Hybrid Defender™. The point of this demo is to provide context for a UI walk-through with more live data.

Task 1 – Create a Protected Object that the Attacker will be targeting
----------------------------------------------------------------------

The DHD device wide protection is enforced for all traffic flowing through the device. For more granular
control, we use **Protected Objects** and configure mitigation settings for those objects to be enforced.

In this task you will configure **Object-Level** DoS protection for a network, simulating your Server Network and then issue an attack and review the results.

-  In the BIG-IP Configuration Utility, open the **DoS Configuration >> Protected Objects** page and in the **Protected Objects** section click the
   **Create** dropdown and select **Protected Object**.

|image220|

-  Configure the Protected Object using the following information, and then click **Create**.

   +------------------------+--------------------+
   | Name                   | ServerNet          |
   +========================+====================+
   | Destination Address    | 10.1.20.0/22       |
   +------------------------+--------------------+
   | Port                   | \*All Ports        |
   +------------------------+--------------------+
   | Protocol               | All Protocols      |
   +------------------------+--------------------+
   | Protection Profile:    | dos                |
   +------------------------+--------------------+
   | Eviction Policy:       | Leave Blank        |
   +------------------------+--------------------+
   | VLAN(s):               | defaultVLAN        |
   +------------------------+--------------------+
   | Logging Profiles:      | local-dos          |
   +------------------------+--------------------+

- Click **Save**

This protected object is defending all ports/protocols for 10.1.20.0/22, which is the network behind the Hybrid Defender. Attacks will be
launched at 10.1.20.12, which is an interface on the LAMP server.

- Click **Update** when finished.

You will now launch the attacks and show the behavior

- Open the following tabs in the DHD UI (Duplicate Tabs to make it easier):

- **DoS Configuration >> DoS Overview >> Filter Type >> Try Both DoS Attack and Device Dos**
- **Visibility >> Dashboard** change Dashboard to **Real Time** which is centered on the timeline.
- **Visibility >> Event Logs >> DoS >> Network >> Events**

- Access the **Attacker** shell and run the following commands/attack (if already in the folder just issue the command)

.. code-block:: console
  # sudo su
  # cd ~/scripts
  # ./multivector.sh

- Click **Refresh** on the DoS Overview page. Look at Explore both **DoS Attack and Device Dos**
|image36|
|image37|

Navigate to **Visibility >> Dashboard**. Explore the amount of rich data returned. Hover over the attacks. Scroll down and see what information is supplied.

|image38|

Navigate to **Visibility >> Event Logs >> DoS >> Network >> Events**

|image39|

- Further explore the DoS Event logs. For example, clear the search and identify the “Stop” and “Start” times for an attack, etc.

.. |image220| image:: /_static/protectedobject.png
   :width: 1641px
   :height: 366px
   :height: 4.36042in
.. |image36| image:: /_static/multivectordos.png
   :width: 1611px
   :height: 430px
.. |image37| image:: /_static/multivector.png
   :width: 1629px
   :height: 616px
.. |image38| image:: /_static/visibilitymultivector.png
   :width: 1580px
   :height: 841px
.. |image39| image:: /_static/visibilitylogs.png
   :width: 1535px
   :height: 648px
