:original_name: en-us_topic_0112331243.html

.. _en-us_topic_0112331243:

Creating a Bandwidth Scaling Policy
===================================

Scenarios
---------

You can automatically adjust your purchased EIP bandwidth and shared bandwidth using a bandwidth scaling policy. This section describes how to create a bandwidth scaling policy.

When creating a bandwidth scaling policy, you need to configure basic information. The system supports three types of bandwidth scaling policies: alarm-based, scheduled, and periodic.

The basic information for creating a bandwidth scaling policy includes the policy name, policy type, and trigger condition.

Creating a Scheduled or Periodic Bandwidth Scaling Policy
---------------------------------------------------------

#. Log in to the management console.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Bandwidth Scaling**.

#. Click **Create Bandwidth Scaling Policy**.

#. Set parameters, such as the policy name, policy type, and trigger condition. For details, see :ref:`Table 1 <en-us_topic_0112331243__table085923816615>`.

   .. _en-us_topic_0112331243__table085923816615:

   .. table:: **Table 1** Scheduled or periodic policy parameters

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                        | Example Value         |
      +=======================+====================================================================================================================================================================================================================================+=======================+
      | Region                | Specifies the region where the AS group resides.                                                                                                                                                                                   | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Policy Name           | Specifies the name of the bandwidth scaling policy.                                                                                                                                                                                | as-policy-p6g5        |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | The name consists of only letters, digits, underscores (_), and hyphens (-).                                                                                                                                                       |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | EIP                   | Specifies the public network IP address whose bandwidth needs to be scaled.                                                                                                                                                        | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Policy Type           | Specifies the policy type. You can select a scheduled or periodic policy.                                                                                                                                                          | N/A                   |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | If you select **Periodic**, you are required to configure two more parameters:                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Time Range                                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    Specifies a time range during which the AS policy can be triggered.                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Period                                                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    -  Day                                                                                                                                                                                                                          |                       |
      |                       |    -  Week                                                                                                                                                                                                                         |                       |
      |                       |    -  Month                                                                                                                                                                                                                        |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Triggered At          | Specifies a time at which the AS policy is triggered.                                                                                                                                                                              | N/A                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Scaling Action        | Specifies the action to be performed.                                                                                                                                                                                              | N/A                   |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | The following scaling action options are available:                                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Add                                                                                                                                                                                                                             |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    When a scaling action is triggered, the bandwidth is increased.                                                                                                                                                                 |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Reduce                                                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    When a scaling action is triggered, the bandwidth is decreased.                                                                                                                                                                 |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       | -  Set to                                                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    The bandwidth is set to a fixed value.                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |    .. note::                                                                                                                                                                                                                       |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |       The step (minimum unit for bandwidth adjustment) varies depending on the bandwidth value range. The bandwidth will be automatically adjusted to the nearest value according to the actual step.                              |                       |
      |                       |                                                                                                                                                                                                                                    |                       |
      |                       |       -  If the bandwidth is less than or equal to 300 Mbit/s, the default step is 1 Mbit/s.                                                                                                                                       |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Cooldown Period       | Specifies a period of time in the unit of second after each scaling action is complete. During the cooldown period, scaling actions triggered by alarms will be denied. Scheduled and periodic scaling actions are not restricted. | 300s                  |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. After setting the parameters, click **Create Now**.
