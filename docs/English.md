# GeoCuts
GeoCuts automatically runs your shortcuts or sends text messages using your current location. As Cronios introduced a new method for automatically running your shortcuts based on time, GeoCuts does the same for location!

You can also create new GeoCuts location triggers from the iOS Share sheet in Maps and Contacts. 

## Background
GeoCuts addresses the problem of  automatically running shortcuts based on your location. While there are a number of great apps that let you create location triggers -- Find My Friends, Reminders, IFTTT, and Launch Center Pro -- none of them can run a shortcut without you having to tap on a notification banner. 

Here are some pros and cons for each app:

- **GeoCuts**
    - Pros: Works in the background. Automatically sends text messages and runs shortcuts. Dedicated interface for managing your location triggers. 
    - Cons: Requires Cronios be running for background operation. Getting Location and sending text messages requires switching back to Shortcuts app.
- **Find My Friends**
    - Pros: Sends notifications automatically and works invisibly in the background.
    - Cons: Requires recipients have Find My Friends installed and an iOS device. Cannot run shortcuts automatically. 
- **Reminders**
    - Pros: Works invisibly in the background.
    - Cons: Requires a tap to run shortcut links in notification banners.
- **IFTTT**
    - Pros: Works in the background as long as the app has been running recently. Integrates with many third-party web services and some native iOS applications. 
    - Cons: Cannot run shortcuts automatically. IFTTT app needs to be running in the background or you can get  inconsistent triggering.
- **Launch Center Pro**
    - Pros: Lots of third-party integrations. Works in the background as long as the app has been running recently.
    - Cons: Needs to be running in the background. Requires a tap to run actions in notification banner. Requires subscription for advanced features.

## Table of Contents



***

## System Requirements
GeoCuts requires:

- iOS 12
- Shortcuts 2.1.2 or higher
- Cronios 1.2.1 or higher

The following permissions need to be granted to the Shortcuts app:

- Contacts (for the pretty menus)
- Location Services
- Notifications

***

## Download and Installation
Download the latest version from RoutineHub.co:

