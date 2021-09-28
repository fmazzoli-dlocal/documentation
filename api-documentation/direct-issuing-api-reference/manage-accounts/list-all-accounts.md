---
description: Learn how to create a list of Issuing Accounts.
---

# List all the accounts

The list of objects is sorted in descending order by creation date, with the most recently created object appearing first.

{% api-method method="get" host="https://issuing-api.dlocal.com" path="/issuing/accounts" %}
{% api-method-summary %}
List all the accounts
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page\_size" type="integer" required=false %}
Limit of accounts to retrieve. Default is 100 and max is 500.
{% endapi-method-parameter %}

{% api-method-parameter name="page\_number" type="integer" required=false %}
Transaction start. By default 0.
{% endapi-method-parameter %}

{% api-method-parameter name="start\_date" type="string" required=false %}
Accounts created after and equal this date. YYYY-MM-DD
{% endapi-method-parameter %}

{% api-method-parameter name="end\_date" type="string" required=false %}
Accounts created before and equal this date. YYYY-MM-DD
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "content": [
        {
        "description": "dLocal Issuing for John Smith",
        "notification_url": "http://someUrl.com",
        "owner": {
            "first_name": "John",
            "last_names": "Smith",
            "birth_date": "1990-11-05",
            "email": "jsmith@dlocal.com",
            "phone_number": "46043767",
            "document": "6095766098",
            "expedition_date": "2020-11-05",
            "address": {
                "country": "CO",
                "city": "Medellin",
                "state": "Antioquia",
                "street": "Carrera 74 zZmLkR",
                "street2": "Carrera 74 EbXiEI",
                "house_number": "52",
                "zip_code": "05001000",
                "neighbourhood": "El Poblado"
            },
            "marital_status": "S",
            "gender": "M",
            "birth_place": "Colombia",
            "nationality": "Colombian",
            "document_type": "CC",
            "mother_name": "Perez",    
            "terms_and_conditions_accepted": true,
            "data_management_accepted": true
            "ip_address": "194.248.71.175"
        },
        "account_uid": "ISGA-33-15dab5f508aa47cabb3d53853e224fa1",
        "account_id": "ISGA-33-15dab5f508aa47cabb3d53853e224fa1",
        "country": "CO",
        "currency": "COP",
        "status": "ACTIVE",
        "status_code": "ACTIVE",
        "status_detail": "Is Active",
        "creation_date": "2021-06-07T19:10:25Z",
        "account_reference": "Dneq12L2bp",
        "cards": [
            {
                "card_id": "ISGC-1234-af4768bcee874a2ea34562f50e0be940",
                "type": "PHYSICAL",
                "created_at": "2021-06-16T15:56:01Z"
            }
        ]
    }
        }
    ],
    "pageable": {
        "sort": {
            "sorted": true,
            "unsorted": false,
            "empty": false
        },
        "page_number": 0,
        "page_size": 1,
        "offset": 0,
        "paged": true,
        "unpaged": false
    },
    "last": false,
    "total_elements": 10415,
    "total_pages": 10415,
    "sort": {
        "sorted": true,
        "unsorted": false,
        "empty": false
    },
    "first": true,
    "number_of_elements": 1,
    "size": 1,
    "number": 0,
    "empty": false
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

