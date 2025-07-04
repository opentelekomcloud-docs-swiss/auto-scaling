:original_name: as_06_0201.html

.. _as_06_0201:

Creating an AS Configuration
============================

Function
--------

This API is used to create an AS configuration.

-  An AS configuration is a template specifying specifications for the instances to be added to an AS group.
-  The AS configuration is decoupled from the AS group. An AS configuration can be used by multiple AS groups.
-  Up to 100 AS configurations can be created for each user.

URI
---

POST /autoscaling-api/v1/{project_id}/scaling_configuration

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

.. table:: **Table 2** Request parameters

   +---------------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                       | Mandatory       | Type            | Description                                                                                                                                                                                            |
   +=================================+=================+=================+========================================================================================================================================================================================================+
   | scaling_configuration_name      | No              | String          | Specifies the AS configuration name. The name contains only letters, digits, underscores (_), and hyphens (-), and cannot exceed 64 characters.                                                        |
   +---------------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_config                 | No              | Object          | Specifies the ECS configuration. For details, see :ref:`Table 3 <as_06_0201__table5981573891121>`.                                                                                                     |
   +---------------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_scaling_configuration_id | No              | String          | Specifies the ID of the source AS configuration, which will be used together with **instance_config** to create a new AS configuration.                                                                |
   |                                 |                 |                 |                                                                                                                                                                                                        |
   |                                 |                 |                 | .. note::                                                                                                                                                                                              |
   |                                 |                 |                 |                                                                                                                                                                                                        |
   |                                 |                 |                 |    -  If **instance_id** is specified in **instance_config**, **instance_id** is preferentially used to create the new AS configuration, and **source_scaling_configuration_id** does not take effect. |
   |                                 |                 |                 |    -  If **instance_id** is not specified in **instance_config**, **source_scaling_configuration_id** and **instance_config** are used together to create the new AS configuration.                    |
   |                                 |                 |                 |                                                                                                                                                                                                        |
   |                                 |                 |                 |       -  If a parameter in **instance_config** is set to **null**, the corresponding setting of the source AS configuration takes effect.                                                              |
   |                                 |                 |                 |       -  If a parameter in **instance_config** is not set to **null** or left empty, this parameter overwrites the corresponding setting of the source AS configuration.                               |
   |                                 |                 |                 |                                                                                                                                                                                                        |
   |                                 |                 |                 |    -  If **source_scaling_configuration_id** is not specified, **scaling_configuration_name** and **instance_config** are mandatory.                                                                   |
   +---------------------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table5981573891121:

