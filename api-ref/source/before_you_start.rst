:original_name: en-us_topic_0045219159.html

.. _en-us_topic_0045219159:

Before You Start
================

Welcome to *Auto Scaling API Reference*. Auto Scaling (AS) is a service that automatically adjusts resources (Elastic Cloud Server resources) based on your service requirements and configured AS policies. You can specify AS policies based on service requirements. These policies free you from having to repeatedly adjust resources to keep up with service changes and demand spikes, helping you reduce resource and labor costs. This document describes how to use application programming interfaces (APIs) to perform operations on AS groups, such as creating, deleting, or modifying AS groups. For details about all supported operations, see :ref:`API Overview <as_03_0100>`.

If you plan to access AS through an API, ensure that you are familiar with AS concepts. For details, see *Auto Scaling User Guide*.

AS supports Representational State Transfer (REST) APIs, allowing you to call APIs using HTTPS. For details about API calling, see :ref:`Calling APIs <as_04_0100>`.

Endpoints
---------

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. For the endpoints of the AS service, see `Regions and Endpoints <https://docs.sc.otc.t-systems.com/en-us/endpoint/index.html>`__.

Concepts
--------

-  Domain

   A domain has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions. The domain should not be used directly to perform routine management. For security purposes, create Identity and Access Management (IAM) users and grant them permissions for routine management.

-  User

   An IAM user is created by an account in IAM to use cloud services. Each IAM user has its own identity credentials (password and access keys).

   API authentication requires information such as the domain name, username, and password.

-  Region

   A region is a geographic area in which cloud resources are deployed. Availability zones (AZs) in the same region can communicate with each other over an intranet, while AZs in different regions are isolated from each other. Deploying cloud resources in different regions can better suit certain user requirements or comply with local laws or regulations.

-  AZ

   An AZ comprises of one or more physical data centers equipped with independent ventilation, fire, water, and electricity facilities. Computing, network, storage, and other resources in an AZ are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to allow you to build cross-AZ high-availability systems.

-  Project

   A project corresponds to a region. Default projects are defined to group and physically isolate resources (including computing, storage, and network resources) across regions. Users can be granted permissions in a default project to access all resources under their domains in the region associated with the project. If you need more refined access control, create subprojects under a default project and create resources in subprojects. Then you can assign users the permissions required to access only the resources in the specific subprojects.


   .. figure:: /_static/images/en-us_image_0000001924299688.png
      :alt: **Figure 1** Project isolation model

      **Figure 1** Project isolation model
