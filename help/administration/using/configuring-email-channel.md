---
title: Configuring email channel in Adobe Campaign Standard
description: Learn how to configure the email channel in Adobe Campaign Standard
audience: administration
feature: Instance Settings
role: Admin
level: Experienced
exl-id: 76d70fd1-dd93-4a6d-b18c-96ebe5a27a7d
---
# Configuring email channel{#configuring-email-channel}

As a Campaign [administrator](../../administration/using/users-management.md#functional-administrators), you can configure email channel settings. These advanced settings include general email channel parameters, email routing accounts, email processing rules and email properties. On this page, learn how to edit the default values for the general email and sending parameters.

## Email channel parameters {#email-channel-parameters}

The email configuration screen allows to define the parameters for the email channel. Administrators can access these configurations in the **[!UICONTROL Administration] > [!UICONTROL Channels] > [!UICONTROL Email] > [!UICONTROL Configuration]** menu.

![](assets/channels_1.png)

* **Authorized masks fields**

  The **[!UICONTROL Header parameters of sent emails]** section lists the authorized email addresses that you can use to send emails to your recipients (sender address) and to enable them to send back automated replies like asynchronous bounces, out-of-office replies, etc. (error address).  Adobe Campaign checks that the addresses entered are valid during the message preparation stage. This operating mode ensures that no addresses are used that could trigger deliverability issues.
    * Both sender and error addresses are set up by Adobe. Those fields cannot be empty.
    * You cannot edit those fields. To update an address, contact the Adobe Customer Care team.
    * To add another address, you can use [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html) to set up a new subdomain, or contact the Adobe Customer Care team. Note that if several masks are used, they are separated by commas.
    * It is a good practice to set addresses using a star such as *@yourdomain.com: it enables you to use any address ending with your subdomain name.

* **Deliverability**

  The **[!UICONTROL Delivery reports ID]** is provided by the Adobe Customer Care team. It identifies each instance with a deliverability ID which is used in the technical deliverability reports.
  <!--The Technical Deliverability report is not accessible through the UI in ACS. It will be replaced with 250ok in the future (project starting).-->

* **Delivery parameters**

  Adobe Campaign sends the messages beginning on the start date.
  
  When a message in a delivery is rejected due to a temporary error or a soft bounce, Campaign retries to send this message each day. Use the **[!UICONTROL Message delivery duration]** field to specify the timeframe during retries can happen. 

  >[!IMPORTANT]
  >
  >**This parameter in Campaign is now only used if set to 3.5 days or less.** If you define a value higher than 3.5 days, it will not be taken into account.

  The **[!UICONTROL Online resources validity duration]** field is used for uploaded resources, mainly for the mirror page and images. The resources on this page are valid for a limited time (to save disk space).

* **Retries**

  Temporarily undelivered messages are subject to an automatic retry. For more on this, see [Retries after a delivery temporary failure](../../sending/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

  >[!IMPORTANT]
  >
  >The maximum number of retries to be performed and the minimum delay between retries are now based on how well an IP is performing both historically and currently at a given domain. The **[!UICONTROL Retry period]** and **[!UICONTROL Number of retries]** settings in Campaign will be ignored.

  <!--This section indicates how many retries should be performed the day after the send is started (**Number of retries**) and the minimum delay between retries (**Retry period**). By default, five retries are scheduled for the first day with a minimum interval of one hour, spread out over the 24 hours of the day. One retry per day is programmed after that and until the delivery deadline, which is defined in the **[!UICONTROL Delivery parameters]** section.-->

* **Email quarantine parameters**

  In the **[!UICONTROL Time between two significant errors]** field, enter a value to define the time the application waits before incrementing the error counter in case of a soft-bounced failure. The default value is **"1d"**, for 1 day.

  When the **[!UICONTROL Maximum number of errors before quarantine]** value is reached, the email address is then quarantined. The default value is **"5"**: the address is quarantined on the fifth error. This means that the contact will be automatically excluded from subsequent deliveries.
  <!--Actually the way ACS works is that the address is already on the quarantine list on the first bounce, but with a different status meaning that the error count has started.-->

  For more on quarantines, see [Understanding quarantine management](../../sending/using/understanding-quarantine-management.md).

## Email routing accounts {#email-routing-accounts}

The **[!UICONTROL Integrated email routing]** external account is provided by default. It contains the technical parameters that allow the application to send emails.

![](assets/channels_2.png)

The account type must always be set to **[!UICONTROL Routing]**, the channel to **[!UICONTROL Email]** and the delivery mode set to **[!UICONTROL Bulk delivery]**.

**Related topic**:

[External accounts](../../administration/using/external-accounts.md)

## Email processing rules {#email-processing-rules}

The **[!UICONTROL Email processing rules]** can be accessed by administrators through the **[!UICONTROL Administration > Channels > Email]** menu.

>[!IMPORTANT]
>
>The email domains and the MX rules are now automatically managed<!--by the Adobe Campaign Enhanced MTA (Message Transfer Agent)--> and cannot be changed.

* **DKIM (DomainKeys Identified Mail)** email authentication signing is done for all messages with all domains. It does not sign with **Sender ID**, **DomainKeys**, or **S/MIME**.
* MX rules automatically customize your throughput by domain based on your own historical email reputation, and on the real-time feedback coming from the domains where you are sending emails.

<!--Note that the email domains and the MX rules are now managed by the Adobe Campaign Enhanced MTA:
* **DKIM (DomainKeys Identified Mail)** email authentication signing is done by the Enhanced MTA for all messages with all domains. It does not sign with **Sender ID**, **DomainKeys**, or **S/MIME** unless otherwise specified at the Enhanced MTA level.
* The Enhanced MTA uses its own MX rules that allow it to customize your throughput by domain based on your own historical email reputation, and on the real-time feedback coming from the domains where you are sending emails.-->

### Bounce mails {#bounce-mails}

Asynchronous bounces are still qualified by the Campaign inMail process through the **[!UICONTROL Bounce mails]** rules.

These rules contain the list of character strings which can be returned by remote servers and which let you qualify the error (**Hard**, **Soft** or **Ignored**).

>[!IMPORTANT]
>
>Synchronous delivery failure error messages are now qualified by the Adobe Campaign Enhanced MTA, which determines the bounce type and qualification, and sends back that information to Campaign.

For more on bounce mail qualification, see this [section](../../sending/using/understanding-delivery-failures.md#bounce-mail-qualification).

<!--Because they are now managed by the Enhanced MTA, the bounce qualifications in the Campaign **[!UICONTROL Message qualification]** table are no longer used. For more on bounce mail qualification, see this [section](../../sending/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Management of email domains {#managing-email-domains}

The email domains are now managed by the Adobe Campaign Enhanced MTA. The Adobe Campaign **[!UICONTROL Domain management]** rules are no longer used.

**DKIM (DomainKeys Identified Mail)** email authentication signing is done by the Enhanced MTA for all messages with all domains. It does not sign with **Sender ID**, **DomainKeys**, or **S/MIME** unless otherwise specified at the Enhanced MTA level.

### MX management {#mx-management}

The MX rules are now managed by the Adobe Campaign Enhanced MTA. The Adobe Campaign **[!UICONTROL MX management]** delivery throughput rules are no longer used.

The Enhanced MTA uses its own MX rules that allow it to customize your throughput by domain based on your own historical email reputation, and on the real-time feedback coming from the domains where you are sending emails.-->

## List of email properties {#list-of-email-properties}

This section details the list of parameters available in the properties screen of an email or email template.

>[!NOTE]
>
>Some parameters are only available in templates. Parameters you can access [depend on your permissions](../../administration/using/users-management.md).

To edit the properties of an email or an email template, use the **[!UICONTROL Edit properties]** button.

![](assets/delivery_options_1.png)

### General parameters {#general-parameters}

On the top of the email parameter screen, identify the email using the **[!UICONTROL Label]** and **[!UICONTROL ID]** fields. This information appears in the interface but is not visible to the message recipients.

![](assets/delivery_options_2.png)

>[!IMPORTANT]
>
>The ID must be unique.

Use the **[!UICONTROL Brand]** field to select the brand linked to the delivery. For more information on using and configuring brands, refer to the [Branding](../../administration/using/branding.md) section.

In the **[!UICONTROL Campaign]** field, enter the campaign associated to the email.

You can also add a **[!UICONTROL Description]** in the corresponding field and edit the image displayed on the email thumbnail in the lists.

### Sending parameters {#sending-parameters}

The **[!UICONTROL Send]** section is only available for email templates. It contains the following parameters:

#### Retries parameters {#retries-parameters}

Temporarily undelivered messages are subject to an automatic retry. For more on this, see [Retries after a delivery temporary failure](../../sending/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

>[!IMPORTANT]
>
>The minimum delay between retries and the maximum number of retries to be performed are now based on how well an IP is performing both historically and currently at a given domain. The **[!UICONTROL Retry period]** and **[!UICONTROL Max. number of retries]** settings in Campaign will be ignored.

The **delivery duration setting** (defined in the [Validity period parameters](#validity-period-parameters) section) **set up in Campaign will still be honored but only up to 3.5 days**. At that point, any message in the retry queue will be removed from the queue and sent back as a bounce. For more on delivery failures, see this [section](../../sending/using/understanding-delivery-failures.md#about-delivery-failures).

#### Email format parameters {#email-format-parameters}

You can configure the format of emails to be sent. There are three options available:

* **Use recipient preferences** (default mode): the message format is defined according to the data stored in the recipient profile and stored by default in the **Email format** field (@emailFormat). If a recipient wishes to receive messages in a certain format, this is the format sent. If the field is not completed, a multipart-alternative message is sent (see below).
* **Let recipient mail client choose the most appropriate format (multipart-alternative)**: the message contains both formats: text and HTML. The format displayed upon reception depends on the configuration of the recipient's mail software (multipart-alternative).

  >[!IMPORTANT]
  >
  >This option includes both versions of the message. It therefore impacts the delivery throughput, because the message size is greater.

* **Send all messages in text format**: the message is sent in text format. HTML format will not be sent, but used for the mirror page only when the recipient clicks the link in the message.

#### SMTP test mode {#smtp-test-mode}

Use the **[!UICONTROL Enable SMTP test mode]** option to test sending emails via an SMTP connection without actually sending messages. The delivery is processed up to connection to the SMTP server but is not sent: for every recipient of the delivery, Campaign connects to the SMTP provider server, executes the SMTP RCPT TO command, and closes the connection before the SMTP DATA command.

![](assets/smtp-test-mode.png)

This option is available for emails and email templates.

If you enable the SMTP test mode option for an email template, all email messages created from this template will have this option enabled.

  >[!IMPORTANT]
  >
  >When this option is enabled for an email, no messages will be sent until it is unchecked.
  >A warning will be displayed in the email or email template dashboard.

For more information on configuring SMTP, refer to the [List of email SMTP parameters](#list-of-email-smtp-parameters) section.

### Validity period parameters {#validity-period-parameters}

The **[!UICONTROL Validity period]** section contains the following parameters:

![](assets/delivery-validity-period.png)

* **[!UICONTROL Explicitly set validity dates]**: when this box is unchecked, you must enter a duration in the **[!UICONTROL Delivery duration]** and **[!UICONTROL Resource validity limit]** fields.

  Check this box if you would like to define specific times and dates.

  ![](assets/delivery-set-explicit-dates.png)

* **[!UICONTROL Delivery duration]** / **[!UICONTROL Validity limit for sending messages]**: Adobe Campaign sends the messages beginning on the start date. Use this field to specify the period during which the messages can be sent.

  >[!IMPORTANT]
  >
  >**You must define a value up to 3.5 days.** If you set a value higher than 3.5 days, it will not be taken into account.
  >
  >The **[!UICONTROL Delivery duration]** parameter does not apply to transactional messages. For more on transactional messaging, see [this section](../../channels/using/getting-started-with-transactional-msg.md).

* **[!UICONTROL Resource validity duration]** / **[!UICONTROL Validity limit date for resources]**: this field is used for uploaded resources, mainly for the mirror page and images. The resources on this page are valid for a limited time (to save disk space).
* **[!UICONTROL Mirror page management]**: the mirror page is an HTML page accessible online via a web browser. Its content is identical to the email content. By default, the mirror page is generated if the link is inserted in the mail content. Use this field to modify how this page is generated:

    * **[!UICONTROL Generate the mirror page if a mirror link appears in the email content]** (default mode): the mirror page is generated if the link is inserted in the mail content. 
    * **Force the generation of the mirror page**: even if no link to the mirror page is inserted into the messages, the mirror page will be created. 
    * **Do not generate the mirror page**: no mirror page is generated, even if the link is in the messages. 
    * **Generate a mirror page accessible using only the message ID**: this option lets you access the content of the mirror page, with personalization information, in the delivery log window.
    
  >[!IMPORTANT]
  >
  >The mirror page is generated only if an HTML content has been defined for the email.
  >


### Tracking parameters {#tracking-parameters}

The **[!UICONTROL Tracking]** section contains the following parameters:

* **[!UICONTROL Activate tracking]**: use this option to activate/deactivate message URL tracking. To manage tracking for each message URL, use the **[!UICONTROL Links]** icon in the Email Designer action bar. See [About tracked URLs](../../designing/using/links.md#about-tracked-urls).
* **[!UICONTROL Tracking validity limit]**: use this option to define the duration for which the tracking will be activated on the URLs.
* **[!UICONTROL Substitution URL for expired URLs]**: use this option to enter a URL to a fall-back web page: it is displayed once the tracking has expired.
* **[!UICONTROL Use tracking pixel at the top of email]**: use this option to move the tracking pixel at the top of the email instead of at the bottom. By default, this pixel is located at the bottom of your emails. If you send large messages, consider moving this pixel at the top of your emails instead of the bottom to improve open tracking - otherwise the tracking pixel could be cut by some email providers.

### Advanced parameters {#advanced-parameters}

The **[!UICONTROL Advanced parameters]** section contains multiple parameters.

The first fields allow you to enter information necessary to elaborate email message headers. You can manage here the reply address and text as well as the sender address (which fills the field "From:"). This information can be personalized.

Click the button to the right of the field that is going to be changed, then add the personalization field, content block or dynamic text.

![](assets/advancedparameters.png)

Inserting and using the personalization content is detailed in the [Personalizing email content](../../designing/using/personalization.md) documentation.

#### Target context {#target-context}

Use the targeting context to define a set of tables that will be used for email targeting (in the audience definition screen) and personalization (defining personalization fields in the HTML content editor).

#### Routing {#routing}

This field indicates the routing mode used. It references an external account. For example, this can be used if you would like to use an external account containing specific branding configurations.

>[!NOTE]
>
>External accounts are accessible via the **Administration** > **Application settings** > **External accounts** menu.

#### Preparation {#preparation}

Preparing messages is detailed in the [Approving messages](../../sending/using/preparing-the-send.md) section.

* **[!UICONTROL Typology]**: before any send, messages must be prepared in order to validate the content and configuration. The verification rules applied during the preparation phase are defined in a **typology**. For example, for emails, preparation involves checking the subject, URLs and images, etc. Select the typology to apply in this field.

  >[!NOTE]
  >
  >Typologies, which can be accessed via the **[!UICONTROL Administration]** > **[!UICONTROL Channels]** > **[!UICONTROL Typologies]** menu, are presented in [this section](../../sending/using/about-typology-rules.md).

* **[!UICONTROL Compute the label during delivery preparation]**: use this option to calculate the label value of the email during the message preparation phase using personalization fields, content blocks, and dynamic text.

  It is also possible to personalize the delivery label with events variables that have been declared into the workflow's external signal activity. For more on this, refer to [this section](../../automating/using/calling-a-workflow-with-external-parameters.md).

* **[!UICONTROL Save SQL queries in the log]**: use this option to add SQL query logs in the journal during the preparation phase.

#### Proof settings {#proof-settings}

In this section, you can configure the default prefix to use in the subject line of the proof messages. Learn more about proofs in [this section](../../sending/using/sending-proofs.md).

### List of email SMTP parameters {#list-of-email-smtp-parameters}

The **[!UICONTROL SMTP]** section contains the following parameters:

* **[!UICONTROL Character encoding]**: check the **[!UICONTROL Force encoding]** box if you would like to force message encoding, then select the encoding you want to use.
* **[!UICONTROL Bounce mails]**: by default, bounce mails are received in the platform's error inbox (defined in the **[!UICONTROL Administration]** > **[!UICONTROL Channels]** > **[!UICONTROL Email]** > **[!UICONTROL Configuration]** screen). To define a specific error address for an email, enter the address in the **[!UICONTROL Error address]** field.
* **[!UICONTROL Additional SMTP headers]**: this option allows for additional SMTP headers to be added to your messages. The script entered in the **[!UICONTROL Headers]** field must reference one header per line, in the form of **name:value**. Values are encoded automatically if necessary.

  >[!IMPORTANT]
  >
  >Adding a script for inserting additional SMTP headers is reserved for advanced users. The syntax of this script must comply with the requirements of this content type: no unused space, no empty line, etc.

### List of access authorization parameters {#list-of-access-authorization-parameters}

The **[!UICONTROL Access authorization]** section contains the following parameters:

* The **[!UICONTROL Organizational unit]** field is used to restrict access to this email to certain users. The users associated with the specified unit or parent units will have read and write access to this email. Users associated with child units will only have read access to this email.

  >[!NOTE]
  >
  >You can configure organizational units via the **Administration** > **Users & Security** menu.

* The **[!UICONTROL Created by]**, **[!UICONTROL Created]**, **[!UICONTROL Modified by]** and **[!UICONTROL Last modified]** fields are automatically completed.

## Legacy settings {#legacy-settings}

If you are **NOT** running the latest version of Campaign, the parameters and UI sections described below still apply to you.

### Retries {#legacy-retries}

The **[!UICONTROL Retries]** settings in the [Configuration menu](#email-channel-parameters) and in the [Sending parameters](#retries-parameters) of the email properties indicate how many retries should be performed the day after the send is started (**[!UICONTROL Number of retries]** / **[!UICONTROL Max. number of retries]**) and the minimum delay between retries (**[!UICONTROL Retry period]**).

The number of retries can be changed globally (contact your Adobe technical administrator) or for each delivery or delivery template.

By default, five retries are scheduled for the first day with a minimum interval of one hour, spread out over the 24 hours of the day. One retry per day is programmed after that and until the delivery deadline, which is defined globally in the **[!UICONTROL Delivery parameters]** section of the **[!UICONTROL Configuration]** menu, or in the **[!UICONTROL Validity period]** section at the delivery level (see the [Delivery duration](#legacy-delivery-duration) section below).

### Delivery duration {#legacy-delivery-duration}

Use the **[!UICONTROL Message delivery duration]** parameter in the [Configuration menu](#email-channel-parameters) to specify the time frame in which any message in the delivery that encounters a temporary error or soft bounce will be retried.

Use the **[!UICONTROL Delivery duration]** or **[!UICONTROL Validity limit for sending messages]** parameter in the [Validity period parameters](#validity-period-parameters) section to specify the duration during which the messages can be sent.

### Email processing rules {#legacy-email-processing-rules}

The **[!UICONTROL MX management]**, **[!UICONTROL Bounce mails]** and **[!UICONTROL Domain management]** rules can be accessed and modified by administrators through the **[!UICONTROL Administration > Channels > Email > Email processing rules]** menu. [Learn more](#email-processing-rules).

### Bounce mail qualification {#legacy-bounce-mail-qualification}

To list the various bounces, and their associated error types and reasons, click the **Adobe** logo, in the top-left, then select **[!UICONTROL Administration > Channels > Quarantines > Message qualification]**.

Bounces can have the following qualification statuses:

* **[!UICONTROL To qualify]**: the bounce mail needs to be qualified. Qualification must be done by the Deliverability team to ensure that the platform deliverability functions correctly. As long as it is not qualified, the bounce mail is not used to enrich the list of email processing rules.
* **[!UICONTROL Keep]**: the bounce mail was qualified and will be used by the **Update for deliverability** workflow to be compared to existing email processing rules and enrich the list.
* **[!UICONTROL Ignore]**: the bounce mail was qualified but will not be used by the **Update for deliverability** workflow. So it will not be sent to the client instances.

>[!NOTE]
>
>In case of an outage of an ISP, emails sent through Campaign will be wrongly marked as bounces. To correct this, you need to update bounce qualification. [Learn more](../../administration/using/update-bounce-qualification.md).

<!--Bounces are qualified through the **[!UICONTROL Bounce mails]** processing rule. For more on accessing this rule, refer to this [section](#legacy-bounce-mail-qualification).-->

### Delivered indicator reporting {#legacy-delivered-status-report}

In the **[!UICONTROL Summary]** view of each message, the **[!UICONTROL Delivered]** percentage progressively goes up throughout the validity period of the delivery, as the soft and hard bounces get reported back.

Soft-bouncing messages show as **[!UICONTROL Failed]** on the first day after the delivery. These messages are retried each day, until the validity period of the delivery ends.
