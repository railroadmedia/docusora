# Push Notifications

### Basic Push Notifications

These notifications only have a title and body, and when tapped by the user, it will open the app.

**To send a basic push notification**...

1. In a campaign workflow, add a Push Notification block to whenever you want the messaging to send.
   ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer_io_push_notification.gif)
2. Click the Push Notification block to name the Push Notification and access some other settings. Click on "Add Content" to configure the push notification content.
3. Fill in the notification **Title** and **Message** fields. You can see a preview of the notification on the right of the screen on both iOS and Android devices and in different formats.
4. Save the Push Notification.
5. It is encouraged to test the push notification on your own device. To do so...
   1. Click on "Send test..." in the upper right corner of the screen.
   2. Choose iOS or Android, depending on the device you have.
   3. Fill in your device token. To find this token, you must go to your Customer IO profile and find your device under "Devices". You can easily copy the token by hovering over the text below the device name and clicking the icon shown below.
      ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer_io_device_token.png)
6. If you see the notification on your device, it's working as expected! If not, let Joel know and we can troubleshoot. 

### Rich Push Notifications

These notifications attach a deep link and/or an image to the notification. When tapped by the user, it will open the app at a specific page.

**To send a rich push notification**...

1. Follow steps 1 - 3 for basic Push Notifications.
2. If you want to include an image to the notification, add a valid image URL to the **Image** field.
3. If you want to include a deep link to the notificaiton, add the following to the **Custom Data** field:
   ```
   {
   
       "uri": "ADD YOUR URL HERE"
    
   } 
   ```
   ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer_io_uri.png)
4. Save the notification.
5. It is encouraged to test the push notification on your own device. To do so...
   1. Click on "Send test..." in the upper right corner of the screen.
   2. Choose iOS or Android, depending on the device you have.
   3. Fill in your device token. To find this token, you must go to your Customer IO profile and find your device under "Devices". You can easily copy the token by hovering over the text below the device name and clicking the icon shown below.
      ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer_io_device_token.png)
6. If you see the notification on your device, it's working as expected! If not, let Joel know and we can troubleshoot. 

# In-App Messaging

In-app Messaging allows us to send a modal-type notification to users that are highly customizable.

![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer-io-in-app-message.gif)

**To send an in app message...** 
1. In a campaign workflow, add an In-App Messsage block to whenever you want the message to send.
   ![In app message block](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer-io-in-app-message-block.gif)
2. Click the In-App Message block to name the In-App Message and access some other settings. Click on "Add Content" to configure the message content.
3. Click the **Choose Recipient** dropdown, and set the **To** field to "id". Setting it to email **_will not work!_**.
   ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer-io-id.png)
4. In the **Page Rule** section, select iOS and Android, and set the rules for which pages you want this message to appear on. A list of all of the page names in the app can be found at the end of this guide.
   ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer-io-page-rules.png)
5. Make sure the **Display** section is set to "Modal".
6. Click the **Message** dropdown to choose which in-app message you would like to send. Please note you need to create them first. [Creating an in app message](https://customer.io/docs/in-app-messages/)
7. The other settings can be set as needed. 
8. Save the changes and send a test message by pressing the "Send test..." button in the top right corner.
   1. Send the message to your accounts "id" (**NOT cio_id**). To see the in-app message, navigate to the page(s) set in the Page Rule section. It may take a moment to pop up.
9. If you see the in-app message, it's working as expected! If not, let Joel know and we can troubleshoot.

**TIP: Make the message dynamic with [variables](https://customer.io/docs/in-app-messages/#template-variables)! Use `{{customer.<variable>}}` in the fields to make the messaging unique the user.**
![](https://github.com/railroadmedia/docusora/blob/master/docs/images/customer-io-variables.png)

## Deeplinks in In-App Messages

Deeplinks are a powerful tool that allows us to direct our users to any (supported) page in our app. In order to use deeplinks in In-App messages, we need to use Custom Actions when creating the In-App Message.

**To include a Deeplink in an In-App message...**
1. Head to [this page](https://fly.customer.io/workspaces/101782/journeys/in-app-messages) and either create a new message from a template or edit an existing message. See the message "Example Deeplink" for reference. 
2. In the desired Action component, ensure the Action type is "Custom Action."
3. In the field below the Action type, insert the desired URL to open inside the app.
4. **IMPORTANT** Finally, name the action "deeplink" with NO CAPITALS and one word. If this is incorrect, the action will not work.

![](https://raw.githubusercontent.com/railroadmedia/docusora/master/docs/images/Screenshot%202023-07-04%20at%2011.24.26%20AM.png)

## List of in-app pages

These app pages are case sensitive, so make sure you enter the correct capitalization into the **Page Rule** section!

| Page Name | Clarification |
| --- | --- |
| SignUp | |
| Login | |
| SignupOnboarding | The onboarding screens when a user logs into the unified app for the first time |
| Home | |
| ExpiredMembershipCatalogue | This is the expired membership home page |
| PackCatalogue | This is the pack-only user home page |
| Shows | |
| SearchScreen| |
| Coaches | |
| CoachOverview | |
| Method | |
| MethodLevel | The overview for a method level |
| Foundation | |
| CourseOverview | |
| ShowOverview | |
| QuickTips | |
| Podcast | |
| Bootcamps | |
| Profile | |
| ProfileMenu | |
| NotificationSettings | |
| ProfileUpdate | |
| Packs | |
| PackOverview | |
| Lessons| This is Guitareo's lessons page |
| Downloads | |
| MyList | |
| Notifications | |
| Lesson | This is any lesson page |
| Song | This is a lesson page, but for songs |
| GuitarQuest | |
| 500Songs | |
| Forum | |
| Settings | |
| DeleteAccount | |
| Support | |
| Routines | |

If you don't see the page you are looking for, let Joel know and he can add it to this list.
