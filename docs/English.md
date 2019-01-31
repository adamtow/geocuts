# Location Triggers for Cronios
Location Triggers works with Cronios, the shortcuts scheduler for iOS, to automatically run shortcuts or send text messages based on your current location.

You can also create new Location Triggers from the iOS Share Sheet in Maps and Contacts. 

As Cronios lets you automate your iOS device based on time, Location Triggers does the same for locations!

## Background
Today, you can use products like Find My Friends, Reminders, IFTTT, Launch Center Pro, and now Location Triggers for Cronios to perform some action when you enter (or exit) a location. There are pros and cons to each of these apps:

- **Location Triggers**
    - Pros: Works in the background. Automatically sends text messages and runs shortcuts. Dedicated interface for managing your Location Triggers. 
    - Cons: Requires Cronios be running for background operation. Getting Location and sending text messages requires switching back to Shortcuts app temporarily.
- **Find My Friends**
    - Pros: Sends notifications automatically and works in the background.
    - Cons: Requires recipients have Find My Friends installed and an iOS device. Cannot run shortcuts automatically. 
- **Reminders**
    - Pros: Works in the background.
    - Cons: Cannot run shortcuts automatically. Requires a tap to run actions in notification banner.
- **IFTTT**
    - Pros: Works in the background as long as the app has been running recently. Integrates with many third-party web services.
    - Cons: Cannot run shortcuts automatically. IFTTT app needs to be running in the background. Sometimes inconsistent triggering.  Cannot send text messages without paid third-party services. 
- **Launch Center Pro**
    - Pros: Lots of third-party integrations. Works in the background as long as the app has been running recently.
    - Cons: Cannot run shortcuts automatically. LCP needs to be running in the background. Requires a tap to run actions in notification banner. Requires subscription for advanced features.

## Table of Contents



***

## System Requirements
Location Triggers for Cronios requires:

- iOS 12
- Shortcuts 2.1.2 or higher
- Cronios 1.2 or higher

The following permissions need to be granted to the Shortcuts app:

- Contacts (for the pretty menus)
- Location Services
- Notifications

***

## Download and Installation
Download the latest version from RoutineHub.co:

- [**Download Location Triggers for Cronios**](https://routinehub.co/shortcut/1732)

When you first install Location Triggers for Cronios, you will ask to configure the following options:

1. **Distance Unit**: Miles or Kilometers
2. **Siri Language**: Used with the [Lock Detection](#lock-detection) feature, this is the language Siri will speak to you. 
3. **Siri Voice**: The voice Siri will use to speak the Lock Detection prompt. 


***

## Creating Your First Location Trigger

Let’s create your first Location Trigger by following these steps:

1. Open Location Triggers for Cronios in Shortcuts.
2. Tap New…
3. Enter the location where you want the trigger to occur. You can specify a street address or Latitude and Longitude. Entering `{{Current Location}}` will create a location trigger that always runs wherever your are.
4. Enter your Trigger Radius, the maximum distance (in miles or kilometers) from the location where the trigger will occur. 
5. Choose whether you want to send a text message or run a shortcut. 
6. If you chose message, you can send to up to five recipients. 
7. If you chose shortcut, be sure to select a background-aware shortcut. 
8. Set the repeat schedule. By default, Location Triggers run once. You can set the Location Trigger to run according to a schedule of your design. 
9. Tap Home. Your changes are automatically saved.
10. Tap Run Once…

If you are within the trigger radius of the location trigger, your message will be sent or your shortcut will be automatically run.





***

## Location Triggers
Location Triggers consist of the following components:

- **Enabled**: The on/off switch for the Location Trigger. 
- **Name**: The name of the Location Trigger. 
- **Location**: The location where the trigger is centered on. 
- **Trigger Radius**: The maximum distance from the location for the trigger to occur. The distance unit of miles or kilometers is specified from the Customize Shortcut… page. 
- **Active Timeframe**: The times during the day when this Location Trigger is active. 
- **Active Days**: The days of the week on which the Location Trigger will work. 
- **Repeat Interval**: How long the Location Trigger must wait before being able to be triggered again at the same location. You can specify:
	- **Run Once**: Once the Location Trigger runs, it turns itself off. Use this for one time events. 
	- **Minutes**: The number of minutes you must wait before the Location Trigger becomes active again. 
	- **Hours**: The number of hours you must wait before the Location Trigger becomes active again. 
	- **Days**: The number of calendar days you must wait before the Location Trigger becomes active again. 
	- **No Delay**: Repeat the command as often as Location Triggers for Cronios is called by Cronios. 
- **Command**: The action performed when there is a location match. You can send a text message or run a [background-aware shortcut](#shortcuts). 
    - **Send a Text Message**
        - **Message**: the contents of the SMS or iMessage that will be sent when the Message command has been selected. 
        - **Recipient**: the recipient(s) of the text message when the Message command has been selected. You can specify up to 5 recipients. 
    - **Run a Shortcut**
        - **Shortcut**: the shortcut to run when the location trigger is successfully matched with the device’s current location. 
- **Success Notification**: Displays a banner notification when the Location Trigger’s command is run. Specify false to suppress the notification. 

## How It Works
When run by Cronios or manually Location Triggers takes the following steps:

1. Checks the global ON/OFF switch. If OFF, it exits. If ON, it continues to Step 2. 
2. Checks if the device is locked using the [Lock Detection technique from Cronios](http://cronios.com#lock-detection). If the device appears locked and Lock Detection is enabled in Settings, an audible prompt or banner notification with sound appears is presented to the user to unlock the device. If the device still appears to be locked after 10 seconds, exit. Otherwise, continue to Step 3. 
3. Notifies the user that an app switch is about to occur. 
4. Switches to the Shortcuts app. To retrieve the current location and send messages, Shortcuts must be the frontmost application. 
5. Retrieves the current location of the device. This may take several seconds. 
6. Iterates through all active and available Location Triggers and determines whether the current location lies within the radius of each trigger.
7. For each match, run the command assigned to the trigger: run a shortcut or send a text message. 
8. Exits and returns control back to Cronios or the user. 

## Balancing the Frequency of Checks
Because retrieving the device location and sending messages currently requires a switch back to the Shortcuts app, you should be careful how often you call Location Triggers for Cronios in Cronios itself. 

Importing the cron job lets you choose from check intervals of 5, 15, and 30 minutes. You can further adjust the schedule from within Cronios. 

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

## Cronios and GeoCuts

## Creating Location Triggers

<span id="settings"></span> 
## Settings


<span id="current-location"></span>
### Current Location

<span id="open-maps-after-running"></span> 
### Open Maps After Running