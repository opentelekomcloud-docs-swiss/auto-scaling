:original_name: as_06_0205.html

.. _as_06_0205:

Batch Deleting AS Configurations
================================

Function
--------

This interface is used to batch delete AS configurations.

-  AS configurations used by AS groups cannot be deleted.
-  A maximum of 50 AS configurations can be deleted at a time.

URI
---

POST /autoscaling-api/v1/{project_id}/scaling_configurations

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

.. table:: **Table 2** Request parameters

   +--------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory | Type             | Description                                                                                         |
   +==========================+===========+==================+=====================================================================================================+
   | scaling_configuration_id | Yes       | Array of strings | Specifies the AS configuration ID. For details, see :ref:`Querying AS Configurations <as_06_0202>`. |
   +--------------------------+-----------+------------------+-----------------------------------------------------------------------------------------------------+

Example Request
---------------

This example deletes the AS configurations with IDs **config1** and **config2** in a batch.

.. code-block:: text

   POST https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_configurations

   {
       "scaling_configuration_id": [
           "config1",
           "config2"
       ]
   }

Response
--------

None

Example Response
----------------

None

Returned Values
---------------

-  Normal

   204

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
