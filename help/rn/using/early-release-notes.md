---
title: Early Release Notes
description: Early Release Notes
feature: Overview
role: User
level: Beginner
hide: yes
hidefromtoc: yes
exl-id: 4b10eb63-3fea-438e-a1a7-25fbf7b0e5b0
---
# Early release notes {#new-release}

This page describes new features, improvements and fixes included in the next Campaign Standard release.

>[!CAUTION]
>
> This content is subject to changes without prior notice until the stage environments upgrade date. Learn more in the [release planning page](../../rn/using/release-planning.md).
>

## Release 22.1 - February 2022 {#feb-2022}


**What's new?**


<table> 
<thead> 
<tr> 
<th> <strong>Security update for Apache Log4j Security Vulnerabilities</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>
<p>Following the update to Apache log4j v2.17.0 release in December 2021, to ensure our customers are not impacted by possible unintended effects of introducing further change to the system outside of our normal release schedule, we have made the update internally and are getting it ready for deployment with this release.</p>
</td> 
</tr> 
</tbody> 
</table>

**Security fixes**

* New URL signature mechanism for tracking included in this release. The previous mechanism had been disabled to prevent an issue that was causing some valid, signed tracking links to be incorrectly blocked after being modified by third-party security tools. (CAMP-48983)
* Reinforce security to access application and server configuration files: JavaScript file access APIs security are now restricted to sandbox directories. (CAMP-49411)

**Improvements**

* Improved processing of reporting data to avoid over loading the system. (CAMP-47578)
* After sending your In-App messages, you can now choose to deactivate your delivery. This allows you to delete your delivery without losing any reporting data. (CAMP-48469)
* To prevent any issue, users can no longer use the same name for a custom table column as the one used for the automatic Primary Key in the database, `"<dataType><resourceName>Id"`. (CAMP-49358)

**Patches**

* Fixed an issue with the **Send report now** option in Dynamic reports: the PDF generation jobs failed with deliveries including multi-variants. (CAMP-49120)
* Fixed an issue that prevented users to refresh or unlink Adobe Experience Manager (AEM) content from their Adobe Campaign Standard deliveries when a duplicated content in AEM shared the same key (cq:uuid). (CAMP-49161)
* Fixed an error when accessing an instance where pages were not loading, deliveries could not be opened or any pending modifications could not be saved. (CAMP-50195)
* Fixed an issue that prevented Delivery alerting criteria to be opened if the field **Delivery filter** applied by this criterion was not filled. (CAMP-49093)
* Fixed an issue when editing the **Secondary** button in In-App deliveries that prevented changes to be taken into account. (CAMP-50250)
* Fixed an error in Japanese instances that prevented users to choose Several times a day as **Execution frequency** in the **Scheduler** activity. (CAMP-50247)
* Fixed an issue when working in a Japanese user interface which displayed an error message when selecting a time in a Scheduler activity. (CAMP-49289)
* Fixed an error with push notification reports that displayed dismissed push notifications as **Open** instead of **Impression**. (CAMP-45980)
* Fixed an issue which could lead to errors when opening a report. (CAMP-49222)
* Fixed an issue which could lead to the email preparation failing after deleting a link to AEM content. (CAMP-49877)
* To solve various issues, the retry mechanism has been improved for deliveries including content imported from a URL. (CAMP-48888)
* Fixed an issue which occurred after creating a new filter in a custom resource, then using it as a reconciliation key in a landing page. If the custom resource was published again, the filter was removed from the list of available reconciliation keys for the landing page. (CAMP-49516)
* Fixed an issue in landing pages when using dynamic conditions with checkboxes. (CAMP-48604)
* Fixed an issue that occurred in a **Query** activity when using the “On or before October” filter condition. When working from an instance set to a European timezone, the selected month for the filter showed September instead of October, due to an issue when converting the timezone. (CAMP-48602)
* To optimize deliverability, emails are now sent using 7-bit encoding instead of 8-bit. This prevents relays from invalidating the DKIM signature when converting from 8 to 7-bits. (CAMP-49016)
* Performances when duplicating audiences have been enhanced in order to avoid any issue when working with large audiences. (CAMP-49639)
* Fixed an issue which could prevent a custom filter from displaying the correct results when used into a **Query** activity. (CAMP-49417)
* Fixed an error that displayed an error message when trying to use a fragment in a delivery with a comma in its name. The issue has been resolved, commas can now be used in fragments’ names. (CAMP-49216)