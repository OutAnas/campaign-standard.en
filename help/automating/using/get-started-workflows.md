---
title: Get started with processes and data management
description: Automate processes with workflows, manage data and audiences, send messages, and more.
audience: automating
content-type: reference
topic-tags: about-workflows-and-data-management

feature: Workflows
role: Data Architect
level: Beginner
exl-id: 26be942a-c252-458f-a590-eb235567ca67
---
# Get started with processes and data management {#get-started-processes-data-management}

<table>
<tr>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#workflow-activities">Workflow activities</a></p></td><td><img src="assets/do-not-localize/icon_activities.svg" width="60px"><p><a href="../../automating/using/workflow-created-query-with-complement.md">Use cases</a></p></td><td><img src="assets/do-not-localize/icon_filter.svg" width="60px"><p><a href="#filter-data">Filter data</a></p></td>
<td><img src="assets/do-not-localize/icon_manage.svg" width="60px"><p><a href="#import-export-data">Import/export data</a></p></td></tr>
</table>

Adobe Campaign offers a comprehensive graphical environment that allows you to design complex processes including segmentation, campaign execution, file processing, etc. For example, you can use a workflow to download a file from a server, decompress it, and then import its records into the Adobe Campaign database.

A workflow can also involve users by assigning them tasks or having them approve performed tasks. This means you can assign a task to one or several users to work on content or specify targets, and approve proofs before sending the message.

Workflows can be used in different contexts, as for example:

* Targeting to manage audiences or send messages.
* Data management (ETL) to manipulate data.
* Importing data into Campaign database.
* Technical processes such as database cleanup, recovering tracking information, etc.

>[!IMPORTANT]
>
> Adobe recommends customers not to run more than 20 active workflows executions simultaneously, and to prioritize and spread out your workflow execution over time. For more on this, refer to the best practices provided in [this page](../../automating/using/best-practices-workflows.md).

## Workflow activities {#workflow-activities}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

Various activities are available to help you design your workflows.

[Targeting activities](../../automating/using/about-targeting-activities.md) allow you to build one or more targets by defining sets and splitting or combining these sets using intersection, union, or exclusion operations.

With [Execution activities](../../automating/using/about-execution-activities.md), coordinate your workflow and its activities, while [Channel activities](../../automating/using/about-channel-activities.md) let you combine Campaign Standard communication channels to create cross-channel workflows.

Finally, [Data management activities](../../automating/using/about-data-management-activities.md) allow you to manipulate data from your database.

Read more:

* [Building a workflow](../../automating/using/building-a-workflow.md)
* [Executing a workflow](../../automating/using/about-workflow-execution.md)
* [Workflow best practices](../../automating/using/best-practices-workflows.md)

## Filter data {#filter-data}

<img src="assets/do-not-localize/icon_filter.svg" width="60px">

Leverage the **query editor** to filter data from your database and build a population to better target your recipients. The query editor is available to perform several actions in Campaign Standard: create Query type audiences, define delivery targets, or populations in workflow activities.

The query editor comes with **predefined filters and rules** for quick and easy filtering. However, you can also use **advanced expression editing** capabilities. This allows you to manually enter conditions and use functions, in order to form your own rules.

Read more:

* [Editing queries](../../automating/using/editing-queries.md)
* [Advanced expression editing](../../automating/using/advanced-expression-editing.md)
* [List of functions](../../automating/using/list-of-functions.md)

## Import/export data {#import-export-data}

<img src="assets/do-not-localize/icon_manage.svg" width="60px">

Campaign Standard comes with several **data management capabilities** to import and export data.

[Workflows data management activities](../../automating/using/about-data-management-activities.md) allow you to import data, perform mass updates on fields, receive or send file, or link unidentified data to existing resources.

With [Import templates](../../automating/using/importing-data-with-import-templates.md), manage certain types of import defined by administrators through simplified import functions.

[Exporting logs](../../automating/using/exporting-logs.md) let you export log data through a simple workflow, allowing you to analyse the resultats of your marketing campaigns in your own reporting or BI tools.

Leverage [Packages](../../automating/using/managing-packages.md) to exchange resources between different campaign instances, for example, to replicate the configuration of an instance, or to transfer data from a server to another including custom resources.

Finally, [Exporting lists](../../automating/using/exporting-lists.md) allow you to export any list from Campaign Standard like, for example, the list of test profiles, the list of quarantines email addresses, etc.

Read more:

* [Importing and exporting data](../../automating/using/about-data-import-and-export.md)
* [Use case: Exporting / importing custom resources](../../automating/using/exporting-importing-custom-resources.md)

## Additional resources

* [Processes and data management tutorial videos](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/managing-processes-and-data/creating-a-workflow.html)
* [Technical workflows](../../administration/using/technical-workflows.md)
* [Get started with Campaign Standard data model](../../developing/using/get-started-data-model.md)
