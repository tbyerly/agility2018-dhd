Lab 3 – Start Baseline Traffic Generation
==============================================

Task 1 – Create Protected Objects that the baseline traffic will be targeting
-----------------------------------------------------------------------------

The DHD device wide protection is enforced for all traffic flowing through the device. For more granular
control, we use **Protected Objects** and configure mitigation settings for those objects to be enforced.

In this task you will configure **object-level** DoS protection, and then issue an attack and review the results.

-  In the BIG-IP Configuration Utility, open the **DoS Configuration>> Pritected Objects** page and in the **Protected Objects** section click the
   **Create** dropdown and select **Protected Object"

|image210|

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

-  You will be logged in as user : ``root``. The session is preconfigured to
   authenticate with a certificate.

-  Start the auto-threshold baselining script with:

   .. code-block:: console

      # cd ~/scripts
      # ./baseline_l4.sh

.. |image210| image:: /_static/protectedobject.png
   :width: 1641px
   :height: 366px
.. |image30| image:: /_static/class2/image32.png
   :width: 5.30972in
   :height: 0.45031in
