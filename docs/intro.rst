Getting Started
---------------

Please follow the instructions provided by the instructor to start your
lab and access your jump host.

.. NOTE::
	 All work for this lab will be performed exclusively from the Windows
	 jumphost. No installation or interaction with your local system is
	 required. You will use **Putty** that has been preconfigured with appropriate keys in
	 order to access the **DHD CLI**, **Good Client**, and the **Attacker** systems.
	 The shortcuts are on the desktop. You will be logged in as "root".

Lab Topology
~~~~~~~~~~~~

The following components have been included in your lab environment:

- 1 x F5 BIG-IP VE (v14.0) Provisioned as DHD
- 1 x Linux Attacker (Ubuntu 14.04)
- 1 x Linux Good Client (Ubuntu 14.04)
- 1 x Linux LAMP Webserver (xubuntu 14.04)
- 1 x Linux LAMP Auction site (xubuntu 14.04)
- 1 x Windows Jumphost

Lab Components
^^^^^^^^^^^^^^

+------------------------------------+-------------------------------+-----------------------+
|     **System**                     |     **Username**              |  **Password**         |
+====================================+===============================+=======================+
| Ravello                            |     Given at site             |     Given at site     |
+------------------------------------+-------------------------------+-----------------------+
| Win7 Jumpbox                       |     external\_user            |     f5DEMOs4u         |
+------------------------------------+-------------------------------+-----------------------+
| Hybrid Defender - WebUI            |     admin                     |     f5DEMOs4u         |
+------------------------------------+-------------------------------+-----------------------+
| Hybrid Defender - CLI              |     root                      |     f5DEMOs4u         |
+------------------------------------+-------------------------------+-----------------------+
| Good Client                        |     ubuntu                    |     Use key           |
+------------------------------------+-------------------------------+-----------------------+
| Attacker                           |     ubuntu                    |     Use key           |
+------------------------------------+-------------------------------+-----------------------+
| Auction CLI                        |     root                      |     default           |
+------------------------------------+-------------------------------+-----------------------+
| Lamp CLI                           |     root                      |     default           |
+------------------------------------+-------------------------------+-----------------------+
| Lamp X-Server Shell                |     xubuntu                   |     <no password>     |
+------------------------------------+-------------------------------+-----------------------+

Accessing the Lab Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Task 1 – Open your RDP client and connect to your Windows Jumpbox
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- A URL will be provided by your Instructor at the training site that will access the training portal.

- Click the Jumpbox RDP link.

 |image6|

 This will RDP to the Jumpbox where you will work all the labs from.

.. NOTE:: Use the show options to provide details.

- Login to the Jumpbox

-  User name: Jumpbox \ external\_user. Password: f5DEMOs4u

|image3|

-  Click YES at the warning

|image4|

.. NOTE:: All Exercises/Tasks are to be completed from the Windows Jumpbox. There are various shortcuts -- Chrome Incognito, Putty shortcuts, Licensing Folders on the jumpbox that you will use through the exercises.

|image5|

.. |image0| image:: /_static/image2.png
   :width: 5.30694in
   :height: 5.22014in
.. |image3| image:: /_static/image5.png
   :width: 2.98681in
   :height: 3.46042in
.. |image4| image:: /_static/image6.png
   :width: 2.92708in
   :height: 2.92708in
.. |image5| image:: /_static/image7.png
   :width: 5.30694in
   :height: 2.98681in
.. |image6| image:: /_static/image71.png
   :width: 6.64028in
   :height: 4.05694in
`
