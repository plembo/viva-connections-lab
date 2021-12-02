# Extend Microsoft Viva Connections with Adaptive Card extensions
https://docs.microsoft.com/en-us/learn/modules/viva-connections-extend-with-adaptive-card-extensions


Adaptive Cards:
* configurable
* target specific audience (e.g. org or job type)
* UI rendered using Adaptive Cards
* Three templates
    * Basic
    * Image
    * Primary Text
    Fluent UI icons or images for icons
* Quick View
    * Adaptive Card Designer, https://adaptivecards.io/designer/
* Link to other resources
* Work with both desktop and mobile experiences

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

## Create a new solution
https://docs.microsoft.com/en-us/learn/modules/viva-connections-extend-with-app-customizers/4-exercise-extend-viva-connections-desktop-with-application-customizers

Build an Adaptive Card Extension (ACE) to display the latest important company announcement. 

* Create a project folder, ```spfx-company-announcements-ace```.
* Step through creating the ACE, starting with scaffolding using ```yo @microsoft/sharepoint```.
* Install the dev certificate with ```gulp trust-dev-cert```.

## Edit the Adaptive Card extension code
* Modify ImportantAnnouncementsAdaptiveCardExtension.ts under src/adaptiveCardExtensions/ImportantAnnouncements.
* Edit CardView.ts under src/adaptiveCardExtensions/importantAnnouncements/cardView.

## Test the Adaptive Card Extension in the workbench
* Run ```gulp serve --nobrowser``` to launch web server on https://localhost:4321.
* Go to workbench at https://[your tenant].sharepoint.com/_layouts/workbench.aspx.
* Add new ACE to the canvas and then Preview, try View.

## Deploy the extension to Viva Connections
* Build the solution in release mode with ```gulp bundle --ship```.
* Make the release mode package with ```gulp package-solution --ship```.
* Package should be under sharepoint/solution as spfx-company-announcements-ace.sppkg file.
* Upload the package to the SharePoint app catalog.
* Deploy the package.
* Add the package to the site (Settings... SharePoint... Add an app)
* Preview card in Viva Connections and add to Dashboard on desktop.
* Then Preview on mobile.
