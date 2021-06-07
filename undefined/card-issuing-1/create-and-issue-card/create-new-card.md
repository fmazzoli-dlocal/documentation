# Create New Card

This function allows to Create and Issue a New Card for an account-owner. The card is associated to the account and all transactions will be reflected on account's balance.

Card schemes are subject to availability.

On response to card creation, you will receive a `card_id`, please store this value as it will be used for transacting.

## Create New Card <a id="create-new-card"></a>

https://sandbox.dlocal.com/issuing/cards

Body Parameters

URL to receive webhook notification on status change

Card reference on merchant side

Required if physical card. If not provided will use same as provided in account creation. See address object specs on Create account-owner section.

Account id to which card is associated

enum\('PHYSICAL','VIRTUAL'\)

```text
{    "account_id": "ISGA-4-9618440e0abe4fcfa77575319e6eb7ec",    "card_reference": "WCaM8vn1YMNJ",    "delivery_address": {        "country": "CO",        "city": "Medellin",        "state": "Antioquia",        "street": "Carrera 74 cYdDao",        "street2": "Carrera 74 biVvwb",        "house_number": "52",        "zip_code": "05001000",        "neighbourhood": "El Poblado"    },    "notification_url": "http://merchant.dlocal.com/notification",    "card_id": "ISGC-4-a635217734a746dd9f3875899492c3aa",    "type": "PHYSICAL",    "status": "PENDING",    "created_at": "2021-03-11T13:46:35.922Z"}
```

## Example Request <a id="example-request"></a>

```text
{    "account_id": "ISGA-4-9618440e0abe4fcfa77575319e6eb7ec",    "type": "PHYSICAL",    "card_reference": "WCaM8vn1YMNJ",    "delivery_address": {        "country": "CO",        "city": "Medellin",        "state": "Antioquia",        "street": "Carrera 74 cYdDao",        "street2": "Carrera 74 biVvwb",        "house_number": "52",        "zip_code": "05001000",        "neighbourhood": "El Poblado"    },    "notification_url": "http://merchant.dlocal.com/notification"}
```

### Asynchronous Notifications <a id="asynchronous-notifications"></a>

When there is a change of status for the card, we will send you a notification to the provided `notification_url` indicating card`_id` . You will need to call [Get Card Information](get-card-information.md#get-card-information) function to review this changes.

```text
{     "card_id":"ISGC-4-a635217734a746dd9f3875899492c3aa",     "account_id": "ISGA-4-9618440e0abe4fcfa77575319e6eb7ec" }
```

### ​ <a id="undefined"></a>

