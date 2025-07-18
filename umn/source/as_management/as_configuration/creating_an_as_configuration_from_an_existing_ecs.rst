:original_name: as_02_0102.html

.. _as_02_0102:

Creating an AS Configuration from an Existing ECS
=================================================

Scenarios
---------

You can use an existing ECS instance to rapidly create an AS configuration. In such a case, the parameter settings, such as the ECS type, vCPUs, memory, image, and disk settings (including size, encryption, key and type) in the AS configuration are the same as those of the selected instance by default.

Procedure
---------

#. Log in to the management console.

#. Under **Computing**, click **Auto Scaling**.

#. Click **Create AS Configuration**.

#. Set the parameters for the AS configuration. :ref:`Table 1 <as_02_0102__table27476571>` lists the AS configuration parameters.

   .. _as_02_0102__table27476571:

   .. table:: **Table 1** AS configuration parameters

      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Parameter              | Description                                                                                                                                                                                                                          | Example Value                         |
      +========================+======================================================================================================================================================================================================================================+=======================================+
      | Name                   | Specifies the name of an AS configuration.                                                                                                                                                                                           | ``-``                                 |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Configuration Template | Choose **Use specifications of an existing ECS** > **Select ECS**.                                                                                                                                                                   | Use specifications of an existing ECS |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | In such a case, the parameter settings, such as the ECS type, vCPUs, memory, image, and disk settings (including size, type, encryption, and key) in the AS configuration are the same as those of the selected instance by default. |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | EIP                    | An EIP is a static public IP address bound to an ECS in a VPC. Using the EIP, the ECS provides services externally.                                                                                                                  | Automatically assign                  |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | The following options are provided:                                                                                                                                                                                                  |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | -  Do not use                                                                                                                                                                                                                        |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    An ECS without an EIP cannot access the Internet. However, it can still be used as a service ECS or deployed in a cluster on a private network.                                                                                   |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | -  Automatically assign                                                                                                                                                                                                              |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    An EIP with a dedicated bandwidth is automatically assigned to each ECS. The bandwidth size is configurable.                                                                                                                      |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Key Pair               | A key pair is used for ECS login authentication. If you select this mode, create or import a key pair on the **Key Pair** page.                                                                                                      | ``-``                                 |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | .. note::                                                                                                                                                                                                                            |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    If you use an existing key, make sure that you have saved the key file locally. Without the key, you will not be able to log in to your instance.                                                                                 |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Advanced Settings      | This allows you to configure **User Data**.                                                                                                                                                                                          | ``-``                                 |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | You can select **Do not configure** or **Configure now**.                                                                                                                                                                            |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | User Data              | Enables an ECS to automatically inject user data when the ECS starts for the first time. This configuration is optional. If this function is enabled, the ECS automatically injects user data upon its first startup.                | ``-``                                 |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | The following two methods are available:                                                                                                                                                                                             |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | -  **As text**: allows you to enter the user data in the text box below.                                                                                                                                                             |                                       |
      |                        | -  **As file**: allows you to inject a script or other files when you create an ECS.                                                                                                                                                 |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    .. note::                                                                                                                                                                                                                         |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |       -  For Linux, if you use password authentication, this function is not supported.                                                                                                                                              |                                       |
      |                        |       -  If the selected image does not support user data injection, this function is not supported.                                                                                                                                 |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+

#. Click **Create Now**. A message is displayed indicating that the AS configuration is created successfully, and the system automatically redirects you to the **AS Configurations** page. The newly created AS configuration is displayed on the page.

#. If you want to use the newly created AS configuration, add it to the AS group. For details, see :ref:`Changing the AS Configuration for an AS Group <as_01_0103>`.
