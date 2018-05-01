Deploy Backend Instances
------------------------

During the previous excercise we made use of the OpenStack CLI.  OpenStack also has a web gui, Horizon, that can be used.  The following will deploy two backend web servers that will be used later in the lab.

Launch Google Chrome and click on the “Login – OpenStack…” bookmark.

|image5|

|image6|

Login to Horizon (OpenStack GUI) using the username: demo, password:
demo

|image7|

You should see.

|image8|

Click on “Instances” and then “Launch Instance” (top right of page).

|image9|

For the Instance name specify “server” for the count enter “2”. Then
click next.

|image10|

Click on the “+” next to “f5demo”.Then click next.

|image11|

Click on the “+” next to “m1.tiny”. Then click next.

|image12|

Click on the “+” next to “internal” Network. This step should have been
completed for you since the internal network is the only network available.
Then click on next TWICE until you are on the Security Groups tab.

|image13|

On the Security Groups tab click on the “+” next to “default-allow-all”.
Then click next.

|image14|

Click on the “+” next to “demo-key-pair” and the click on “Launch
Instance”.  This step should have been completed for you since the
demo-key-pair is the only available key pair.

|image15|

You should now see them starting.

|image16|

Once the instance status is "active" on “server-1” then “Log” you should see

|image17|


.. |image5| image:: /_static/class1/image7.png
   :scale: 25%
.. |image6| image:: /_static/class1/image8.png
   :scale: 50%
.. |image7| image:: /_static/class1/image9.png
   :scale: 50%
.. |image8| image:: /_static/class1/image10.png
   :scale: 50%
.. |image9| image:: /_static/class1/image11.png
   :scale: 50%
.. |image10| image:: /_static/class1/image12.png
   :scale: 50%
.. |image11| image:: /_static/class1/image13.png
   :scale: 50%
.. |image12| image:: /_static/class1/image14.png
   :scale: 50%
.. |image13| image:: /_static/class1/image15.png
   :scale: 50%
.. |image14| image:: /_static/class1/image16.png
   :scale: 50%
.. |image15| image:: /_static/class1/image17.png
   :scale: 50%
.. |image16| image:: /_static/class1/image18.png
   :scale: 50%
.. |image17| image:: /_static/class1/image19.png
   :scale: 50%
