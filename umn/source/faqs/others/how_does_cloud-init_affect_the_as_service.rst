:original_name: as_faq_0013.html

.. _as_faq_0013:

How Does Cloud-Init Affect the AS Service?
==========================================

Cloud-Init is an open-source cloud initialization program, which initializes specified custom configurations, such as the hostname, key pair, and user data, of a newly created ECS. When creating an AS configuration, you can choose an image with Cloud-Init or Cloudbase-Init preinstalled for ECS initialization.

If Cloud-Init or Cloudbase-Init is not installed in the private image specified in the AS configuration of an AS group, the following issues can occur on the ECSs created in a scaling action:

-  On a Windows image, the system will display a message indicating that the password for logging in to the ECS could not be viewed. In such a case, you can log in to the ECS using the image password. If you forgot the image password, use the password resetting function available on the **Elastic Cloud Server** page to reset the password.

-  On a Linux image, the ECS cannot be logged in using the password or key pair configured during ECS creation. In such a case, you can log in to the ECS only using the image password or key pair. If you forgot the image password or key, use the password resetting function available on the **Elastic Cloud Server** page to reset the password.

-  On a private image, user data injection fails.

   To avoid these issues, confirm that the private image specified in the AS configuration has Cloud-Init or Cloudbase-Init installed. If the program was not installed, use a private image with the program installed to create an AS configuration, and replace the AS configuration of the AS group with the newly created one. The procedure is as follows:

   #. Log in to the management console.
   #. Under **Computing**, click **Auto Scaling**.
   #. Click the **AS Configurations** tab.
   #. Click **Create AS Configuration** and select a private image with Cloud-Init or Cloudbase-Init installed to create a desired AS configuration.
   #. Change the AS configuration of the AS group to the newly created one.
