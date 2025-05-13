:original_name: as_04_0104.html

.. _as_04_0104:

Response
========

Status Codes
------------

After sending a request, you will receive a response, including a status code, response header, and response body.

A status code is a group of digits, ranging from 1xx to 5xx. It indicates the status of a request.

For example, if status code **201** is returned for calling the API used to `obtain a user token <https://docs.sc.otc.t-systems.com/api/iam/en-us_topic_0057845583.html>`__, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-Type**.

The following shows the response header fields for the `obtain a user token <https://docs.sc.otc.t-systems.com/api/iam/en-us_topic_0057845583.html>`__. The **X-Subject-Token** header field is the desired user token. You can use the token to authenticate other API calls.

.. note::

   For security purposes, you are advised to set the token in ciphertext in configuration files or environment variables and decrypt it when using it.


.. figure:: /_static/images/en-us_image_0000001974561537.png
   :alt: **Figure 1** Header fields of the response to the request for obtaining a user token

   **Figure 1** Header fields of the response to the request for obtaining a user token

(Optional) Response Body
------------------------

This part is optional. The body of a response is often returned in structured format (for example, JSON or XML) as specified in the **Content-Type** header field. The response body transfers content except the response header.

The following is part of the response body for the API used to `obtain a user token <https://docs.sc.otc.t-systems.com/api/iam/en-us_topic_0057845583.html>`__.

::

   {
       "token": {
           "expires_at": "2019-02-13T06:52:13.855000Z",
           "methods": [
               "password"
           ],
           "catalog": [
               {
                   "endpoints": [
                       {
                           "region_id": "az-01",
   ......

If an error occurs during API calling, an error code and a message will be displayed. The following shows an error response body.

.. code-block::

   {
       "error_msg": The request message format is invalid.",
       "error_code": "AS.0001"
   }

In the response body, **error_code** is an error code, and **error_msg** provides information about the error.
