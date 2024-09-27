In this repository I provide Automations, Scripts and other files for Home Assistant.

# [Automations](https://github.com/benjamin-dcs/home-assistant/blob/main/automations/)
## [Birthday Notifier](https://github.com/benjamin-dcs/home-assistant/blob/main/automations/birthday_notifier.yaml)
Uses a Home Assistant calender to send several notifications for someone's birthday. Calendar events are expected to be in one of the following two formats:
- \<Name\>
- \<Name\> (YYYY)

When using the second format, the age is calculated and included in the notification. 
- Sends a notification at 12:00 **_2 days_** prior to the birthday
- Sends a notification at 12:00 **_1 day_** prior to the birthday
- Sends a notification **_every hour_**, starting at day of birth until the notification is _Marked as done_ (You have send a celebration message to the person 🎉).

**Dependencies**:
- Uses the [`Notify Me`](https://github.com/benjamin-dcs/home-assistant/blob/main/scripts/notify_me.yaml) Script to send the notifications
- Uses the [`Notification Action Handler`](https://github.com/benjamin-dcs/home-assistant/blob/main/automations/notification_action_handler.yaml) Automation to handle the _'Mark as done'_ action

## [Notification Action Handler](https://github.com/benjamin-dcs/home-assistant/blob/main/automations/notification_action_handler.yaml)
Generic Automation to handle all my [Actionable Notifications](https://companion.home-assistant.io/docs/notifications/actionable-notifications/).

# [Scripts](https://github.com/benjamin-dcs/home-assistant/tree/main/scripts)
## [Notify Me](https://github.com/benjamin-dcs/home-assistant/blob/main/scripts/notify_me.yaml)
Provides a user friendly (visual editor) interface to send a notification to one or multiple notification providers, including Home Assistant Persistent Notifications.

**Features**:
- (Multi-)Selector for Notification Service(s)
- Templatable message field
- Templatable title field
- Data object
- Templatable url field

<img width="796" alt="image" src="https://github.com/user-attachments/assets/458e13b0-0e6a-4e47-950f-e82eddf1fa02">

## [Get ChatGPT Response](https://github.com/benjamin-dcs/home-assistant/blob/main/scripts/get_chatgpt_response.yaml)
Provides a user friendly (visual editor) interface to get a ChatGPT response.

**Features**:
- Templatable prompt field
- Selector for language
- Templatable instruction field
- Selector for ChatGPT model. The model(s) should be exactly the same as your OpenAI Conversation entity. For example model `gpt_4o_mini` uses `conversation.gpt_4o_mini` as conversation agent.

<img width="787" alt="image" src="https://github.com/user-attachments/assets/868415f0-914b-4b32-99b1-dd083b9eef78">


## [Set Input Text with ChatGPT](https://github.com/benjamin-dcs/home-assistant/blob/main/scripts/set_input_text_with_chatgpt.yaml)
...


<a href="https://www.buymeacoffee.com/benjamindcs" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
