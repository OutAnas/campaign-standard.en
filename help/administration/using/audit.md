---
title: Audit Trail
description: Monitor actions and events with Campaign Audit Trail
audience: administration
feature: Access Management
role: Admin
level: Experienced
exl-id: bda6f8d5-3bcf-498c-a7c4-d3c2c79b9510
---
# Audit trail {#audit}

The **[!UICONTROL Audit trail]** gives you access to the complete history of changes made within your instance.

**[!UICONTROL Audit trail]** captures, in real-time, a comprehensive list of actions and events occurring within your Adobe Campaign Standard instance. It includes a self-serve way to access a history of data to help answer questions such as: what happened to your workflows, custom resources and options, who last updated them or what did your users do in the instance.

![](assets/audit-trail.png)

**[!UICONTROL Audit trail]** consists of three components:

* **Custom Resources Audit trail**: check the activity and last modification done to custom resources.

    For more information on **[!UICONTROL Custom resources]**, refer to this [page](../../developing/using/key-steps-to-add-a-resource.md).

* **Workflow Audit trail**: check the activity and last modification done to workflows, and additionally, the state of your workflows such as:

  * Created
  * Modified
  * Deleted
  * Workflow Start
  * Workflow Pause
  * Workflow Stop
  * Workflow Restart
  * Workflow Cleanup
  * Workflow Simulate
  * Workflow Wakeup
  * Workflow Immediate Stop
  * Workflow Restart with same user
  * Workflow Restart Unknown command

  For more information on **[!UICONTROL Workflows]**, refer to this [page](../../automating/using/get-started-workflows.md).

* **Option Audit trail**: check the activity and last modification done to options.

    For more information on **[!UICONTROL Options]**, refer to this [page](../../administration/using/about-campaign-standard-settings.md).

Note that, by default, retention period is 30 days.

## Accessing Audit trail {#audit-access}

To access your instance's Audit trail:

1. In Adobe Campaign Standard, from the advanced menu, select **[!UICONTROL Administration]** > **[!UICONTROL Audit trail]**.

    ![](assets/audit-trail.png)

1. The **[!UICONTROL Audit trail]** window opens with the list of your entities. Adobe Campaign Standard will audit the create, edit and delete actions for workflows, options and custom resources.

    From the **[!UICONTROL Search]** menu, you can filter your entity on:
    
    * **[!UICONTROL Start date]**
    * **[!UICONTROL End date]**
    * **[!UICONTROL Type]**: Entity's type between All, Workflow, Custom Resource and Option.
    * **[!UICONTROL Entity name]**: ID of your workflow, option or custom resource

    ![](assets/audit-trail_2.png)

1. Select one of the entities to learn more about the last modifications.

1. The Audit entity window gives you more detailed information on the chosen entity such as:

    * **[!UICONTROL Entity]**: ID of your workflow, option or custom resource.
    * **[!UICONTROL Action]**: Last action performed on this entity.
    * **[!UICONTROL Changed by]**: Username of the last person who last modified this entity.
    * **[!UICONTROL Changed date]**: Date of the last action performed on this entity.
    * **[!UICONTROL Content]**: Code block which gives you more information on what was changed exactly in your entity.

    In this example, we can see that the workflow WKF110 has been started on August 26th by the Business administrator of this instance.

    ![](assets/audit-trail_3.png)

## Enable/disable Audit trail {#enable-disable-audit}

>[!NOTE]
>
> Only Functional administrators can enable or disable Audit trail. For more on this, refer to this [page](../../administration/using/users-management.md#functional-administrators).

Audit trail can be easily activated or deactivated for a specific activity.

To do so:

1. In Adobe Campaign Standard, from the advanced menu, select **[!UICONTROL Administration]** > **[!UICONTROL Application settings]** > **[!UICONTROL Options]**.

    ![](assets/audit-trail_4.png)

1. Select one of the following options depending on the entity you want to disable:

    * **[!UICONTROL XtkAudit_Workflows]** option to manage the Audit trail for Workflows.
    * **[!UICONTROL XtkAudit_Option]** option to manage the Audit trail for Options.
    * **[!UICONTROL XtkAudit_CusResource]** option to manage the Audit trail for Custom resources.
    * **[!UICONTROL XtkAudit_Enable_All]** option to manage the Audit trail for every entity.

        >[!NOTE]
        >
        >If the **[!UICONTROL XtkAudit_Enable_All]** option is set to 0, the **[!UICONTROL Audit trail]** feature will be completely disabled, regardless of other individual option values.
    
    ![](assets/audit-trail_5.png)

1. From your **[!UICONTROL Options]** page, set the **[!UICONTROL Value (integer)]** to 0 if you want to disable the **[!UICONTROL Audit trail]** or to 1 to enable it.

    ![](assets/audit-trail_6.png)

1. Click **[!UICONTROL Save]**.
