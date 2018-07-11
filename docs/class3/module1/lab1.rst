Lab 1 – DDoS Hybrid Defender Setup
==================================

Estimated completion time: 20 minutes

Task 1 – Initial Set-up
-----------------------

- Open the Chrome web browser and access the DHD from the toolbar shortcut.

- Login to the BIG-IP Configuration Utility using the ''admin'' account.

|image200|

.. NOTE:: When you first power up a F5 DHD device you would normally go through the
  steps of licensing, provisioning and basic set-up.  We have licensed, assigned the management
  IP, hostname, NTP and DNS servers for you.

.. NOTE:: If you are familiar with the BIG-IP UI, You will notice the menus on the left are consolidated. This is an indication you are working with a DDoS Hybrid defender device.

|image201|
- If you need to access more options, there  is a shortcut at the bottom of the Menu page. **Show Advanced Menu**

|image211|
- Explore the **Resource Provisioning** page

|image202|

.. NOTE:: The above task ensures that you are using a purpose built DDoS Hybrid Defender.  If you are familiar with other
  F5 Modules/Technology that you have used in the past, you will notice that we have none of those provisioned.

- When done click **Submit**.


Task 2 – DDoS Hybrid Defender Base Configuration
---------------------------------------------------------

The architecture and design decisions should have been made already. Based on F5 recommendations we are going to deploy this device in L2 Transparent Mode.

- Click **Network** in the left hand menu. Then Select **Topology**.
- You will notice the various options you can select based on the prior architecture decisions.
- For this classes purpose **Click** on the VLAN Group image.
|image203|
- Click **Create** on the upper right side.

- Fill out the information from the table below. Then Click **Done Editing** within that section.

  +-----------------------+----------------------------------+
  | **VLAN Group Name:**  | defaultVlan                      |
  |                       |                                  |
  +-----------------------+----------------------------------+
  | **Internal:           | 20                               |
  | VLAN Tag**            |                                  |
  +-----------------------+----------------------------------+
  | **Internal:           | 1.2 Untagged (Click **Add**)     |
  | Interfaces**          |                                  |
  +-----------------------+----------------------------------+
  | **External:           | 10                               |
  | VLAN Tag**            |                                  |
  +-----------------------+----------------------------------+
  | **External:           | 1.1 Untagged (Click **Add**)     |
  | Interfaces**          |                                  |
  +-----------------------+----------------------------------+

|image204|
- At the bottom of the page click **Finished** to create the default network.

**This completes the initial Network Set-Up of DHD.**

.. |image201| image:: /_static/DDoSMenu.PNG
   :width: 1627px
   :height: 585px
.. |image203| image:: /_static/GuidedConfig.PNG
   :width: 1613px
   :height: 849px
.. |image200| image:: /_static/logon.png
   :width: 701px
   :height: 462px
.. |image202| image:: /_static/ResourceProvisioning.PNG
   :width: 1310px
   :height: 828px
.. |image211| image:: /_static/advancedmenu.png
   :width: 261px
   :height: 474px
.. |image204| image:: /_static/defaultVLANnoip.png
      :width: 1660px
      :height: 379px
