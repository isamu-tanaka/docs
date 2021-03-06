---
title: "Sending Email"
space: "General How-To's"
category: "Mendix Cloud"
---

You may want to send email in the Mendix Cloud via, for instance, the [Email Module](https://appstore.home.mendix.com/link/app/259/Mendix/E-mail-module-with-templates). After you have installed this you will need to configure an SMTP server in your application. There are several options:

|   | Enterprise/Professional Plans | Free Plan (sandbox) |
| --- | --- | --- |
| **Amazon Simple Email Service** | &#x2713; | &#x2713; |
| **Gmail** | &#x2713; | &#x2713; |
| **MailGun** | &#x2713; | &#x2713; |
| **SendGrid** | &#x2713; | &#x2713; |
| **Other SMTP compatible services** | &#x2713; | &#x2713; |
| **Mendix Mail Servers** | &#x2713; | &#x2717; |

In our paid plans we include a local mail server for convenience and backwards compatibility. For new applications, or applications that send large amounts of e-mail we recommend using an external e-mail service.

## 1. External Email Providers

In general we recommend external services as these offer specialized tools for sending e-mail, working with spam filters, keeping track of sent e-mail and giving insights into your target reach via analytics tools. The [Email Module](https://appstore.home.mendix.com/link/app/259/Mendix/E-mail-module-with-templates) from the AppStore is compatible with all providers that offer an SMTP interface. If you want to use other ways of sending e-mail using an external service, such as REST APIs, you can use the [REST Services Module](https://appstore.home.mendix.com/link/app/997/Mendix/Rest-Services) from the AppStore or create your own Java actions for sending e-mail.

In order to use an external provider you will need to sign up for an account with them and use their SMTP settings which include:

*   Host
*   Port
*   SSL/TLS
*   Username
*   Password

Frequently used providers (A-Z) are:

*   [Amazon Simple Email Service](https://aws.amazon.com/ses/) [[settings](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/smtp-connect.html)]
*   [Gmail](https://mail.google.com/) [[settings](https://support.google.com/a/answer/176600?hl=en) - [common configuration problem](http://stackoverflow.com/questions/20337040/gmail-smtp-debug-error-please-log-in-via-your-web-browser)]
*   [MailGun](https://mailgun.com/) [[settings](https://documentation.mailgun.com/quickstart-sending.html#send-via-smtp)]
*   [Mandrill](https://www.mandrill.com/) [[settings](http://help.mandrill.com/categories/20090941-SMTP-Integration)]
*   [SendGrid](https://sendgrid.com/) [[settings](https://support.sendgrid.com/hc/en-us/articles/200328026-Recommended-SMTP-settings)]

Many users of our free tier use the settings of their own GMail account for convenience. There are many more email providers, most of which have SMTP compatibility.

## 2\. Mendix Mail Servers

The Mendix mail servers are only available in our paid plans. If you are using more than 1000 messages per day we recommend you use an external mail service as described above. The settings for the Mendix mail servers are as follows:

**Servername:** localhost
**Port:** 25

No authentication information is needed. You can use this same SMTP server from the [Email Module](https://appstore.home.mendix.com/link/app/259/Mendix/E-mail-module-with-templates) from the AppStore or custom Java actions.

### 2.1 Using Sender Policy Framework (SPF) while sending outgoing mail from Mendix

When using Mendix mail servers and a sender address in a domain that has a restrictive SPF policy configured, you may encounter email delivery issues when the outgoing email servers from Mendix are not listed in the SPF record of that domain name.

*   The needed information about Mendix mail servers that deliver outgoing mail traffic to the internet can be included in the SPF settings for the domain of the sender address by including "include:<a rel="nofollow">_spf.mendix.com</a>" into the policy rule. By using this technique, your SPF configuration will always automatically be kept up to date.
*   Do **not** directly use hard coded low level infrastructure details like IP addresses of mail servers. These addresses are subject to change whenever Mendix is doing upgrades and maintenance.

## 3\. General Email Guidelines

### 3.1 Sender and recipient address requirements

*   Always use a sender address which is an existing address on which you are able to receive mail. If using a non-existing address as sender address, you will not get (bounce) error messages which might be generated when mail delivery fails half way.
*   Do not invent your own non-existing domain or local part, do not use noreply@ addresses if that noreply@ address is not a real email box from which you can read and process delivery errors.
*   Sender or recipient addresses which contain a domain name that does not exist on the internet may be rejected by the outgoing mail server.
*   Sender or recipient addresses which do not contain a domain name at all will be rejected by the outgoing mail server.
*   Do not invent your own email addresses for testing purposes. Domain names like 'domain.com', 'email.com', 'test.com' are actually real domain names. Likely there's someone reading the mailbox for 'test@domain.com', who will receive email you send from your test environment if you send it there.

## 4\. Related content

*   [Trends](trends)
*   [Deploying to the cloud](deploying-to-the-cloud)
*   [How to deploy a Mendix app on Azure](how-to-deploy-a-mendix-app-on-azure)
*   [Sending Email](sending-email)
*   [Different user logins when integrated with Mendix SSO](different-user-logins-when-integrated-with-mendix-sso)
*   [Integrate your app with Mendix SSO](integrate-your-app-with-mendix-sso)
*   [Deploying to a Free App](deploying-to-a-free-app)