.. table:: **Table 3** **instance_config** field description

   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                    |
   +=================+=================+=========================================================================+================================================================================================================================================================================================================================================================================================================================================================================================+
   | instance_id     | No              | String                                                                  | Specifies the ECS ID. When you want to create an AS configuration from an ECS, specify this parameter. In this case, the **flavorRef**, **imageRef**, **disk**, and **security_groups** fields do not take effect.                                                                                                                                                                             |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | If the **instance_id** field is not specified, **flavorRef**, **imageRef**, and **disk** fields are mandatory.                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavorRef       | No              | String                                                                  | Specifies the ECS flavor ID. A maximum of 10 flavors can be selected. Use a comma (,) to separate multiple flavor IDs. You can obtain an ECS flavor ID from the API for querying details about flavors and extended flavor information.                                                                                                                                                        |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | imageRef        | No              | String                                                                  | Specifies the image ID. Its value is the same as that of **image_id** for specifying the image selected during ECS creation. You can obtain an image ID by calling the IMS API for querying images.                                                                                                                                                                                            |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | disk            | No              | Array of :ref:`disk <as_06_0201__table279810959126>` objects            | Specifies the disk group information. System disks are mandatory and data disks are optional. For details, see :ref:`Table 4 <as_06_0201__table279810959126>`.                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_name        | Yes             | String                                                                  | Specifies the name of the SSH key pair used to log in to the ECS.                                                                                                                                                                                                                                                                                                                              |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | personality     | No              | Array of :ref:`personality <as_06_0201__table3396587291242>` objects    | Specifies information about the injected file. Only text files can be injected. A maximum of five files can be injected at a time and the maximum size of each file is 1 KB. For details, see :ref:`Table 6 <as_06_0201__table3396587291242>`.                                                                                                                                                 |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | public_ip       | No              | :ref:`public_ip <as_06_0201__table105840310312>` object                 | Specifies the EIP of the ECS. The EIP can be configured in two ways. For details, see :ref:`Table 7 <as_06_0201__table105840310312>`.                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | -  Do not use an EIP. In this case, this parameter is unavailable.                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                         | -  Automatically assign an EIP. You need to specify the information about the new EIP.                                                                                                                                                                                                                                                                                                         |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_data       | No              | String                                                                  | Specifies the user data to be injected during the ECS creation process. Text, text files, and gzip files can be injected.                                                                                                                                                                                                                                                                      |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | Constraints:                                                                                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | -  The content to be injected must be encoded with base64. The maximum size of the content to be injected (before encoding) is 32 KB.                                                                                                                                                                                                                                                          |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | Examples:                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | -  Linux                                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         |    .. code-block::                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         |       #! /bin/bash                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                         |       echo user_test >> /home/user.txt                                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | -  Windows                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         |    .. code-block::                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         |       rem cmd                                                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                                                                         |       echo 111 > c:\aaa.txt                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | .. note::                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         |    Data injection is not supported for ECSs that use a Linux image and the password login mode.                                                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata        | No              | :ref:`metadata <as_06_0201__table6119722495435>` object                 | Specifies the ECS metadata. For details, see :ref:`Table 10 <as_06_0201__table6119722495435>`.                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | .. note::                                                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         |    -  This parameter is mandatory when a Windows ECS with password authentication is created.                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                                                                         |    -  This field does not allow users to write data. It is mandatory when the ECS is to be created using a Windows image.                                                                                                                                                                                                                                                                      |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_groups | No              | Array of :ref:`security_groups <as_06_0201__table144645712211>` objects | Specifies security groups. For details, see :ref:`Table 11 <as_06_0201__table144645712211>`.                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                         | If a security group is specified both in the AS configuration and AS group, scaled ECS instances will be added to the security group specified in the AS configuration. If a security group is not specified in either of them, scaled ECS instances will be added to the default security group. For your convenience, you are advised to specify the security group in the AS configuration. |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | market_type     | No              | String                                                                  | This parameter is reserved.                                                                                                                                                                                                                                                                                                                                                                    |
   +-----------------+-----------------+-------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table279810959126:

.. table:: **Table 4** **disk** field description

   +--------------------+-----------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type                                                  | Description                                                                                                                                                      |
   +====================+=================+=======================================================+==================================================================================================================================================================+
   | size               | Yes             | Integer                                               | Specifies the disk size. The unit is GB.                                                                                                                         |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       | The system disk size ranges from 1 to 1024 and must be greater than or equal to the minimum size (**min_disk** value) of the system disk specified in the image. |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       | The data disk size ranges from 10 to 32768.                                                                                                                      |
   +--------------------+-----------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type        | Yes             | String                                                | Specifies the ECS system disk type. The disk type must match the available disk type.                                                                            |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       | The value can be **SSD** or **SAS**.                                                                                                                             |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       | -  **SSD**: the ultra-high I/O type                                                                                                                              |
   |                    |                 |                                                       | -  **SAS**: the high I/O type                                                                                                                                    |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       | .. note::                                                                                                                                                        |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       |    -  For details about disk types, see **Disk Types and Performance** in the *Elastic Volume Service User Guide*.                                               |
   +--------------------+-----------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | disk_type          | Yes             | String                                                | Specifies a disk type. The options are as follows:                                                                                                               |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       | -  **DATA**: indicates a data disk.                                                                                                                              |
   |                    |                 |                                                       | -  **SYS**: indicates a system disk.                                                                                                                             |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       |    .. note::                                                                                                                                                     |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       |       System disk encryption is not supported.                                                                                                                   |
   +--------------------+-----------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_disk_image_id | No              | String                                                | Specifies the ID of a data disk image used to export data disks of an ECS.                                                                                       |
   +--------------------+-----------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id        | No              | String                                                | Specifies the disk backup snapshot ID for restoring the system disk and data disks using a full-ECS backup when a full-ECS image is used.                        |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       | .. note::                                                                                                                                                        |
   |                    |                 |                                                       |                                                                                                                                                                  |
   |                    |                 |                                                       |    Each disk in an AS configuration must correspond to a disk backup in the full-ECS backup by **snapshot_id**.                                                  |
   +--------------------+-----------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata           | No              | :ref:`metadata <as_06_0201__table24491331595>` object | Specifies the metadata for creating disks. For details, see :ref:`Table 5 <as_06_0201__table24491331595>`.                                                       |
   +--------------------+-----------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table24491331595:

