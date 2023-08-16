:original_name: as_04_0104.html

.. _as_04_0104:

Response
========

Status Codes
------------

After sending a request, you will receive a response, including a status code, response header, and response body.

A status code is a group of digits, ranging from 1xx to 5xx. It indicates the status of a request.

For example, if status code 201 is returned for calling the API used to obtain a user token, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-type**.

:ref:`Figure 1 <as_04_0104__en-us_topic_0170155703_fig4865141011511>` shows the response header fields for the API used to obtain a user token. The **x-subject-token** header field is the desired user token. This token can then be used to authenticate the calling of other APIs.

.. _as_04_0104__en-us_topic_0170155703_fig4865141011511:

.. figure:: /_static/images/en-us_image_0172657663.png
   :alt: **Figure 1** Header fields of the response to the request for obtaining a user token

   **Figure 1** Header fields of the response to the request for obtaining a user token

(Optional) Response Body
------------------------

This part is optional. The body of a response is often returned in structured format (for example, JSON or XML) as specified in the **Content-Type** header field. The response body transfers content except the response header.

The following is part of the response body for the API used to obtain a user token. For the sake of limited space, only part of the content is displayed.

.. code-block::

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
       "error_msg": "The format of message is error",
       "error_code": "AS.0001"
   }

In the response body, **error_code** is an error code, and **error_msg** provides information about the error.
