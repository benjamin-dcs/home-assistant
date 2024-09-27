<p align="center">
<img width="750" alt="image" src="https://github.com/user-attachments/assets/e98f26d1-8713-459d-b4c5-a32d22fabdd7">
</p>

<p align="center">
<b>In this repository I provide Automations, Scripts and other files for Home Assistant.</b>
</p>

### Notes
- The code in this repo is often a slightly modified (and untested) version of my personal version. In case of any issues, feel free to create an [issue](https://github.com/benjamin-dcs/home-assistant/issues)
- As I am Dutch, some files will contain Dutch text. My guess is that most of you should be able to find your way to Google Translate ;)

# Table of Contents
- [Automations](#automations)
  - [Birthday Notifier](#birthday-notifier)
  - [Notification Action Handler](#notification-action-handler)
  - [Purge Entities](#purge-entities)
- [Scripts](#scripts)
  - [Notify Me](#notify-me)
  - [Get ChatGPT Response](#get-chatgpt-response)
  - [Set Input Text with ChatGPT](#set-input-text-with-chatgpt)
- [Snippets](#snippets)
  - [Error Handling for a Wait For Trigger Action](#error-handling-for-a-wait-for-trigger-action)
- [Dashboard cards](#dashboard-cards)
  - [Button Card Header Button](#button-card-header-button)
  - [Afvalwijzer Card](#afvalwijzer-card)
  - [Compact Energy Card](#compact-energy-card)
- [Todo / On Request](#todo--on-request)
  - [Thermostat controller and card](#thermostat-controller-and-card)
  - [OpenSprinkler dashboard and automation](#opensprinkler-dashboard-and-automation)

# [Automations](automations)
### [Birthday Notifier](automations/birthday_notifier.yaml)
Uses a Home Assistant calender to send several notifications for someone's birthday. For Calendar events ending with `(YYYY)` (including the brackets) the age is calculated and added to the notification.

**Features:**
- Sends a notification at 12:00 **_2 days_** prior to the birthday
- Sends a notification at 12:00 **_1 day_** prior to the birthday
- Sends a notification **_every hour_**, starting at day of birth until the notification is _Marked as done_ (You have send a celebration message to the person 🎉).

**Requirements:**
- Switch Helper: input_boolean.birthday_celebration_sent

**Dependencies:**
- Uses the [`Notify Me`](scripts/notify_me.yaml) Script to send the notifications
- Uses the [`Notification Action Handler`](automations/notification_action_handler.yaml) Automation to handle the _'Mark as done'_ action

### [Notification Action Handler](automations/notification_action_handler.yaml)
Generic Automation to handle all my [Actionable Notifications](https://companion.home-assistant.io/docs/notifications/actionable-notifications/).

### [Purge Entities](automations/purge_entities.yaml)
Simple automation to purge entites after 1, 3 or 7 days.

**Tip!** Use a tool like [DbStats](https://github.com/jehy/hass-addons/tree/master/dbstats) to analyse your Home Assistant Database. Use the automation for entities that use a lot of disc-space to keep your database as small as possible.

# [Scripts](scripts)
### [Notify Me](scripts/notify_me.yaml)
Provides a user friendly (visual editor) interface to send a notification to one or multiple notification providers, including Home Assistant Persistent Notifications.

**Features:**
- (Multi-)Selector for Notification Service(s)
- Templatable message field
- Templatable title field
- Data object
- Templatable url field

**Screenshot:**
<p><img width="750" alt="image" src="https://github.com/user-attachments/assets/924f8dee-e131-4752-9274-81cb048f8a48"></p>

### [Get ChatGPT Response](scripts/get_chatgpt_response.yaml)
Provides a user friendly (visual editor) interface to get a ChatGPT response.

**Features:**
- Templatable prompt field
- Selector for language
- Templatable instruction field
- Selector for ChatGPT model. The model(s) should be exactly the same as your OpenAI Conversation entity. For example model `gpt_4o_mini` uses `conversation.gpt_4o_mini` as conversation agent.

**Screenshot:**
<p><img width="750" src="https://github.com/user-attachments/assets/4fdc4578-1b34-4e14-addf-e1880ea3647e"></p>

### [Set Input Text with ChatGPT](scripts/set_input_text_with_chatgpt.yaml)
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

**Screenshot:**
<p><img width="750" src="https://github.com/user-attachments/assets/a6da515c-2fd7-4f61-8086-7715af30a6e4"></p>

# [Snippets](snippets)
### [Error Handling for a Wait For Trigger Action](snippets/error_handling_wait_for_trigger.yaml)
Snippet with a success and fail path for a [`wait for trigger`](https://www.home-assistant.io/docs/scripts/#wait-for-a-trigger) action

# [Dashboard cards](dashboard)
### [Button Card Header Button](dashboard/button_card_header_button.yaml)
![image](https://github.com/user-attachments/assets/8aca0570-061b-4697-9616-301440979fca)

### [Afvalwijzer Card](dashboard/afvalwijzer.yaml)
![image](https://github.com/user-attachments/assets/8d2c2876-0fc4-4e7d-aae4-191008842019)

### [Compact Energy Card](dashboard/compact_energy_card.yaml)
Probably requires some tweaking of the `grid-template-columns` percentages in order to get right on your own dashboard/screen

<img width="391" alt="image" src="https://github.com/user-attachments/assets/641fd45f-cee0-47a9-a017-63002e0676e2">

# Todo / On Request
### Thermostat controller and card
**Screenshot:**
<p><img width="389" alt="image" src="https://github.com/user-attachments/assets/b6ef98f8-28f1-4c08-af6f-ce7df4127bf0"></p>

**Features:**
- Day / Night settings:
  - Temperature
  - Time
  - Enabled / Enabled once / Disabled once / Disabled
  - Staged heating (-1° -> 0.5° -> <Setting>) _(optional)_
  - Staged cooling (Turn down temp 0.5° <delta> time before night-setting) _(optional)_ 

### OpenSprinkler dashboard and automation
<p><img width="1199" alt="image" src="https://github.com/user-attachments/assets/674095f0-da78-4cb3-ad74-beb90fff717e"></p>

**Features:**
- 2 programs to configure (Uses two valves for my 'grass'-zone. Other zones have one valve)
- Dashboard card to view upcoming zones/times
- Notifications when starting/switching/finishing
- Track water used

# Support
<a href="https://www.buymeacoffee.com/benjamindcs" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
