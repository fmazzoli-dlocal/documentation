# Notification parameters

The notification will inform that the status of a payout has changed. After that, you will need to ask the new status of the payout. Notification will be sent to the merchant notification URL by POST protocol, with the following parameters:

| Field | Format | Description | Example |
| :--- | :--- | :--- | :--- |
| external\_id | String \(max. 100 chars\) | Payout identification \(at the merchant site\) | payout1234 |
| cashout\_id | Number \(max. 10 chars\) | Payout identification \(at dLocal site\) | 10050 |
| date | Format: YYYY-MM-DD HH:MM:SS \(GMT\) | The date when the status changed | 2015-10-03 15:32:01 |
| bank\_reference\_id | String \(max. 50 chars\) | Number reference at the bank | 513512.04198.5 |
| comments | String \(max. 200 chars\) | Payout comment | This is a comment |