.. table:: **Table 5** **metadata** Field Description for Creating Disks

   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type            | Description                                                                                                                  |
   +======================+=================+=================+==============================================================================================================================+
   | \__system__encrypted | No              | String          | Specifies encryption in **metadata**. The value can be **0** (encryption disabled) or **1** (encryption enabled).            |
   |                      |                 |                 |                                                                                                                              |
   |                      |                 |                 | If this parameter does not exist, the disk will not be encrypted by default.                                                 |
   |                      |                 |                 |                                                                                                                              |
   |                      |                 |                 | .. note::                                                                                                                    |
   |                      |                 |                 |                                                                                                                              |
   |                      |                 |                 |    System disk encryption is not supported.                                                                                  |
   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid     | No              | String          | Specifies the CMK ID, which indicates encryption in **metadata**. This parameter is used with **\__system__encrypted**.      |
   |                      |                 |                 |                                                                                                                              |
   |                      |                 |                 | .. note::                                                                                                                    |
   |                      |                 |                 |                                                                                                                              |
   |                      |                 |                 |    -  For details about how to obtain the CMK ID, see "Querying the List of CMKs" in *Key Management Service API Reference*. |
   |                      |                 |                 |    -  System disk encryption is not supported.                                                                               |
   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table3396587291242:

.. table:: **Table 6** **personality** field description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================+
   | path            | Yes             | String          | Specifies the path of the injected file.                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                           |
   |                 |                 |                 | -  For Linux OSs, specify the path, for example, **/etc/foo.txt**, for storing the injected file.                                                                                                         |
   |                 |                 |                 | -  For Windows, the injected file is automatically stored in the root directory of drive C. You only need to specify the file name, for example, **foo**. The file name contains only letters and digits. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content         | Yes             | String          | Specifies the content of the injected file.                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                           |
   |                 |                 |                 | The value must be the information after the content of the injected file is encoded using Base64.                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table105840310312:

.. table:: **Table 7** **public_ip** field description

   +-----------+-----------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                | Description                                                                                                             |
   +===========+===========+=====================================================+=========================================================================================================================+
   | eip       | Yes       | :ref:`eip <as_06_0201__table35964662103154>` object | Specifies the EIP automatically assigned to the ECS. For details, see :ref:`Table 8 <as_06_0201__table35964662103154>`. |
   +-----------+-----------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table35964662103154:

.. table:: **Table 8** **eip** field description

   +-----------+-----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                      | Description                                                                                                  |
   +===========+===========+===========================================================+==============================================================================================================+
   | ip_type   | Yes       | String                                                    | Specifies the EIP type.                                                                                      |
   +-----------+-----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | bandwidth | Yes       | :ref:`bandwidth <as_06_0201__table18754238103344>` object | Specifies the bandwidth of an IP address. For details, see :ref:`Table 9 <as_06_0201__table18754238103344>`. |
   +-----------+-----------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table18754238103344:

