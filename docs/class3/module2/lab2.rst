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

- **DoS Configuration >> DoS Overview->ServerNet**
- **Visibility >> Dashboard**
- **Visibility >> Event Logs >> DoS >> Network >> Events**

- Access the **Attacker** shell and run the following commands/attack (if already in the folder just issue the command)

  .. code-block:: console
    # sudo su
    # cd ~/scripts
    # ./multivector.sh

- Click **Refresh** on the DoS Overview page. You will see some attacks mitigated by **Device Configuration** and some mitigated by the more specific settings on the **ServerNet Protected Object**.

  |image36|

Navigate to **Security->Event Logs->DoS->Network->Events**.

- Click on “custom search…” link.

- Drag one of the values from the “Attack Type” column into the custom
  search builder. From the Action column, drag Drop into the search
  builder. Click “Search”.

  |image37|

- Further explore the DoS Event logs. For example, clear the search and identify the “Stop” and “Start” times for an attack, etc.

.. |image212| image:: /_static/protectedobject.png
   :width: 1641px
   :height: 366px
   :height: 4.36042in
.. |image36| image:: /_static/image38.png
   :width: 6.41389in
   :height: 1.87424in
.. |image37| image:: /_static/image39.png
   :width: 6.41389in
   :height: 2.26358in
.. |image38| image:: /_static/image40.png
   :width: 6.41389in
   :height: 1.06667in
.. |image39| image:: /_static/image41.png
   :width: 6.41389in
   :height: 3.65347in
.. |image30| image:: /_static/image32.png
   :width: 6.20151in
   :height: 1.49784in
.. |image31| image:: /_static/image33.png
   :width: 3.26695in
   :height: 0.70006in
.. |image32| image:: /_static/image34.png
   :width: 2.28106in
   :height: 0.68981in
.. |image33| image:: /_static/image35.png
   :width: 4.90177in
   :height: 0.96655in
.. |image34| image:: /_static/image36.png
   :width: 3.06463in
   :height: 0.92886in