- [**Download GeoCuts**](https://routinehub.co/shortcut/1732)

When you first install GeoCuts, there will be two phases to set up:

1. Customize Shortcut
2. GeoCuts Setup

### Customize Shortcut
The Customize Shortcuts screen will appear and ask you the following questions:

1. **Siri Language**: Used with the [Lock Detection](#lock-detection) feature, this is the language Siri will speak to you. 
2. **Siri Voice**: The voice Siri will use to speak the Lock Detection prompt. 

![GeoCuts Customize Shortcut](https://adamtow.github.io/geocuts/images/geocuts-Customize-shortcut.png)

>It may take a few seconds for the Customize Shortcuts screen to disappear when you hit Done. GeoCuts is a very large shortcut (nearly 4,000 actions), and the Shortcuts app seems to take a while updating the Siri Language and Voice actions. 

### GeoCuts Setup
Next, GeoCuts will ask you a series of setup questions. You can change all of these settings later in GeoCuts Settings. 

- **Language**: GeoCuts comes pre-installed for English, but it is fully localized and ready to be translated in your language. [Read the section on localization for more details.](#localization) 
- **Distance Unit**: Choose between Kilometers or Miles when entering Trigger Radius values. 
- **Current Location Method**: GeoCuts uses one of two methods for retrieving your current location. Get Current Weather is fast but less accurate than the slower but more precise Get Current Location.
- **Default Mapping App**: GeoCuts works with Apple Maps, Google Maps, and Waze. Make sure you have the last two installed if you want to use them. Otherwise, GeoCuts will give an error when trying to open them. 
- **Lock Detection**: When [running in the background via Cronios](#cronios), GeoCuts can detect when your device is locked and the screen is off. GeoCuts can then prompt you to unlock the device in order to evaluate your location triggers. You can also customize the unlock prompt if you changed your Siri Voice and Language in the Customize Shortcut portion of setup.  
- **Logging**: Choose the level of logging you would like GeoCuts to perform. Basic provides just information on the shortcuts that have run via GeoCuts. Extended records all the locations that GeoCuts has been run from. Developer provides detailed information to help you develop your location triggers. 
- **GeoCuts Helper**; Information on the GeoCuts Helper shortcut will be shown. Use this shortcut from the iOS Home screen to immediately evaluate your location triggers or from iOS Share Sheet to add new location triggers to GeoCuts. 
- **Cronios**: Information on how to use GeoCuts with Cronios to automatically run shortcuts or send text messages based on your location will be shown next.  
- **Setup Complete**: Create a new location trigger, add the GeoCuts cron job to Cronios, read the documentation, or go to the GeoCuts Home. 



***

## Creating Your First Location Trigger
Let’s create your first location trigger.

>First be sure you run GeoCuts from the Shortcuts Home screen. With over 3,300 action steps, running it from the Shortcuts edit screen will be very slow.

Once GeoCuts is open, follow these steps:

1. Tap New…
2. Enter the location where you want the trigger to occur. You can specify a street address or Latitude and Longitude. For now, enter the special string `{{Current Location}}` to create a location trigger that always runs wherever you are.
3. Choose whether your trigger runs by entering or exiting the location. 
4. Enter the maximum distance (in miles or kilometers) from the location where the trigger will occur. 
5. Choose whether you want to send a text message or run a shortcut. 
6. If you chose message, you can send to up to five recipients. 
7. If you chose shortcut, be sure to select a [background-aware shortcut](#background-aware-shortcuts). 
8. Set active times and days for your location trigger. You can for instance, set up a trigger to only run from 8 a.m. to 10:00 a.m. on Monday through Friday. 
9. Set how long the location trigger must wait after running to run again. 
10. Enter a name for your new location trigger. 
11. Tap Home. 
12. Tap Run. 
13. Tap Run Once…

GeoCuts will now perform the following tasks automatically:

1. Retrieve your current location. 
2. Evaluate each location trigger to see if we can run it. 
3. Compare each valid location trigger’s location with the current location. 
4. Run shortcuts or send text messages for all matching location triggers. 

By itself, GeoCuts is a great tool for organizing all of your location based shortcuts.

>Using the included GeoCuts Helper shortcut, you can create a Siri phrase to run GeoCuts in Run Once Mode by saying, "Run My Location Triggers" or "Evaluate My Current Location." 

When paired with Cronios, however, it gains tremendous power by being able to run shortcuts or send text messages automatically based on your current location. 

***

## Location Triggers
Location triggers consist of the following components:

- **Enabled**: The on/off switch for the location trigger. 
- **Name**: The name of the location trigger. 
- **Location**: The location where the trigger is centered on. 
- **Trigger Radius**: The maximum distance from the location for the trigger to occur. The distance unit of miles or kilometers is specified from the Customize Shortcut… page. 
- **Active Timeframe**: The times during the day when this location trigger is active. 
- **Active Days**: The days of the week on which the location trigger will work. 
- **Repeat Interval**: How long the location trigger must wait before being able to be triggered again at the same location. You can specify:
	- **Run Once**: Once the location trigger runs, it turns itself off. Use this for one time events. 
	- **Minutes**: The number of minutes you must wait before the location trigger becomes active again. 
	- **Hours**: The number of hours you must wait before the location trigger becomes active again. 
	- **Days**: The number of calendar days you must wait before the location trigger becomes active again. 
	- **No Delay**: Repeat the command as often as GeoCuts is called by Cronios. 
- **Command**: The action performed when there is a location match. You can send a text message or run a [background-aware shortcut](#shortcuts). 
    - **Send a Text Message**
        - **Message**: the contents of the SMS or iMessage that will be sent when the Message command has been selected. 
        - **Recipient**: the recipient(s) of the text message when the Message command has been selected. You can specify up to 5 recipients. 
    - **Run a Shortcut**
        - **Shortcut**: the shortcut to run when the location trigger is successfully matched with the device’s current location. 
- **Success Notification**: Displays a banner notification when the location trigger’s command is run. Specify false to suppress the notification. 


## Exploring the GeoCuts Interface
When you open to the GeoCuts Home screen, you're presented with the following sections of information:

- **Enable/Disable Monitoring**: A global on/off switch for GeoCuts. If disabled, you will not be able to monitor your location triggers from Cronios or the GeoCuts Helper shortcut.
- **Run Continously Via Cronios**: Launches Cronios in "Run Continuously" mode. If you've added the GeoCuts cron job to Cronios, it will automatically run on the schedule that you have assigned. [Learn more about Cronios and Geocuts here](#cronios).
- **Add Cron Job to Cronios**: Adds or updates the GeoCuts cron job in Cronios. Updating requires Cronios 1.2 or higher.
- **Run Once**: Evaluates your location triggers based on your current location. Returns to the GeoCuts Home screen when done.
- **Open Maps After Running**: If you are actively using a mapping application like Maps, Google Maps, or Wave, you can enable this setting to return to the designated app after evaluating your location triggers. Learn more about this feature in the [Open Maps After Running](#open-maps-after-running) section.
- **Get Current Location**: Retrieves your current location using either the [Get Current Weather or Get Current Location action](#current-location).
- **Show Current/Last Location**: Displays either your current location or your last location in your default mapping application.
- **New Location Trigger**: Creates a new location trigger. Opens to the Location Trigger Assistant if that preferences has been set, the location trigger edit screen if not. [Learn more about creating location triggers](creating-location-triggers).
- **List of Your Location Triggers**: This section lists all of your location triggers, sorted by enabled status and name.
- **Bulk Edit**: Allows you to choose and edit multiple location triggers from your list.
- **Bulk Edit All**: Performs an operation on all of your location triggers.
- **About**: Displays the GeoCuts about screen, which contains version and build number information.
- **Help**: Displays the GeoCuts Help documentation on GitHub. Requires internet access to retrieve documentation.
- **Tip Jar**: Like GeoCuts? I'd appreciate a tip or donation!
- **Settings**: Opens to the [GeoCuts Settings page](#settings).

Enabling Show Description labels will display additional icons next to your location trigger's location.

- ▶️ - The location trigger will run a shortcut
- 💬 - The location trigger will send a text message
- ♾ - The location trigger will run every time Cronios successfully evaluates GeoCuts.
- 📆 - The repeat interval for the location trigger has been sent for (calendar) days.
- 1️⃣ - The location trigger has been set up to run once before disabling itself.
- ⏰ - The location trigger has been set up to run every X hours.
- ⏲ - The location trigger has been set up to run every X minutes.
- 🏃‍♀️ - Denotes an exit trigger. The user must exit the viewed zone to if it's possible
- 🎯 - Your location trigger is in range. It will be evaluated if you run GeoCuts.



## Creating Location Triggers

<span id="settings"></span> 
## Settings


<span id="current-location"></span>
### Current Location

<span id="open-maps-after-running"></span> 
### Open Maps After Running


## Cronios and GeoCuts

## How It Works
When run by Cronios or manually GeoCuts takes the following steps:

1. Checks the global ON/OFF switch. If OFF, it exits. If ON, it continues to Step 2. 
2. Checks if the device is locked using the [Lock Detection technique from Cronios](http://cronios.com#lock-detection). If the device appears locked and Lock Detection is enabled in Settings, an audible prompt or banner notification with sound appears is presented to the user to unlock the device. If the device still appears to be locked after 10 seconds, exit. Otherwise, continue to Step 3. 
3. Notifies the user that an app switch is about to occur. 
4. Switches to the Shortcuts app. To retrieve the current location and send messages, Shortcuts must be the frontmost application. 
5. Retrieves the current location of the device. This may take several seconds. 
6. Iterates through all active and available location triggers and determines whether the current location lies within the radius of each trigger.
7. For each match, run the command assigned to the trigger: run a shortcut or send a text message. 
8. Exits and returns control back to Cronios or the user. 

## Balancing the Frequency of Checks
Because retrieving the device location and sending messages currently requires a switch back to the Shortcuts app, you should be careful how often you call GeoCuts in Cronios itself. 

Importing the cron job lets you choose from check intervals of 5, 15, and 30 minutes. You can further adjust the schedule from within Cronios. 


## GeoCuts Helper
The GeoCuts Helper shortcut does two things:

1. Creates new location triggers from Contacts, Map Links, and Locations using the iOS Share sheet.
2. Calls the `Run Once` function of GeoCuts. Add a Siri phrase for this shortcut or add GeoCuts Helper to the iOS Home screen for one step access to evaluating your location triggers.

![GeoCuts Helper creates new location triggers from the iOS Share sheet.](https://adamtow.github.io/geocuts/images/geocuts-helper.png)

To install GeoCuts Helper, follow these steps:

1. Tap `Settings…` from the GeoCuts Home screen.
2. Tap `Install GeoCuts Helper Shortcut…`.
3. Tap `Open` or `Tap to Install GeoCuts Helpers`.

![Installing the GeoCuts Helper shortcut.](https://adamtow.github.io/geocuts/images/geocuts-helper-install.png)

### Using GeoCuts Helper from the iOS Share Sheet
You can use GeoCuts Helper from the iOS Share sheet in the Maps and Contacts applications to create new location triggers.

1. Tap Share
2. Choose GeoCuts Helper

GeoCuts Helper will launch GeoCuts and create a new location trigger based on the address you're looking at in Maps or the current contact card in Contacts.

### Evaluate Your Location Triggers
Tapping on GeoCuts Helper from the Shortcuts screen will cause GeoCuts to evaluate all of your location triggers. For even faster access, add GeoCuts Helper to your iOS Home screen and add a Siri phrase.

1. From the Shortcuts home screen, tap the edit button in GeoCuts Helper.
2. Tap the Settings icon in the upper-right.
3. Tap `Add to Siri` and follow the on-screen directions.
4. Tap `Add to Home Screen` and follow the on-screen directions.

![Installing the GeoCuts Helper shortcut.](https://adamtow.github.io/geocuts/images/geocuts-helper-siri-home.png)

***

## Settings
GeoCuts features many settings to customize its operation to your personal preferences. 

### General

- Show Description Labels
- Use Location Trigger Assistant
- Use Quick Menu

### Defaults

- Set Default Mapping App
- Edit Default Location Trigger

### Current Location

- Use Get Current Weather
- Get Current Location at Startup

### Lock Detection
- Enable Lock Detection
- Audibly Ask to Unlock Device
- Custom Unlock Prompt

### Advanced

- Enable Logs
- Enable Location Log
- Debug

### Tools

- Install Share Sheet Helper
- View Logs
- Check For Updates
- Change Language
- Reset

<span id="localization"></span> 
## Localization
