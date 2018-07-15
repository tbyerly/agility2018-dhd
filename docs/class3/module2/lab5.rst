Lab 5 – Configuring L7  Behavioral Attack Protection
====================================================

In this exercise we will use a protected object and analyze how the |dhd| reacts and mitigates L7 attacks based on Behavioral Analysis.

Task 1 – Create Protection Profile for Dos Behavioral Object
------------------------------------------------------

- In the BIG-IP Configuration Utility, open the **DoS Configuration >> Protection Profiles** page and click the
   **Create** button.

- Name the profile dos_behavioral and **select** the HTTP Families. *Click the HTTP Vector page to configure.
Click "Behavioral Bad Actor". The Fly Out opens and unselect "Bad Actor Detection".

- **Click** The "HTTP Group Configuration" Place the "Operation Mode" into Blocking and the "Behavioral Base Attributes" into Standard Mitigation and Signatue Detection Selected.
This places this profile into a behavioral based detection profile.

Task 2 – Create Protected Object and Launch Attack
--------------------------------------------------

- In the BIG-IP Configuration Utility, open the **DoS Protection > Quick Configuration** page and in the Protected Objects section click
   **Create**.

- Configure a protected object using the following information, and then click **Save**.

+------------------------+-----------------------------+
| Name                   | Auction                     |
+------------------------+-----------------------------+
| Destination Address    | 10.1.20.11                  |
+------------------------+-----------------------------+
| Service Port           | 80                          |
+------------------------+-----------------------------+
| Protocol               | TCP                         |
+------------------------+-----------------------------+
| Service Profile:       | DHD_http                    |
+------------------------+-----------------------------+
| Protection Profile:    | dos_behavioral              |
+------------------------+-----------------------------+
| VLAN(s)                | default_VLAN                |
+------------------------+-----------------------------+
| Logging Profile(s)     | local-dos                   |
+------------------------+-----------------------------+

|image500|

.. WARNING:: Name needs to be exact or demo will fail.

- Next we need to modify the VS we created earlier to pass traffic.

- At the bottom of the Menu **Click** the "Show Advanced Menu"" >> Local Traffic >> Virtual Servers >> Virtual Server List >> Select the Auction Server.

- Under ""Configuration"" Select **Advanced**
- Ensure the following are Set:
  -Source Address translation to none
  -Uncheck Address translation
  -Uncheck Port translation
  -Set Transparent Next Hop to the Internal Interface Bridge Member of the VLAN (mbr931)

-To figure out interface type "tmsh list net vlan" You want the next hope to be the internal interface.

- Click **Update**

- From the Good Client CLI, issue the following command.

.. code-block:: console

  ~/scripts/generate_clean_traffic.sh

Make sure you are receiving Status Code 200.

.. NOTE::  This will need to run for approximately 10 minutes.

- From the DHD CLI issue the following commands:

.. code-block:: console

   #/root/scripts/l7bdos-reset.sh
   #/root/scripts/l7-mon.sh

- Monitor the window.  When you see the following number go to 100, you will move on.

|image502|

- The health of the Protected Object will be shown. In general, a healthy system will show a value around .45. If the value is .5 consistently, then for some reason no learning is occurring and you should check your configuration and verify that baselining traffic is hitting the protected object in  question.

- If the system has detected and is mitigating and attack, or not. This will show in the output of ‘info.attack’ signal. The two numbers in brackets indicate if there is an attack (1 = yes, 0 = no) and if the system is mitigating that attack (1 = yes, 0 = no).

- The output will also include the ‘info.learning’ signal, which includes 4 comma-separated values that show the status of the admd behavioral dos learning:

|image99|

- signal values: [baseline_learning_confidence, learned_bins_count , good_table_size , good_table_confidence]

- baseline learning_confidence in % - How confident the system is in the baseline learning.

- This should be between 80% - 90%

- learned_bins_count - number of learned bins

- This should be > 0

- good_table_size - number of learned requests

- This should be > 4000

- good_table_confidence - how confident, as a percentage, the system is in the good table.

- It must be 100% for behavioral signatures.

- From the Attacker CLI issue the following command:

.. code-block:: console

   ~/scripts/http_flood.sh

|image92|

- Choose option **1**, "Attack Auction"

- You will see the attack start in the DHD SSH window:

|image501|

- In addition you will see the good client start returning a status of 000 as it is unresponsive. It no longer returns a Status 200. Until the DHD starts mitigation.

|image97|

- Explore Dos Configuration >> Protected Objects.  Click on the "Attack Status" to expand.

|image503|

- Let this run for 2 minutes.  Stop the attack by pressing "Enter"" a couple of times in the **Attacker** window the choosing option "3" to stop the "Attack"

.. NOTE:: The DHD does not record the end of the attack right away, it is very conservative, therefore you may have to wait 5 minutes to see the results.

- Look at the Event Logs.

|image504|

- Look at the Signature created.  Advanced Menu >> Security >> Dos Protection >> signatures

|image505|


- This concludes the DHD Hands on Labs.

.. |image500| image:: /_static/behavioralinitial.png
   :width: 1639px
   :height: 295px
.. |image501| image:: /_static/behavioralunderattack.png
   :width: 953px
   :height: 283px
.. |image502| image:: /_static/behavioralhealthclimbing.png
   :width: 963px
   :height: 573px
.. |image503| image:: /_static/behavioraldosexpanded.PNG
   :width: 1855px
   :height: 791px
.. |image504| image:: /_static/behavioraleventlog.PNG
   :width: 1522px
   :height: 353px
.. |image505| image:: /_static/behavioralsig2.png
   :width: 1835px
   :height: 648px
.. |image92| image:: /_static/image58.png
   :width: 4.590033in
   :height: 1.17006in
.. |image97| image:: /_static/image68.png
   :width: 6.37000in
   :height: 4.32068in
.. |image99| image:: /_static/image63.png
   :width: 6.54000in
   :height: 0.68068in