.. table:: **Table 9** **bandwidth** field description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================+
   | size            | Yes             | Integer         | Specifies the bandwidth (Mbit/s). The value ranges from 1 to 300.                                                                                          |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | .. note::                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 |    -  The specific range may vary depending on the configuration in each region. You can see the bandwidth range of each region on the management console. |
   |                 |                 |                 |    -  The minimum unit for bandwidth varies depending on the bandwidth range.                                                                              |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 |       -  The minimum unit is 1 Mbit/s if the allowed bandwidth size ranges from 0 to 300 Mbit/s (with 300 Mbit/s included).                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_type      | Yes             | String          | Specifies the bandwidth sharing type.                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Enumerated values of the sharing type:                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | -  **PER**: dedicated                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Only dedicated bandwidth is available.                                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | charging_mode   | Yes             | String          | Specifies the bandwidth billing mode.                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | **traffic**: billed by traffic.                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | If the parameter value is out of the preceding options, creating the ECS will fail.                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table6119722495435:

.. table:: **Table 10** **metadata** field description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================+
   | admin_pass      | No              | String          | Specifies the initial login password of the administrator account for logging in to an ECS using password authentication. The Linux administrator is **root**, and the Windows administrator is **Administrator**. |
   |                 |                 |                 |                                                                                                                                                                                                                    |
   |                 |                 |                 | Password complexity requirements:                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                    |
   |                 |                 |                 | -  Consists of 8 to 26 characters.                                                                                                                                                                                 |
   |                 |                 |                 | -  Contains at least three of the following character types: uppercase letters, lowercase letters, digits, and special characters ``!@$%^-_=+[{}]:,./?``                                                           |
   |                 |                 |                 | -  The password cannot contain the username or the username in reversed order.                                                                                                                                     |
   |                 |                 |                 | -  The Windows ECS password cannot contain the username, the username in reversed order, or more than two consecutive characters in the username.                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0201__table144645712211:

.. table:: **Table 11** **security_groups** field description

   ========= ========= ====== =======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================================
   id        Yes       String Specifies the ID of the security group.
   ========= ========= ====== =======================================

Example Request
---------------

This example creates an AS configuration with name **as-config-tlzp**, image ID **627a1223-2ca3-46a7-8d5f-7aef22c74ee6**, flavor ID **s3.xlarge.4**, **40 GB SATA** system disk, and SSH key name **100vm_key**.

.. code-block:: text

   POST https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_configuration

   {
       "scaling_configuration_name": "as-config-tlzq",
       "instance_config": {
           "flavorRef": "s3.xlarge.4",
           "imageRef": "627a1223-2ca3-46a7-8d5f-7aef22c74ee6",
           "disk": [
               {
                   "size": 40,
                   "volume_type": "SATA",
                   "disk_type": "SYS"
               }
           ],
           "key_name": "100vm_key" ,
       "security_groups": [{
           "id": "6c22a6c0-b5d2-4a84-ac56-51090dcc33be"
       }],
           "multi_flavor_priority_policy": "PICK_FIRST"
       }
   }

Response
--------

.. table:: **Table 12** Response parameters

   ======================== ====== ==================================
   Parameter                Type   Description
   ======================== ====== ==================================
   scaling_configuration_id String Specifies the AS configuration ID.
   ======================== ====== ==================================

Example Response
----------------

.. code-block::

   {
       "scaling_configuration_id": "f8327883-6a07-4497-9a61-68c03e8e72a2"
   }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Returned Value                    | Description                                                                                |
   +===================================+============================================================================================+
   | 400 Bad Request                   | The server failed to process the request.                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 401 Unauthorized                  | You must enter the username and password to access the requested page.                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 403 Forbidden                     | You are forbidden to access the requested page.                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 404 Not Found                     | The server could not find the requested page.                                              |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | You are not allowed to use the method specified in the request.                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The response generated by the server could not be accepted by the client.                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | You must use the proxy server for authentication to process the request.                   |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The request timed out.                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request could not be processed due to a conflict.                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | Failed to complete the request because of an internal service error.                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | Failed to complete the request because the server does not support the requested function. |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | Failed to complete the request because the request is invalid.                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | Failed to complete the request because the system is unavailable.                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | A gateway timeout error occurred.                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <as_07_0102>`.
