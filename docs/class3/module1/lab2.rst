Lab 2 – Configuring Hybrid Defender DDoS Device Protection
==========================================================

Task 1 – Verify Communication Through the DHD Device.
-----------------------------------------------------

- **PuTTY** to the **BIG-IP CLI** (10.1.1.245) from your jumpbox desktop shortcut and resize window by making it wider. You will be logged on as ``root``.

- At the **config** prompt, type (or copy and paste) the following
  command:

  ``tcpdump -i 0.0 host 10.1.20.12``

- **PuTTY** to the **Attacker** host from your jumpbox desktop shortcut. Accept the Warning.  Enter "ubuntu" as the user. I't will use **a pre-loaded public key** as the credentials.

- At the **config** prompt, type (or copy and paste) the following command:

  ``ping 10.1.20.12``

- Examine the **tcpdump** window and verify ICMP packets are flowing
  through the BIG-IP DHD.

The attacker can successfully communicate with a back-end resource behind the BIG-IP DHD.

.. NOTE:: The listener for the ICMP packets is the VLAN group.

- Cancel the ``ping`` command, then verify the ``tcpdump`` stops receiving ICMP packets, and then press **Enter** several times to clear the recent log entries.

Task 2 – Disable **Device-Level** DHD DoS Protection
----------------------------------------------------

- In the Configuration Utility, in the **DoS Configuration, Device Protection** section click **Network**.
|image205|
- On the left side of the page select the checkbox for **ICMPv4 flood**, **TCP SYN flood** and **UDP Flood**.

- At the bottom just below the last vector, chose the drop down **Set State** and then select **Disabled**.

.. HINT:: This is the new method for selecting and changing multiple items at one-time.

|image206|
- Navigate back to the top of the window and Select **Commit Changes to System**
|image209|
- On the Jumpbox in the **Attacker** PuTTY window type (or copy and paste) the following:

.. code-block:: console

  # sudo su
  # cd scripts
  # ls

These are some of the different scripts we’ll be using during the exercises to simulate DoS attacks.

- Type (or copy and paste) the following command:

  ``for i in {1..10}; do ./icmpflood.sh; done``

This script launches the Attack and then repeats for a total of ten occurrences.

- View the ``tcpdump`` window and verify that ICMP attack traffic is reaching the back-end server.

- Let the attack run for about 15 seconds before moving on.

- In the Configuration Utility, open the **DoS Configuration > DoS Overview (non HTTP)** page.

- View the Protection Profile and notice no results are returned. We disabled those vectors.

|image207|

- Navigate to **Visibility > Event Logs > DoS > Network >Events**.

|image208|

- Notice no logs are captured.  We could have chosen **Learn Only** or **Detect Only** and had different results. If you want to test, feel free.

.. NOTE:: If you want to run the other attacks, use the format above.  ./synflood.sh and udp_flood.sh behave similar.   If you are not seeing the traffic on the DHD Cli, Stop and Re-Start the tcpdump.

Both of these locations we will return to throughout this course to see how our DHD is viewing these attacks.

Task 3 – Re-enable **Device-Level** DHD DoS Protection
------------------------------------------------------

In this task you will re-configure **device-level** DoS protection and then issue the same command and review the results.

-  In the Configuration Utility, in the **DoS Configuration, Device Protection** section click **Network**.

- On the left side of the page select the checkbox for **ICMPv4 flood**, **TCP SYN flood** and **UDP Flood**.

- At the bottom just below the last vector, chose the drop down **Set State** and then select **Mitigate**.

.. NOTE:: You have the option of Learn Only and Detect Only as well.

-  Navigate back to the top of the window and Select **Commit Changes to System**

.. NOTE:: This returns the configuration back to factory supplied device level enforcement.


.. |image205| image:: /_static/DeviceProtection.PNG
   :width: 1887px
   :height: 779px
.. |image206| image:: /_static/SetState.PNG
   :width: 1448px
   :height: 298px
.. |image207| image:: /_static/ddosnomitigation.png
   :width: 1629px
   :height: 399px
.. |image208| image:: /_static/eventlognoevents.png
   :width: 1637px
   :height: 412px
.. |image209| image:: /_static/CommitChanges.PNG
   :width: 1643px
   :height: 404px
