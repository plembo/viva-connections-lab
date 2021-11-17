# Microsoft Learn: Extend Viva Connections desktop with web parts
https://docs.microsoft.com/en-us/learn/modules/viva-connections-extend-with-web-parts/3-extend-viva-connections-desktop-with-web-parts

## Prerequisites
* Windows 10 desktop
* SharePoint admin access to Microsoft 365 tenant.
* [Viva Connections enabled](https://docs.microsoft.com/en-us/learn/modules/viva-connections-get-started) on Microsoft 365 tenant.
* Code editor.
* Node.js v14.

After enabling Viva Connections as instructed in the tutorial the root and homesite for the SharePoint tenant will be the same Communications site.

## Install development tools for extending Viva Connections
Node modules:

* gulp (```npm install -g gulp-cli```)
* yeoman (```npm install -g yo```)
* SharePoint Framework generator (```npm install -g @microsoft/generator-sharepont```)

Create a SharePoint list named "Announcements" with sample data.

## Build a SharePoint Framework web part
Important: web parts only work with Viva Connections desktop, they won't work with the mobile Viva Connections app.

Web part will get data from a SharePoint list.

Note: On Linux, running ```gulp trust-dev-cert``` will create a pem encoded cert and a key under ~/.rushstack, _not_ the path indicated in the message gulp prints to the console. Don Kirkham. "Developer Certificate Changes in SPFx v1.12.1". _Don_Kirkham_, 30 June 2021, https://www.donkirkham.com/blog/spfx-dev-cert/.

```
[trust-cert] Automatic certificate trust is only implemented for debug-certificate-manager on Windows and macOS. To trust the development certificate, add this certificate to your trusted root certification authorities: "/home/philip/Projects/viva-connections-lab/spfx-company-announcements-webpart/node_modules/@rushstack/debug-certificate-manager/temp/1637081329673.pem".
```
