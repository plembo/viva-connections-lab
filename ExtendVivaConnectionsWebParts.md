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

## Create a SharePoint Framework web part
Important: web parts only work with Viva Connections desktop, they won't work with the mobile Viva Connections app.

Web part will get data from a SharePoint list.

* Create a project folder, ```spfx-company-announcements-webpart```.
* Step through creating the web part, starting with scaffolding using ```yo @microsoft/sharepoint```.
* Install the dev certificate with ```gulp trust-dev-cert```.
* Modify CompanyAnnouncementsWebPart.ts and CompanyAnnouncementsWebPart.module.scss under src/webparts/companyAnnouncements.

## Test web part in SharePoint Framework Workbench
Run ```gulp serve` --nobrowser`` to launch web server on https://localhost:4321. Then go to SharePoint Framework Workbench on tenant to test web part. Workbench URL will be https://[tenantname].sharepoint.com/_layouts/workbench.aspx.

This will not work on Linux [1]

## Deploy the web part to Viva Connections
* Build the solution is release mode with ```gulp bundle --ship```.
* Make the release mode package with ```gulp package-solution --ship```.
* Upload the package to the SharePoint app catalog.
* Deploy the package.
* Add the package to the site (Settings... SharePoint... Add an app)
* Edit the page to include the new web part.


[1] On Linux, running ```gulp trust-dev-cert``` will create a pem encoded cert and a key under ~/.rushstack, _not_ the path indicated in the message gulp prints to the console. Don Kirkham. "Developer Certificate Changes in SPFx v1.12.1". _Don_Kirkham_, 30 June 2021, https://www.donkirkham.com/blog/spfx-dev-cert/.

Although the self-signed cert does load, will get this error when trying to access the Workbench on tenant:

```
[trust-cert] Automatic certificate trust is only implemented for debug-certificate-manager on Windows and macOS. To trust the development certificate, add this certificate to your trusted root certification authorities: "/home/[username]/Projects/viva-connections-lab/spfx-company-announcements-webpart/node_modules/@rushstack/debug-certificate-manager/temp/1637081329673.pem".
```
