Lab 2 - Multi-vector Demo
=========================

In this simple demo you will launch a small number of network attacks and show the configuration, logging and reporting capabilities of the
Hybrid Defender. The point of this demo is to provide context for a UI walkthrough with more live data live data.

Task 1 – Create a Protected Object that the Attacker will be targeting
----------------------------------------------------------------------

The DHD device wide protection is enforced for all traffic flowing through the device. For more granular
control, we use **Protected Objects** and configure mitigation settings for those objects to be enforced.

In this task you will configure **object-level** DoS protection, and then issue an attack and review the results.

-  In the BIG-IP Configuration Utility, open the **DoS Configuration >> Protected Objects** page and in the **Protected Objects** section click the
   **Create** dropdown and select **Protected Object"

|image212|

-  Configure the Protected Object using the following information, and then click **Create**.

   +------------------------+--------------------+
   | Name                   | ServerNet            |
   +========================+====================+
   | Destination Address    | 10.1.20.0/22         |
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

This protected object is defending all ports/protocols for 10.1.20.0/22, which is the network behind the Hybrid Defender. Attacks will be
launched at 10.1.20.12, which is an interface on the LAMP server.

- Click **Update** when finished.

You will now launch the attacks and show the behavior

- Open the following tabs in the DHD UI (Duplicate Tabs to make it easier):

- **DoS Configuration >> DoS Overview >> Filer Type >> Try Both DoS Attack and Device Dos**
- **Visibility >> Dashboard** Change Dashboard to **Real Time** Centered on the timeline.
- **Visibility >> Event Logs >> DoS >> Network >> Events**

- Access the **Attacker** shell and run the following commands/attack (if already in the folder just issue the command)

  .. code-block:: console
    # sudo su
    # cd ~/scripts
    # ./multivector.sh

- Click **Refresh** on the DoS Overview page. Look at Explore both **DoS Attack and Device Dos**

|image36|
|image37|

Navigate to **Visibility >> Dashboard**. Explore the amount of rich data returned.

|image38|

Navigate to **Visibility >> Event Logs >> DoS >> Network >> Events**

|image39|

- Further explore the DoS Event logs. For example, clear the search and identify the “Stop” and “Start” times for an attack, etc.

.. |image212| image:: /_static/protectedobject.png
   :width: 1641px
   :height: 366px
   :height: 4.36042in
.. |image36| image:: /_static/multivectordos.png
   :width: 1611px
   :height: 430px
.. |image37| image:: /_static/multivector.png
   :width: 1629px
   :height: 616px
.. |image38| image:: /_static/multivectordashboard.png
   :width: 1620px
   :height: 819px
.. |image39| image:: /_static/multivectoreventlogs.png
   :width: 1644px
   :height: 594px
