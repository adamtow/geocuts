# Location Triggers for Cronios

Trigger the running of shortcuts or sending of text messages when you arrive at a location. Location Triggers for Cronios makes it easy to define a series of Location Triggers that automate tasks based on your current location. 

you want automated tasks to occur. Working in conjunction with Cronios, you will able to able automate 

## Download and Installation

## System Requirements

## Location Triggers
Location Triggers consist of the following components:
- **Enabled**: The on/off switch for the Location Trigger. 
- **Name**: The name of the location Trigger. 
- **Location**: The location where the trigger is centered on. 
- **Trigger Radius**: Maximum distance from the location. You can specify either miles or kilometers.
- **Active Timeframe**: The times during the day when this Location Trigger is active. 
- **Active Days**: The days of the week on which the Location Trigger will work. 
- **Repeat Interval**: How long the Location Trigger must wait before being able to be triggered again at the same location. You can specify:
	- Don’t Repeat: 
	- Minutes:
	- Hours: 
	- Days: 
	- No Delay: 
- **Command**: The action performed when there is a location match. Right now, you can send a text message or run a shortcut. 
    - **Send a Text Message**
        - **Message**: the contents of the SMS or iMessage that will be sent when the Message command has been selected. 
        - **Recipient**: the recipient of the text message when the Message command has been selected. 
    - **Run a Shortcut**
        - **Shortcut**: the shortcut to run when the location trigger is successfully matched with the device’s current location. 
- **Success Notification**: Displays a banner notification when the Location Trigger’s command is run. Specify false to suppress the notification. 

## How It Works
When run by Cronios or manually Location Triggers takes the following steps:

1. Checks its global ON/OFF switch. If OFF, it exits. If ON, it continues to Step 2. 
2. Checks if the device is locked using the [Lock Detection technique from Cronios](http://cronios.com#lock-detection). If the device appears locked and Lock Detection is enabled in Settjngs, provide an audible prompt to the user to unlock the device. If the device still appears to be locked, exit. Otherwise, it continued to Step 3. 
3. Notifies the user that an app switch is about to occur. 
4. Switches to the Shortcuts app. To retrieve the current location and send a text message, Shortcuts must be the front most application. 
5. Retrieved the current location of the device. This may take several seconds. 
6. Iterates through all of your Location Triggers and sees if the current location lies within the radius of your trigger.
7. For each match, run the command assigned to the trigger: run a shortcut or send a text message. 
8. Exits and returns control back to Cronios or the user. 

## Balancing the Frequency of Checks
Because retrieving the device location and sending the text message currently requires a switch back to the Shortcuts app

## Alternatives
Here are some alternatives to using Location Triggers for Cronios:

- **IFTTT**: Requires an IFTTT account, the iOS app, and that the app has been opened within past day (not force quit). 
- **Launch Center Pro**: 
- **Find My Friends**: 