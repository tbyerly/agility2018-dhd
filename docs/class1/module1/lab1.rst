Lab 1 – DDoS Hybrid Defender Setup
==================================

Estimated completion time: 45 minutes

Task 1 – Initial Set-up
-----------------------

- Open the Chrome web browser and access the DHD from the toolbar shortcut.

- Login to the BIG-IP Configuration Utility.

 .. NOTE:: When you first power up a F5 DHD device you would go through the
  steps of Licensing and Provisioning.  We have assigned the management
  IP, hostname, NTP and DNS servers.

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

- The architecture and design decsions shoul d ave been made already.
Based on F5 recommendations we are going to deploy this device in L2 Transparent Mode.

|image101|

- Click Network Setup in the left hand menu. Then Select Topology.
You will notice the various option you canselect based on the prior architecture decisions.

- Click **Create** om the upper right side.

- Fill outthe information from the table below.

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


Task 3 – Configure Silverline Signaling
---------------------------------------

- In the BIG-IP Configuration Utility, open the **DoS Protection >
  Quick Configuration** page.

-
Task 4 – Configure DHD Device Bandwidth Thresholds
--------------------------------------------------

- In the **DoS Protection > Quick Configuration** \page, open the
   **Protected Objects** page.

- In the **Network Protection** section click **Create**.

- Configure using following information, and then click **Save**.

  +--------------------------------------+-----------------+
  | **Maximum Bandwidth: Specify**       | 500             |
  +======================================+=================+
  | **Scrubbing Threshold: Type**        | Percentage      |
  +--------------------------------------+-----------------+
  | **1.20Scrubbing Threshold: Value**   | 75              |
  +--------------------------------------+-----------------+
  | **Advertisement Method**             | Silverline      |
  +--------------------------------------+-----------------+
  | **Scrubber Details: Type**           | Advertise All   |
  +--------------------------------------+-----------------+

  |image22|

- That completes the setup for BIG-IP DDoS Hybrid Defender with
  Silverline integration.

.. |image6| image:: /_static/image8.png
   :width: 6.64028in
   :height: 3.15377in
.. |image7| image:: /_static/image9.png
   :width: 6.64028in
   :height: 1.13399in
.. |image8| image:: /_static/image10.png
   :width: 6.44722in
   :height: 0.53333in
.. |image9| image:: /_static/image11.png
   :width: 6.64028in
   :height: 1.84583in
.. |image10| image:: /_static/image12.png
   :width: 6.64028in
   :height: 2.01931in
.. |image11| image:: /_static/image13.png
   :width: 6.64028in
   :height: 1.12569in
.. |image12| image:: /_static/image14.png
   :width: 4.83435in
   :height: 2.68715in
.. |image13| image:: /_static/image15.png
   :width: 6.51491in
   :height: 3.29901in
.. |image14| image:: /_static/image16.png
   :width: 6.51491in
   :height: 1.61067in
.. |image15| image:: /_static/image17.png
   :width: 5.82741in
   :height: 2.98196in
.. |image16| image:: /_static/image18.png
   :width: 6.64028in
   :height: 4.05694in
.. |image17| image:: /_static/image19.png
   :width: 5.20878in
   :height: 0.73340in
.. |image18| image:: /_static/image20.png
   :width: 6.14167in
   :height: 0.76803in
.. |image19| image:: /_static/image21.png
   :width: 3.88367in
   :height: 0.70006in
.. |image20| image:: /_static/image22.png
   :width: 3.57500in
   :height: 2.71750in
.. |image21| image:: /_static/image23.png
   :width: 6.64028in
   :height: 1.65186in
.. |image22| image:: /_static/image24.png
   :width: 6.64028in
   :height: 3.17847in
