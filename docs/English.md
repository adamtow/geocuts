# GeoCuts
GeoCuts runs shortcuts or sends messages using your current location. When paired with Cronios (cronios.com) — the shortcuts scheduler for iOS — GeoCuts does this all automatically as you move about during the day.

> [**Download the latest version of GeoCuts**](https://routineHub.co/shortcut/1732)

![GeoCuts Home](https://adamtow.github.io/geocuts/images/geocuts-home.png)

<span id="overview"></span>
## Overview
As Cronios introduced a new method for automatically running your shortcuts based on time, GeoCuts does the same for location — still with no tapping on notifications banners required.

Each location trigger you create has its own schedule — hours of operation and active days in the week — and you can configure how often a trigger can run again after being triggered. You can also create multiple triggers directly from the iOS Share sheet using the [GeoCuts Helper shortcut](#helper). 

Here are a few ideas on what you can do automatically with GeoCuts:

- **Arrive at Work**: A location trigger that runs once a day from 7-9 a.m. on the weekdays when you enter your work zone. 
- **Leaving Work**: An exit trigger that runs between 5-7 p.m. on the weekdays when you leave your work zone. 
- **Location DND**: A trigger that sets Do Not Disturb mode on whenever you are at your favorite movie theater or restaurant. 
- **Running Music**: A series of location triggers that play your favorite songs or inform you or your friends and family at key points along your running path.  

![GeoCuts Apple Visitor Center](https://adamtow.github.io/geocuts/images/geocuts-apple-visitor-center.png)

## Table of Contents

- [Overview](#overview)
- [Background](#background)
- [System Requirements](#system-requirements)
- [Download and Installation](#download)
- [Creating Your First Location Trigger](#getting-started)
- [How It Works](#how-it-works)
- [Exploring the GeoCuts Interface](#interface)
- [Creating Location Triggers](#creating-location-triggers)
- [Editing Location Triggers](#editing-location-triggers)
- [GeoCuts and Cronios](#cronios)
	- [GeoCuts Helper Shortcut](#geocuts-helper)
- [Settings](#settings)
	- [Location Trigger Defaults](#defaults)
	- [Default Mapping App](#default-mapping-app)
	- [Lock Detection](#lock-detection)
	- [Logging](#logging)
	- [Tools](#tools)
- [Handling Errors](#errors)
- [Developers](#developers)
	- [Shortcut App Framework](#framework)
- [Localization](#localization)
- [License](#license)

<span id="background"></span>
## Background
GeoCuts addresses the problem that you can't automatically run shortcuts based on your location. While there are a number of great apps that let you create location triggers — Find My Friends, Reminders, IFTTT, and Launch Center Pro — none of them can run a shortcut without you having to tap on a notification banner. Here are some pros and cons for each app:

- **GeoCuts**
    - PROS: Works in the background. Automatically runs shortcuts and sends text messages. Dedicated interface for managing your location triggers. 
    - CONS: Requires Cronios be running for background operation. Getting Location and sending text messages requires switching back to Shortcuts app.
- **Find My Friends**
    - PROS: Sends notifications automatically and works invisibly in the background. Can create multiple entrance and exit triggers for notifying friends of your location.
    - CONS: Recipients must have Find My Friends installed and an iOS device. Cannot run shortcuts automatically.
- **Reminders**
    - PROS: Works invisibly in the background.
    - CONS: Requires a tap to run shortcut links in notification banners. Have to manually create shortcut links.
- **IFTTT**
    - PROS: Works in the background as long as the app has been running recently. Integrates with many third-party web services and some native iOS applications. 
    - CONS: Cannot run shortcuts automatically. IFTTT app needs to be running in the background or you can get inconsistent triggering.
- **Launch Center Pro**
    - PROS: Lots of third-party integrations. Works in the background as long as the app has been running recently.
    - CONS: Needs to be running in the background. Requires a tap to run actions in notification banner. Requires subscription for advanced features.

***

<span id="system-requirements"></span>
## System Requirements
GeoCuts requires:

- iOS 12 or higher
- Shortcuts 2.1.2 or higher
- Cronios 1.2.1 or higher

The following permissions need to be granted to the Shortcuts app:

- Contacts (for the pretty menus)
- Location Services
- Notifications

***

<span id="download"></span>
## Download and Installation
Download the latest version from RoutineHub.co:

- [**Download GeoCuts from RoutineHub.co**](https://routinehub.co/shortcut/1732)

When you first install GeoCuts, there will be two setup phases to complete:

1. Customize Shortcut
2. GeoCuts Setup

### Customize Shortcut
First, the Customize Shortcut screen will appear and ask you the following questions:

1. **Siri Language**: Used with the [Lock Detection](#lock-detection) feature, this is the language Siri will speak to you. 
2. **Siri Voice**: The voice Siri will use to speak the Lock Detection prompt. 

![GeoCuts Customize Shortcut](https://adamtow.github.io/geocuts/images/geocuts-customize-shortcut.png)

> NOTE: It may take a few seconds for Shortcuts to record your changes after tapping Done from the Customize Shortcuts and Shortcut Settings screens due to the large size of GeoCuts (almost 5,000 actions).

### GeoCuts Setup
Next, GeoCuts will ask you a series of setup questions. You can change all of these settings later in GeoCuts Settings. 

- **Language**: GeoCuts comes pre-installed for English, but it is fully localized and ready to be translated in your language. [Read the section on localization for more details.](#localization) 
- **Distance Unit**: Choose between Kilometers or Miles when entering Trigger Radius values. If you have reset GeoCuts, you'll be given the opportunity to convert the trigger radius values of your existing location triggers from one distance unit to the other.
- **Current Location Method**: GeoCuts uses one of two methods for retrieving your current location. Get Current Weather is fast but less accurate than the slower but more precise Get Current Location.
- **Default Mapping App**: GeoCuts works with [Apple Maps, Google Maps, and Waze](#default-mapping-app). Make sure you have the last two installed if you want to use them. Otherwise, GeoCuts will give an error when trying to open them. 
- **Lock Detection**: When [running in the background via Cronios](#cronios), GeoCuts can [detect when the screen is off](#lock-detection). GeoCuts can then prompt you to unlock the device in order to evaluate your location triggers. You can also customize the unlock prompt if you changed your Siri Voice and Language in the Customize Shortcut portion of setup.  
- **Logging**: Choose the [level of logging](#logging) you would like GeoCuts to perform. Basic provides just information on the shortcuts that have run via GeoCuts. Extended (recommended) records all the locations that GeoCuts has been run from. Developer provides detailed information to help you develop and debug your location triggers. 
- **GeoCuts Helper**; Information on the [GeoCuts Helper shortcut](#helper) will be shown. Use this shortcut from the iOS Home screen to immediately evaluate your location triggers or from iOS Share Sheet to add new location triggers to GeoCuts. 
- **Cronios**: Information on how to use GeoCuts with Cronios to automatically run shortcuts or send text messages based on your location will be shown next.  
- **Setup Complete**: Create a new location trigger, add the GeoCuts cron job to Cronios, read the documentation, or go to the GeoCuts Home. 

***

<span id="getting-started"></span>
## Creating Your First Location Trigger
Let’s create your first location trigger.

>First be sure you run GeoCuts from the Shortcuts Home screen. With nearly 5,000 action steps, running it from the Shortcuts edit screen will be very slow.

Once GeoCuts is open, follow these steps:

1. Tap **New Location Trigger** to open the **Location Trigger Assistant**. 
2. Enter the location where you want the trigger to occur. You can specify a street address or Latitude and Longitude. For now, enter the special string `{{Current Location}}` to create a location trigger that always runs wherever you are.
3. Choose whether your trigger runs by **arriving** at or **leaving** the location. 
4. Enter the **maximum distance** (in miles or kilometers) from the location where the trigger will occur. ![Create Location Trigger #1](https://adamtow.github.io/geocuts/images/create-location-trigger-1.png)
5. Choose whether you want to send a **text message** or **run a shortcut**. 
6. If you chose message, you can send to up to five recipients. 
7. If you chose shortcut, be sure to select a [background-aware shortcut](#background-aware-shortcuts). You can also optionally add input to your shortcut. ![Create Location Trigger #2](https://adamtow.github.io/geocuts/images/create-location-trigger-2.png)
8. Set **active times** and **active days** for your location trigger. You can for instance, set up a trigger to only run from 8 a.m. to 10:00 a.m. on Monday through Friday. 
9. Set the **repeat interval**, or how long the location trigger must wait after running to run again. 
10. Enter some optional **tags** for the location trigger. You can filter which location triggers appear and run on the GeoCuts Home screen. ![Create Location Trigger #3](https://adamtow.github.io/geocuts/images/create-location-trigger-3.png)
11. Enter a **name** for your new location trigger. 
12. Choose to add a **location-reminder** in the Reminders app to run the [GeoCuts Helper shortcut](#geocuts-helper). 
13. Tap **Home**. ![Create Location Trigger #4](https://adamtow.github.io/geocuts/images/create-location-trigger-4.png)
14. Tap **Run**. 
15. Tap **Run Once**.

GeoCuts will now perform the following tasks automatically:

1. Retrieve your current location. 
2. Evaluate each location trigger to see if we can run it. 
3. Compare each valid location trigger’s location with the current location. 
4. Run shortcuts or send text messages for all matching location triggers. 

By itself, GeoCuts is a great tool for organizing all of your location-based shortcuts. Pair it with [Cronios](https://routinehub.co/shortcut/1267) to give it the power to automatically run your shortcuts or send text messages as you move about in the world. 

***

<span id="how-it-works"></span>
## How It Works
When run by Cronios or manually GeoCuts takes the following steps:

1. Checks the global ON/OFF switch. If OFF, it exits. If ON, it continues to Step 2. 
2. Checks if the device is locked using the [Lock Detection technique from Cronios](http://cronios.com#lock-detection). If the device appears locked and Lock Detection is enabled in Settings, an audible prompt or banner notification with sound appears is presented to the user to unlock the device. If the device still appears to be locked after 10 seconds, exit. Otherwise, continue to Step 3. 
3. Notifies the user that an app switch is about to occur.
4. Switches to the Shortcuts app. To retrieve the current location and send messages, Shortcuts must be the frontmost application. 
5. Retrieves the current location of the device. This may take several seconds if you are using Get Current Location instead of Get Current Weather. 
6. Iterates through all active and filtered location triggers and determines whether the current location lies within the radius of each trigger.
7. For each match, run the command assigned to the trigger: run a shortcut or send a text message. 
8. Exits and returns control back to Cronios or the user. 

***

<span id="interface"></span>
## Exploring the GeoCuts Interface
When you open to the GeoCuts Home screen, you're presented with the following sections of information:

![GeoCuts Interface](https://adamtow.github.io/geocuts/images/geocuts-interface.png)

### Next Steps
These actions appear after you installed GeoCuts or if you have reset your settings.

- **Install GeoCuts Helper**: Adds the Helper shortcut to Shortcuts. This option disappears when you have run the command (you can find it again in Settings). 
- **Add GeoCuts Cron Job to Cronios**: Opens Cronios and adds a cron job for GeoCuts at a check frequency of your choosing. This option moves to the bottom of the Home screen when you first run it. Updating an existing GeoCuts cron job requires Cronios 1.2 or higher.

### ON/OFF and Current Location

- **Enable/Disable Monitoring**: A global ON/OFF switch for GeoCuts. If disabled, you will not be able to monitor your location triggers from Cronios or the GeoCuts Helper shortcut.
- **Get Current Location**: Retrieves your current location using either the [Get Current Location or Get Current Weather action](#current-location).
- **Show Current/Last Location**: Displays either your current location or your last location in your default mapping application.

### Run Options

- **Use Get Current Weather**: Enable this to use the faster but less accurate method for retrieving your current location. Disable this to use the Get Current Location Action, which is slower but more accurate. 
- **Run Only Filtered Location Triggers**: If Enabled, only location triggers matching your current tag filter will be evaluated and run. [Learn more here about tags here](#tags).
- **Open Maps After Running**: If you are actively using a mapping application like Maps, Google Maps, or Wave for turn-by-turn directions, you can enable this setting to return to the app after evaluating your location triggers. Learn more about this feature in the [Open Maps After Running](#open-maps-after-running) section.

### Run Controls

- **Run Continously Via Cronios**: Launches Cronios in "Run Continuously" mode. If you've added the GeoCuts cron job to Cronios, it will automatically run on the schedule that you have assigned. [Learn more about Cronios and Geocuts here](#cronios).
- **Run Once**: Evaluates your location triggers based on your current location. Returns to the GeoCuts Home screen when done.

### Location Triggers

- **New Location Trigger**: Creates a new location trigger. Opens to the Location Trigger Assistant if that preferences has been set, the location trigger edit screen if not. [Learn more about creating location triggers](#creating-location-triggers).
- **Filter**: Choose which location triggers appear in the Home list by filtering based on tags. Depending on the **Run Only Filtered Location Triggers** settings, all location triggers or only those visible will be evaluated when GeoCuts runs.
- **List of Your Location Triggers**: This section lists all of your location triggers, filtered by tag and sorted by enabled status and name. [This section details the information](#location-triggers-information) you see in each location trigger row.
- **Bulk Edit**: Allows you to choose and edit multiple location triggers from your list.
- **Bulk Edit All**: Performs an operation on all of your location triggers.
- **Import Location Triggers**: Import a list of location triggers into GeoCuts. 
- **Update GeoCuts in Cronios**: Once you've added the GeoCuts Cron Job to Cronios, this menu item will appear. It allows you to re-export the cron job back to Cronios and replace the existing cron job with the new one.

### GeoCuts

- **About**: Displays the GeoCuts about screen, which contains version and build number information.
- **Help**: Displays the GeoCuts Help documentation on GitHub. Requires internet access to retrieve documentation.
- **Tip Jar**: Like GeoCuts? I'd appreciate a tip or donation!
- **Settings**: Opens to the [GeoCuts Settings page](#settings).

***

### Location Trigger Information
By default, each location trigger shows the following information:

- **Name**: The name of the location trigger.
- 🎯 - The location trigger is in range. It will be evaluated if you run GeoCuts. This icon appears if you have retrieved the Current Location in the app.
- ⬅️ - Denotes an exit location trigger. The location trigger will run after detecting you have entered the specified location.
- **Location**: The location where the entrance or exit trigger will occur.

![Minimal description labels next to each location trigger.](https://adamtow.github.io/geocuts/images/geocuts-description-labels.png)

Enabling **Show Description Labels** option in [Settings](#settings) will display additional icons next to your location trigger's location.

- ▶️ - The location trigger will run a shortcut.
- 💬 - The location trigger will send a text message.
- ♾ - The location trigger will run every time Cronios successfully evaluates GeoCuts.
- 📆 - The repeat interval for the location trigger has been sent for (calendar) days.
- 1️⃣ - The location trigger has been set up to run once before disabling itself.
- ⏰ - The location trigger has been set up to run every X hours.
- ⏲ - The location trigger has been set up to run every X minutes.
- 🏃‍♀️ - Denotes an active exit trigger. The user must have first entered the zone for this icon to become visible.
- **Trigger radius**: The current trigger radius value in kilometers or miles. 

![Additional description labels for each location trigger are shown when you enable the **Show Description Labels** preference in Settings.](https://adamtow.github.io/geocuts/images/geocuts-description-labels.png)

***

<span id="creating-location-triggers"></span>
## Creating Location Triggers
We have already seen how the [Location Trigger Assistant](#assistant) guides you in creating a new Location Trigger.

>If you prefer, you can turn off the Assistant from Settings. Tapping on New Location Trigger from the home screen will load up the default location trigger template and display the Edit Location Trigger screen. From there you can adjust whatever setting you want in the new location trigger.

If you want to add multiple locations at a time, GeoCuts currently supports three methods:

- **GeoCuts Helper**: Install the [GeoCuts Helper shortcut](#helper) to send items from the iOS Share sheet into GeoCuts. 
- **Run Shortcut**: Shortcut developers can send Locations, Contacts, text with addresses, images, etc. directly to GeoCuts. 
- **Import Location Triggers**: Triggers that you export can be imported on another iOS device running GeoCuts. Location Triggers with the same ID will not be imported. 

In the first two cases, GeoCuts will do its best to extract any addresses from the inputted data. If multiple locations were found, it will present a menu allowing you to choose which locations to import. 

If you choose to import multiple items, they will inherit settings from the [Default Location Trigger template](#default-template), although you will get a chance to modify the following settings:

- **Name**: Set the name of each location trigger individually.
- **Location**: Tweak the location before saving the location trigger.
- **Command**: You can choose to use the default command or apply a single command (text message or shortcut) to every location being imported.

By using one of these methods, you can quickly add multiple location triggers at once, which is useful if you are:

- Running along a known route and you want people to be informed of your progress at certain points. 
- Traveling by car and want to know when you enter (or exit) a city, state, or zone. 
- Remembering the locations where you took your favorite photos or experienced your most rewarding memories.
- Creating zones where certain tasks have to occur. 

***

<span id="editing-location-triggers"></span>
## Editing Location Triggers
When you tap on a location trigger from the GeoCuts Home screen, you'll be directed to the Edit Location Trigger screen. The following menu items will be shown:

![Editing a Location Trigger](https://adamtow.github.io/geocuts/images/edit-location-trigger.png)

- **Enabled**: The ON/OFF switch for the location trigger. 
- **Name**: The name of the location trigger. 
- **Tags**: Keywords for the location trigger. You can filter which triggers appear and run on the GeoCuts Home screen. 
- **Location**: The location where the trigger is centered on. 
- **Trigger Radius**: The maximum distance from the location for the trigger to occur. The distance unit of miles or kilometers is specified in [Settings](#settings).
- **Trigger on Exit**: Enable this if you want the location trigger to run after you enter **and** exit the location.
- **Map Options**: A menu containing the following options:
	- **Open in {{Default Mapping App}}**: Opens the default mapping app to the location trigger's location. ![Open in Maps](https://adamtow.github.io/geocuts/images/open-in-maps.png)
	- **Get Directions Using {{Default Mapping App}}**: Gets directions using the default mapping app to the location trigger's location.
	- **Get Maps URL**: Get an Apple Maps URL to the location trigger's location.
	- **Set Default Mapping App**: Choose between Apple Maps, Google Maps, and Waze as your default mapping application.
- **Command**: The action performed when there is a location match. You can send a text message or run a [background-aware shortcut](#shortcuts). 
    - **Send a Text Message**
        - **Message**: the contents of the SMS or iMessage that will be sent when the Message command has been selected. 
        - **Recipient**: the recipient(s) of the text message when the Message command has been selected. You can specify up to 5 recipients. ![Send a Text Message](https://adamtow.github.io/geocuts/images/send-message.png)
    - **Run a Shortcut**
        - **Shortcut**: the shortcut to run when the location trigger is successfully matched with the device’s current location. 
        - **Optional Input**: optional text input to provide to the shortcut. The input is contained with the [GeoCuts Dictionary](#developer) under the `Input` key. 
- **Schedule**: Configure when the location trigger is active and how frequently it can run.
	- **Active Timeframe**: The times during the day when this location trigger is active. ![Active Timeframe](https://adamtow.github.io/geocuts/images/active-hours.png)
	- **Active Days**: The days of the week on which the location trigger will work. NOTE: If you deselect all days, every day will be selected again.![Active Days](https://adamtow.github.io/geocuts/images/day-schedule.png)
	- **Repeat Interval**: How long the location trigger must wait before being able to be triggered again at the same location. You can specify:
		- **Run Once**: Once the location trigger runs, it turns itself off. Use this for one time events. 
		- **Minutes**: The number of minutes you must wait before the location trigger becomes active again. ![Repeat Interval using minutes](https://adamtow.github.io/geocuts/images/repeat-interval.png)
		- **Hours**: The number of hours you must wait before the location trigger becomes active again. 
		- **Days**: The number of calendar days you must wait before the location trigger becomes active again. 
		- **No Delay**: Repeat the command as often as GeoCuts is called by Cronios. 
- **Display Notification When Run**: Displays a banner notification when the location trigger’s command is run. Specify false to suppress the notification. 
- **Add to Reminders**: Adds a location-reminder to run GeoCuts in your Reminders app. This is useful if you don't plan to run Cronios all the time or if you want an extra reminder that you have a location trigger ready to run when you enter a location.

![Location Reminder](https://adamtow.github.io/geocuts/images/location-reminder.png)

- **Export**: Exports the current location trigger. You can copy and paste the text displayed in the Quick Look window and import it on another iOS device running GeoCuts.
- **Delete**: Deletes the current location trigger. You will be prompted to delete any location-reminders in the Reminders app as well.
- **Home**: Returns to the GeoCuts Home screen.

***

<span id="cronios"></span>
## GeoCuts and Cronios
Take GeoCuts to the next level by pairing it with [Cronios, the shortcuts scheduler for iOS](http://cronios.com). Cronios automatically runs your shortcuts in the background on a schedule of your design. 

To add the GeoCuts cron job to Cronios, perform the following steps:

1. From the GeoCuts Home screen, tap **Next Steps**. ![GeoCuts Cron Job #1](https://adamtow.github.io/geocuts/images/cronios-cronjob-1.png)
2. Tap **Add GeoCuts Cron Job to Cronios**.
3. Choose a check frequency. See section below to determine a value appropriate for your needs.
4. Read the information about importing and enabling the cron job. ![GeoCuts Cron Job #2](https://adamtow.github.io/geocuts/images/cronios-cronjob-2.png)
5. Cronios will now open to the its Import dialog box. Make sure the GeoCuts cron job is selected and tap **Done**.
6. If you already have the GeoCuts cron job installed, Cronios will ask you to replace the existing cron job or keep both. It's recommend to replace the existing one, so you only have one GeoCuts cron job operating at one time.
7. After importing the cron job, you can return to GeoCuts or go to the Cronios Home screen.

![GeoCuts Cron Job #3](https://adamtow.github.io/geocuts/images/cronios-cronjob-3.png)

### Balancing the Frequency of Checks
Because retrieving the device location and sending messages currently requires a switch back to the Shortcuts app, you should be mindful how often you call GeoCuts from Cronios. 

Importing the cron job lets you choose from check intervals of 2, 5, 10, 15, and 30 minutes. You can further adjust the schedule from within Cronios.

>With Cronios 1.2.1 or higher, you can set a cron job’s Repeat Interval like you can with location triggers. So while you can have GeoCuts’ cron job evaluate every 5 minutes, you can set it to run every 30 minutes from the last successful run. Configure the Repeat Interval within GeoCuts cron job entry in Cronios. 

<span id="helper"></span>
### GeoCuts Helper
The GeoCuts Helper shortcut does two things:

1. Creates new location triggers in GeoCuts from the iOS Share sheet.
2. Calls the `Run Once` function of GeoCuts.

![GeoCuts Helper creates new location triggers from the iOS Share sheet.](https://adamtow.github.io/geocuts/images/geocuts-helper.png)

To install GeoCuts Helper, follow these steps:

1. Tap `Settings…` from the GeoCuts Home screen.
2. Tap `Install GeoCuts Helper Shortcut…`.
3. Tap `Open` or `Tap to Install GeoCuts Helpers`.

![Installing the GeoCuts Helper shortcut.](https://adamtow.github.io/geocuts/images/geocuts-helper-install.png)

#### Using GeoCuts Helper from the iOS Share Sheet
You can use GeoCuts Helper from the iOS Share sheet to create new location triggers. Try it using:

- Photos that you have taken with your iPhone. 
- Contacts in your Address Book. 
- Places in the Maps app. 
- PDFs
- Text files. 
- Web pages. 

1. Tap Share. 
2. Choose GeoCuts Helper. 
3. If multiple locations are found in the shared data, a menu will appear allowing you to choose which locations to import. 
4. Select which command to use with the imported locations. 
5. Adjust the location and name of each imported location trigger. 

#### Evaluate Your Location Triggers with GeoCuts
Tapping on GeoCuts Helper from the Shortcuts screen will cause GeoCuts to evaluate all of your location triggers. For even faster access, add GeoCuts Helper to your iOS Home screen and add a Siri phrase.

1. From the Shortcuts home screen, tap the edit button in GeoCuts Helper.
2. Tap the Settings icon in the upper-right.
3. Tap `Add to Siri` and follow the on-screen directions.
4. Tap `Add to Home Screen` and follow the on-screen directions.

![Adding the GeoCuts Helper shortcut to Siri and the iOS Home screen.](https://adamtow.github.io/geocuts/images/geocuts-helper-siri-home.png)

***

<span id="settings"></span> 
## Settings
GeoCuts is highly configurable. From the Settings page (access from the bottom of the Home screen), you can adjust the following options in GeoCuts.

![GeoCuts Settings](https://adamtow.github.io/geocuts/images/geocuts-settings.png)

### General

- [Launch Action](#launch-action)
- [Use Location Trigger Assistant](#location-trigger-assistant)
- [Show Description Labels](#show-description-labels)
- [Use Quick Edit Menu](#use-quick-edit-menu)

<span id="launch-action"></span>
#### Launch Action
You can configure what GeoCuts does when you tap on its icon from the Shortcuts Home screen.

- **GeoCuts Home**: Displays the GeoCuts Home screen.
- **New Location Trigger**: Creates a new location trigger.
- **Run Once**: Evaluates your location triggers and returns to the GeoCuts Home screen.
- **Show Menu**: Displays a menu with the three options above.

<span id="location-trigger-assistant"></span>
#### Use Location Trigger Assistant
The Location Trigger Assistant guides you in creating new location triggers. If you want to go directly to the location trigger edit screen, disable this option.

<span id="show-description-labels"></span>
#### Show Description Labels
Displays additional information about a location trigger in the description area below the name (on the GeoCuts Home page).

![Description labels for each location trigger.](https://adamtow.github.io/geocuts/images/geocuts-description-labels.png)

<span id="use-quick-edit-menu"></span>
#### Use Quick Edit Menu
By default, tapping on a location trigger from the GeoCuts Home screen will open the selected location trigged in the Edit Location Trigger screen. Enabling the **Use Quick Edit Menu** option will present a menu with commonly used actions:

- **Enable/Disable**: Global ON/OFF switch for this location trigger.
- **Edit**: Opens the Edit Location Trigger window.
- **View in Maps/Google Maps/Waze**: Open the location in the location trigger using your default mapping application.
- **Delete**: Delete the selected location trigger.
- **Clear Last Run Date**: Clearing the Last Run Date is useful if you are testing your location trigger and have set a Repeat Interval time (i.e. run after 5 minutes or after 10 hours).

<span id="defaults"></span>
### Defaults

- **Use Miles**: GeoCuts can calculate trigger radiuses in either miles or kilometers. Changing from one to another will cause GeoCuts to prompt you if you want to re-calculate the existing trigger radius values.
- **Set Default Mapping App**: Choose between Apple Maps, Google Maps, or Waze. For the last two, you must have those apps installed.
- **Edit Default Location Trigger**: You can edit the default template for location triggers. Suppose you want all of your entries to run during the weekdays from 9-12 pm. Instead of modifying each location trigger as you add them, you can update the default template.

<span id="default-mapping-app"></span>
#### Default Mapping Application
Your default mapping application is used with the following commands in GeoCuts:

- **Show Current Location**: From the GeoCuts Home screen, this opens the mapping application to your current location.
- **Show Last Location**: From the GeoCuts Home screen, this opens the mapping application to your last recorded location.
- **Open After Run**: When running GeoCuts via Cronios, this switches your iOS device to the mapping application after your location triggers have been evaluated.
- **Open in**: From the location trigger edit screen, this opens the mapping application to the location trigger's location.
- **Get Directions Using**: From the location trigger edit screen, this instructs the mapping application to show directions to the location trigger's location.

<span id="lock-detection"></span>
### Lock Detection
When running automatically via Cronios, GeoCuts can detect when it is running but your device is locked. It does so by checking the device brightness. If it's 0, GeoCuts considers the device locked. GeoCuts can display an audible notification banner or speak to you. 

It will then wait 10 seconds before evaluating the brightness value again. If the brightness value is above 0, it considers the device unlocked and continues evaluating your location triggers. If the device brightness remains 0, GeoCuts does not do any evaluation and returns control back to Cronios.

- **Enable Lock Detection**: The ON/OFF toggle for Lock Detection. If you disable Lock Detection, GeoCuts will not run when it thinks your device is locked.
- **Audibly Ask to Unlock Your Device**: Prompts you with the Siri voice to ask you to unlock your device.
- **Set Unlock Prompt Volume**: You can set the volume of the unlock prompt or use the current system volume (set the value to 0).
- **Custom Unlock Prompt**: You can customize the unlock prompt the iOS device speaks to you. If you set a custom Siri Voice and Language, you'll want to set a customized unlock prompt in your language.

#### Limitations
Lock Detection is not perfect and has the following limitations: 

1. If your device is locked but the screen is on, lock detection will not work. GeoCuts will try to get the current location, but it will fail and crash GeoCuts and Cronios. You will have to restart Cronios and GeoCuts to resume location trigger evaluation.
2. If you manually set your device brightness to 0, GeoCuts will consider the device locked.

### Advanced

<span id="logging"></span>
- **Log Level**: GeoCuts can be configured to write to a log file to iCloud Drive. Select from one of four logging levels:
	1. **No Logging**
	2. **Basic**: Only run activity will be recorded.
	3. **Extended**: GeoCuts will write to a location log of all the places it has checked your location triggers.
	4. **Developer**: Additional information is recorded about each location trigger and they are evaluated and run by GeoCuts.
- **Switch to Shortcuts Immediately**: In order to check your current location, GeoCuts must switch back to the Shortcuts app. This context shift can be jarring, so by default, a notification banner appears and GeoCuts waits 2 seconds before switching applications. Enable this preference to immediately switch to the Shortcuts app.
- **Enable Debug Mode**: Displays additional information when running GeoCuts, including the next function call being made and how long the application has stayed in the current loop iteration.

<span id="tools"></span>
### Tools

- **Install GeoCuts Helper Shortcut**: Installs the shortcut that can be used from the iOS Share sheet to create new location triggers.
- **View Logs**: Displays and run and location logs for the current device.
- **Export Location Triggers**: Exports all of your location triggers into a GeoCuts Export Dictionary object. You can take this and import it into another iOS device running GeoCuts.
- **Import Location Triggers**: Import location triggers into GeoCuts. The input must be a valid GeoCuts Export Dictionary object.
- **Check For Updates**: Checks for updates to GeoCuts on GitHub.
- **Change Language**: Change to a different language.
- **Reset**: Reset GeoCuts back to factory settings, erase all content and settings from GeoCuts, or clear the Shortcuts icon cache.i

*** 

<span id="errors"></span>
## Handling Errors
When getting the current location, you may experience the following error conditions:

1. GPS location cannot be retrieved.
2. Network is offline.
3. One of you location triggers has an invalid location.

Because Shortcuts does not provide much in the way of error checking, this error will terminate GeoCuts (and Cronios, if it was running in the background). GeoCuts will not run in automatic evaluation mode until you clear the error, which you can do simply by opening the application to the GeoCuts Home screen.

If the error was a result of an invalid location, you must correct the location trigger before you can continue evaluation.

*** 

<span id="developers"></span>
## Developers
GeoCuts sends a special GeoCuts dictionary to all shortcuts that it calls from a location trigger. The GeoCuts dictionary has the following fields defined:

- **GeoCuts**: A boolean value true means the shortcut is being run from GeoCuts.
- **Name**: The name of the location trigger.
- **Location**: The current location.
- **Exit**: A boolean value of true means the shortcut is an exit trigger.
- **Trigger Radius**: The maximum distance from the location that the device could be in.
- **Input**: Optional input sent to the shortcut. 
- **Online**: A boolean value denoting your current network status. True means online and false means offline.
- **Last Run**: The date the location trigger last ran.
- **Distance**: The distance calculated from your current location and the trigger location.
- **Distance Unit**: The user's distance unit, Miles or Kilometers.
- **Distance Unit String**: The distance unit as a localized string.

With the information in the GeoCuts dictionary, you can perform many custom actions. 

<span id="framework"></span>
### App Framework
GeoCuts was developed using the [Shortcut App Framework](https://routinehub.co/shortcut/1510) approach to developing application-like shortcuts. This framework was also used to develop:

- [**Cronios**](https://routinehub.co/shortcut/1267): The shortcuts scheduler for iOS.
- [**Inspector**](https://routinehub.co/shortcut/1106): View and modify objects at runtime in your shortcuts.
- [**LaunchCuts**](https://routinehub.co/shortcut/959): Folders and tags for your organizing and launching your shortcuts.
- [**WatchCuts**](https://routinehub.co/shortcut/1864): Trigger shortcuts on your iPhone and iPad using any of your iCloud-connected devices: iPhone, iPad, Mac, Apple Watch, or iCloud.com!

Learn more how you can create your own [shortcut applications with App Framework here](https://tow.com/shortcuts/framework).

*** 

<span id="localization"></span> 
## Localization
GeoCuts comes pre-installed for the English language, but the app is fully localized and ready to be translated into different languages. If you would like to help translate GeoCuts, submit a pull request based off of the [English.json localization template](https://github.com/adamtow/geocuts/blob/master/localization/English.json) on GitHub.

GeoCuts is a complicated shortcut application, and there are a lot of strings to translate. 

<span id="license"></span>
## License
Copyright (c) 2019 Adam Tow • tow.com • @atow

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT  SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
