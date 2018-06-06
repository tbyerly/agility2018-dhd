Lab 1 – DDoS Hybrid Defender Setup
==================================

Estimated completion time: 20 minutes

Task 1 – Initial Set-up
-----------------------

- Open the Chrome web browser and access the DHD from the toolbar shortcut.

- Login to the BIG-IP Configuration Utility.

 .. NOTE:: When you first power up a F5 DHD device you would normally go through the
  steps of Licensing and Provisioning and basic set-up.  We have licensed, assigned the management
  IP, hostname, NTP and DNS servers for you.

.. NOTE:: If you are familiar with the BIG-IP UI, You will notice the menus on the left are consolidated.
This is an indication you are working with a DDoS Hybrid efender device.

|image100|

  +----------------------------------------+--------------------------+
  | Host Name                              | <your name>.f5demo.com   |
  +========================================+==========================+
  | Root Account (Password and Confirm)    | f5DEMOs4u                |
  +----------------------------------------+--------------------------+
  | Admin Account (Password and Confirm)   | f5DEMOs4u                |
  +----------------------------------------+--------------------------+

- This will log you out. Log back in

  |image6|

- Click **Next** and explore **Resource Provisioning** page

.. NOTE:: The above task ensures that you are using a purpose built
  DDoS Hybrid Defender.  If you are familiar with other
  F5 Modules/Technology that you have used in the past, you will
  notice that we have none of those provisioned.

- When done click **Submit**.


Task 2 – DDoS Hybrid Defender Base Configuration
---------------------------------------------------------

- The architecture and design decsions should have been made already.
Based on F5 recommendations we are going to deploy this device in L2 Transparent Mode.

|image101|

- Click Network Setup in the left hand menu. Then Select Topology.
You will notice the various option you can select based on the prior architecture decisions.

- Click **Create** om the upper right side.

- Fill out the information from the table below.

- In the DVLAN Group Name fill in **defaultVLAN**.

- Configure the VLANs using following information, and then click
  **Done Editing**.

  +-----------------------+----------------------------------+
  | \ **Internal:         | 20                               |
  | VLAN Tag**            |                                  |
  +=======================+==================================+
  | **Internal:           | 1.2 Untagged                     |
  | Interfaces**          |                                  |
  +-----------------------+----------------------------------+
  | **Internal:           | 10.1.20.240/21 (Click **Add**)   |
  | IP Address / Mask**   |                                  |
  +-----------------------+----------------------------------+
  | **External:           | 10                               |
  | VLAN Tag**            |                                  |
  +-----------------------+----------------------------------+
  | **External:           | 1.1 Untagged (Click **Add**)     |
  | Interfaces**          |                                  |
  +-----------------------+----------------------------------+

  |image18|

- At the bottom of the page click **Finished** to create the default
  network.

- Open the **Network > DNS Resolvers > DNS Resolver** list page and
  click **Create**.

- Enter default\_DNS\_resolver and then click **Finished**.

- A DNS resolver is required by bot signatures to allow for proper
  detection of benign search engines such as Google and Bing.




.. |image6| image:: /_static/image8.png
   :width: 6.64028in
   :height: 3.15377in
.. |image18| image:: /_static/image20.png
   :width: 6.14167in
   :height: 0.76803in
.. |image100| image:: /_static/DDoSMenu.PNG
   :width: 6.64028in
   :height: 1.65186in
.. |image101| image:: /_static/GuidedConfig.PNG
   :width: 6.64028in
   :height: 3.17847in
