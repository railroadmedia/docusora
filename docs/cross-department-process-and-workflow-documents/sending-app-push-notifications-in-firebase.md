# Overview

Drumeo push notifications can be sent via intercom using their messaging system.
Unfortunately because we only use a single intercom account for both drumeo
and pianote, and intercom doesn't support multiple apps per account, we cannot
send campaign-based push notifications to pianote using intercom. Instead, they
must be sent manually via firebase.

Firebase does not have CRM-like functions. It can only send to a specific
device or all devices with the app installed.

# Steps

## Send To A Specific Device
1. Install the pianote app on your phone (if you want to send it to your device)
1. Ask Caleb F to get you the device ID you are looking for (he will need your
   account email)
1. Continue with same process below
   
## Send To All Devices With App Installed
1. Login to the firebase console: 
   [https://console.firebase.google.com/](https://console.firebase.google.com/)
1. Go to the pianote-app: 
   [https://console.firebase.google.com/project/pianote-app/overview](https://console.firebase.google.com/project/pianote-app/overview)
1. In the left-hand menu, go to 'Cloud Messaging': 
   [https://console.firebase.google.com/project/pianote-app/notification](https://console.firebase.google.com/project/pianote-app/notification)
1. Click the 'New notification' button
1. Enter the desired title, text, image (optional), name (optional)
1. Click next
1. Under target select 'User segment', then choose the com.pianote2 (android) 
   target
1. Click 'Target another app'
1. Choose the 'com.drumeo.PianoteApp' option (IOS)
1. Now your notification will go to all installed devices for both android 
   and IOS
1. Click next, schedule the message if desired
1. Enter conversion event details if desired (Caleb doesn't know how those work...)
1. Click next to go to 'Additional options'
1. Leave 'Android Notification Channel' blank
1. In order to set a 'url' that will direct the user to a screen in the app when
   they tap on the notification you must set 2 custom data properties
1. Create 1 new custom data field with the key 'uri', set the value to the website
   url of where you want the user to go when they click the notification. For
   example 'https://www.pianote.com/members' will send them to the main
   members home screen. 'https://www.pianote.com/members/learning-paths/pianote-method/276693'
   will send them to the main method screen. Not all URLs map to a screen in the app.
   URLs should always be tested ahead of time to make sure they map to an app screen
   properly.
1. Create a 2nd custom data field with the key 'type', send the value to 'deeplink'
1. Set the 'Sound', 'IOS badge', and 'Expires' fields accordingly.
1. **It's highly highly recommended to send a test notification to your own device first before publishing.**
1. Open up the first step again 'Notification'
1. Click 'Send test message'
1. Inside the 'Add an FCM registration token' input, enter your device ID you got from Caleb
1. Click the plus to add your device to the list
1. Select your device from the list, click 'test'
1. View the notification on your phone, tap it to make sure it opens to the right screen
1. If everything looks good, you are ready to publish!