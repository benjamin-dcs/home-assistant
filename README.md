In this repository I provide Automations, Scripts and other files for Home Assistant.

# Automations [(click)](https://github.com/benjamin-dcs/home-assistant/blob/main/automations/)
## Birthday Notifier [(click)](https://github.com/benjamin-dcs/home-assistant/blob/main/automations/birthday_notifier.yaml)
Uses a Home Assistant calender to send several notifications for someone's birthday. Calendar events are expected to be in one of the following two formats:
- \<Name\>
- \<Name\> (YYYY)

When using the second format, the age is calculated and included in the notification. 
- Sends a notification at 12:00 **_2 days_** prior to the birthday
- Sends a notification at 12:00 **_1 day_** prior to the birthday
- Sends a notification **_every hour_**, starting at day of birth until the notification is _Marked as done_ (You have send a celebration message to the person 🎉). Uses the `Notification Action Handler` Automation to handle the _'Mark as done'_ action

# Scripts