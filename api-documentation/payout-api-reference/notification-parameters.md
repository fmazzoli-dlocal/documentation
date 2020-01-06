# Notification parameters

Notifications will be sent to your notification URL using the POST protocol whenever there is a payout status change. The following is a list of the parameters included in the notification POST message:

| Field | Format | Description | Example |
| :--- | :--- | :--- | :--- |
| external\_id | String \(max. 100 chars\) | Payout identification \(at the merchant site\) | payout1234 |
| cashout\_id | Number \(max. 10 chars\) | Payout identification \(at dLocal site\) | 10050 |
| date | Format: YYYY-MM-DD HH:MM:SS \(GMT\) | The date when the status changed | 2015-10-03 15:32:01 |
| bank\_reference\_id | String \(max. 50 chars\) | Number reference at the bank | 513512.04198.5 |
| comments | String \(max. 200 chars\) | Payout comment | This is a comment |



