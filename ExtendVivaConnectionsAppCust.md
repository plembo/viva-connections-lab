# Microsoft Learn: Extend Viva Connections desktop with app customizers
https://docs.microsoft.com/en-us/learn/modules/viva-connections-extend-with-app-customizers

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

Create(d) a SharePoint list named "Announcements" with sample data.

## Create a SharePoint Framework extension
https://docs.microsoft.com/en-us/learn/modules/viva-connections-extend-with-app-customizers/4-exercise-extend-viva-connections-desktop-with-application-customizers

Build a SharePoint Framework application customizer that gets announcements from the SharePoint list and displays at the top of the home page.

* Create a project folder, ```spfx-company-announcements-appcustomizer```.
* Step through creating the web extension, starting with scaffolding using ```yo @microsoft/sharepoint```.
* Run ```npm install @microsoft/sp-office-ui-fabric-core``` to install the Office UI Fabric package (will be needed later to style the app). 
* Install the dev certificate with ```gulp trust-dev-cert```.
* Edit ImportantCompanyAnnouncementsApplicationCustomizer.ts under src/extensions/importantCompanyAnnouncements/.

## Test the extension on a page
* Run ```gulp serve --nobrowser``` to launch web server on https://localhost:4321.
* Get id value from src/extensions/importantCompanyAnnouncements/ImportantCompanyAnnouncementsApplicationCustomizer.manifest.json file.
* Go to debug page:
```https://[yourtenant].sharepoint.com/SitePages/home.aspx?debugManifestsFile=https://localhost:4321/temp/manifests.js&loadSPFX=true&customActions={"<id>":{"location":"ClientSideExtension.ApplicationCustomizer","properties":{ }}}```
* Choose "Load debug scripts".
* "Important announcements" should now appear on top of page.

## Deploy the extension to Viva Connections
* Build the solution in release mode with ```gulp bundle --ship```.
* Make the release mode package with ```gulp package-solution --ship```.
* Package should be under sharepoint/solution as spfx-announcements-appcustomizer.sppkg file.
* Upload the package to the SharePoint app catalog.
* Deploy the package.
* Add the package to the site (Settings... SharePoint... Add an app)
* Use browser to confirm announcements banner now appears on home site front page.
* Do the same by checking home page in Teams.
