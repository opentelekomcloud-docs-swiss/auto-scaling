:original_name: as_pro_0006.html

.. _as_pro_0006:

AS and Other Services
=====================

AS can work with other cloud services to meet your requirements for different scenarios.

:ref:`Figure 1 <as_pro_0006__fig0580646173411>` shows the relationships between AS and other services.

.. _as_pro_0006__fig0580646173411:

.. figure:: /_static/images/en-us_image_0282034671.png
   :alt: **Figure 1** Relationships between AS and other services

   **Figure 1** Relationships between AS and other services

.. _as_pro_0006__en-us_topic_0190954097_table1856812418720:

.. table:: **Table 1** Related services

   +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Service                      | Description                                                                                                                                                    | Interaction                                                              | Reference                                                                                     |
   +==============================+================================================================================================================================================================+==========================================================================+===============================================================================================+
   | Elastic Load Balance (ELB)   | After ELB is configured, AS automatically associates ECS instances to a load balancer listener when adding ECSs, and unbinds them when removing the instances. | ELB distributes traffic to all ECSs in an AS group.                      | :ref:`(Optional) Adding a Load Balancer to an AS Group <as_01_0102>`                          |
   |                              |                                                                                                                                                                |                                                                          |                                                                                               |
   |                              | For AS to work with ELB, the AS group and load balancer must be in the same VPC.                                                                               |                                                                          |                                                                                               |
   +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Cloud Eye                    | If an alarm-triggered policy is configured, AS triggers scaling actions when an alarm triggering condition specified in Cloud Eye is met.                      | AS scales resources based on ECS instance status monitored by Cloud Eye. | :ref:`AS Metrics <as_06_0105__en-us_topic_0042018317_table57136275115435>`                    |
   +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | ECS                          | ECS instances added in a scaling action can be managed and maintained on the ECS console.                                                                      | AS automatically adjusts the number of ECS instances.                    | :ref:`Dynamically Expanding Resources <as_04_0101>` and :ref:`Scheduled Scaling <as_04_0102>` |
   +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Cloud Trace Service (CTS)    | With CTS, you can record AS operation logs for view, audit, and backtracking.                                                                                  | Log audit                                                                | :ref:`Recording AS Resource Operations <as_06_0103>`                                          |
   +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Tag Management Service (TMS) | If you have multiple resources of the same type, TMS enables you to manage these resources more easily.                                                        | Tags                                                                     | :ref:`Adding Tags to AS Groups and Instances <as_06_0104>`                                    |
   +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
