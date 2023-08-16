:original_name: as_01_0106.html

.. _as_01_0106:

Modifying an AS Group
=====================

Scenarios
---------

You can modify an AS group if needed. The values of the following parameters can be changed: **Name**, **Max. Instances**, **Min. Instances**, **Expected Instances**, **Health Check Method**, **Health Check Interval**, **Instance Removal Policy**.

.. note::

   Changing the value of **Expected Instances** will trigger a scaling action. AS will automatically increase or decrease the number of instances to the value of **Expected Instances**.

If the AS group is not enabled, contains no instances, and has no scaling action ongoing, you can modify **Subnet** and **Load Balancing** configurations.

Procedure
---------

#. Log in to the management console.
#. Under **Computing**, click **Auto Scaling**. Then, on the **Auto Scaling** page, click the **AS Groups** tab.

3. In the AS group list, locate the AS group you want to modify and choose **More** > **Modify** in the **Operation** column.

   You can also click the AS group name to switch to the **Overview** page, and click **Modify** in the upper right corner.

4. In the **Modify AS Group** dialog box, modify related data, for example, the expected number of instances.

5. Click **OK**.
