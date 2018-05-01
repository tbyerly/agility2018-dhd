Module 3: Stitching Workflows from Class 1 into new Orchestratable Collections
==============================================================================

In the previous module we saw the example of stitching together the Authentication
Folder and some facts gathering. We will now stitch together the Postman
Collection from Class 1 and the Authentication Collection from Module 2. Once we
validate the new file we'll use f5-newman-wrapper to execute.

Stitching together the collections and workflows allows Super-NetOps engineers
the ability to start quickly Orchestrating calls running Automation workflows.
This also allows BIG-IP to be Orchestrated from upper level orchestration toolkits.

Using this structure allows you to build your own solutions, to manage BIG-IP
quickly as native REST calls are used.

.. NOTE:: If you are running this lab independent from Class 1 you will want
   to restore BIGIP-A from UCS ``bigip-a-module3.ucs``. Not restoring
   BIGIP-A will result in services unable to be accessed 
   and nodes/pool members unavailable. The steps for a UCS restore can
   be found under the **HOWTos: Index** in the content tree on the left
   side of the Lab Guide


.. toctree::
   :maxdepth: 1
   :glob:

   lab*
