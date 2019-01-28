# Location Triggers for Cronios
Location Triggers works with Cronios, the shortcuts scheduler for iOS, to automatically run shortcuts or send text messages based on your current location.

You can also create new Location Triggers from the iOS Share Sheet in Maps and Contacts. 

As Cronios lets you automate your iOS device based on time, Location Triggers does the same for locations!

## Background
Today, you can use apps like Find My Friends, Reminders, IFTTT, Launch Center Pro, and now Location Triggers for Cronios to perform some action when you enter or exit a location. There are pros and cons to each of these apps:

- **Location Triggers**
    - Pros: Works in the background. Automatically sends text messages and runs shortcuts. Dedicated interface for managing your Location Triggers. 
    - Cons: Requires Cronios be running for background operation. Getting Location and sending text messages requires switching back to Shortcuts app.
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
    - Cons: Cannot run shortcuts automatically. Needs to be running in the background. Requires a tap to run actions in notification banner. Requires subscription for advanced features.

## Table of Contents



***

## System Requirements
Location Triggers for Cronios requires:

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

- [**Download Location Triggers for Cronios**](https://routinehub.co/shortcut/1732)

When you first install Location Triggers for Cronios, you will ask to configure the following options:

1. **Distance Unit**: Miles or Kilometers
2. **Siri Language**: Used with the [Lock Detection](#lock-detection) feature, this is the language Siri will speak to you. 
3. **Siri Voice**: The voice Siri will use to speak the Lock Detection prompt. 

***

## Creating Your First Location Trigger
Let’s create your first Location Trigger.

>First be sure you run Location Triggers for Cronios from the Shortcuts Home screen. With over 3,300 action steps, running it from the Shortcuts edit screen will be very slow.

Once Location Triggers for Cronios is open, follow these steps:

1. Tap New…
2. Enter the location where you want the trigger to occur. You can specify a street address or Latitude and Longitude. For now, enter the special string `{{Current Location}}` to create a Location Trigger that always runs wherever you are.
3. Choose whether your trigger runs by entering or exiting the location. 
4. Enter the maximum distance (in miles or kilometers) from the location where the trigger will occur. 
5. Choose whether you want to send a text message or run a shortcut. 
6. If you chose message, you can send to up to five recipients. 
7. If you chose shortcut, be sure to select a [background-aware shortcut](#background-aware-shortcuts). 
8. Set active times and days for your Location Trigger. You can for instance, set up a trigger to only run from 8 a.m. to 10:00 a.m. on Monday through Friday. 
9. Set how long the Location Trigger must wait after running to run again. 
10. Enter a name for your new Location Trigger. 
11. Tap Home. 
12. Tap Run. 
13. Tap Run Once…

Location Triggers for Cronios will now perform the following tasks automatically:

1. Retrieve your current location. 
2. Evaluate each Location Trigger to see if we can run it. 
3. Compare each valid Location Trigger’s location with the current location. 
4. Run shortcuts or send text messages for all matching Location Triggers. 

By itself, Location Triggers for Cronios is a great tool for organizing all of your location based shortcuts.

>Using the included Location Triggers Share shortcut, you can create a Siri phrase to run Location Triggers for Cronios in Run Once Mode by saying, “Run My Location Triggers” or “Evaluate My Current Location.” 

When paired with Cronios, however, it gains tremendous power by being able to run shortcuts or send text messages automatically based on your current location. 

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

## Settings
Location Triggers for Cronios features many settings to customize its operation to your personal preferences. 

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
