In this repository I provide Automations, Scripts and other files for Home Assistant.

The code in this repo is often a slightly modified (and untested) version of my personal version. In case of any issues, feel free to create an [issue](https://github.com/benjamin-dcs/home-assistant/issues)

# Table of Contents
- [Automations](#automations)
- [Scripts](#scripts)  
- [Snippets](#snippets)  

# [Automations](automations)
## [Birthday Notifier](automations/birthday_notifier.yaml)
Uses a Home Assistant calender to send several notifications for someone's birthday. Calendar events are expected to be in one of the following two formats:
- \<Name\>
- \<Name\> (YYYY)

When using the second format, the age is calculated and included in the notification. 
- Sends a notification at 12:00 **_2 days_** prior to the birthday
- Sends a notification at 12:00 **_1 day_** prior to the birthday
- Sends a notification **_every hour_**, starting at day of birth until the notification is _Marked as done_ (You have send a celebration message to the person 🎉).

**Requirements:**
- Switch Helper: input_boolean.birthday_celebration_sent

**Dependencies:**
- Uses the [`Notify Me`](scripts/notify_me.yaml) Script to send the notifications
- Uses the [`Notification Action Handler`](automations/notification_action_handler.yaml) Automation to handle the _'Mark as done'_ action

## [Notification Action Handler](automations/notification_action_handler.yaml)
Generic Automation to handle all my [Actionable Notifications](https://companion.home-assistant.io/docs/notifications/actionable-notifications/).

# [Scripts](scripts)
## [Notify Me](scripts/notify_me.yaml)
Provides a user friendly (visual editor) interface to send a notification to one or multiple notification providers, including Home Assistant Persistent Notifications.

**Features:**
- (Multi-)Selector for Notification Service(s)
- Templatable message field
- Templatable title field
- Data object
- Templatable url field

<p align="center">
<img width="750" alt="image" src="https://github.com/user-attachments/assets/924f8dee-e131-4752-9274-81cb048f8a48">
</p>

## [Get ChatGPT Response](scripts/get_chatgpt_response.yaml)
Provides a user friendly (visual editor) interface to get a ChatGPT response.

**Features:**
- Templatable prompt field
- Selector for language
- Templatable instruction field
- Selector for ChatGPT model. The model(s) should be exactly the same as your OpenAI Conversation entity. For example model `gpt_4o_mini` uses `conversation.gpt_4o_mini` as conversation agent.

<p align="center">
<img width="750" src="https://github.com/user-attachments/assets/4fdc4578-1b34-4e14-addf-e1880ea3647e">
</p>

## [Set Input Text with ChatGPT](scripts/set_input_text_with_chatgpt.yaml)
In the majority of my use-cases for a ChatGPT response, I store the result in a Text-Helper. I then use this Text-Helper as the source for my Automation/Script when it runs. At the end of the Automation/Script, I run this `Set Input Text with ChatGPT`-script to renew the Text-Helper. This has two advantages:
- No extra wait-time from ChatGPT before I need the response. For example, in my doorbell automation I want the notifcation to be send as quickly as possible.
- When ChatGPT isn't responding for whatever reason, my automation/script will still continue to run because the text is already stored.

**Features:**
- Templatable prompt field
- Selector for language
- Templatable instruction field
- Selector for ChatGPT model.
- Entity-Selector
- Remove First And Last Quotes Switch. For some prompts, ChatGPT's response is quoted. This option removes the first and last quote from the response.

<p align="center">
<img width="750" src="https://github.com/user-attachments/assets/a6da515c-2fd7-4f61-8086-7715af30a6e4">
</p>

# [Snippets](https://github.com/benjamin-dcs/home-assistant/tree/main/snippets)
## [Error Handling for a Wait For Trigger Action](snippets/error_handling_wait_for_trigger.yaml)
Snippet with a success and fail path for a [`wait for trigger`](https://www.home-assistant.io/docs/scripts/#wait-for-a-trigger) action

# Support
<a href="https://www.buymeacoffee.com/benjamindcs" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
