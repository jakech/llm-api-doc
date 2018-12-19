---
title: Lalamove API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

The lalamove API lets you integrate your application and business with express delivery, including following end points for our client to use.

**APIPurpose**1QuotationAllow the user to get quotation of an order, delivery with multiple stops and schedule order of a specific time2Place orderAllow the user to place an order with a defined value from our quotation API3Get order detailsAllow the user to retrieve the order information4Get order's driver informationAllow the user to retrieve the driver information of an order5Get order's driver locationAllow the user to retrieve the driver latest location6Cancel orderAllow the user to cancel the order before the driver is matched and less than 3 mins after driver is matched. (cannot cancel after driver has arrived first stop)

# Authentication

Lalamove API makes use of [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code) (SHA256) as the authentication mechanism.

Customers will be provided with a api key(a fixed unique identifier given by lalamove representing the customer identity), and a secret for generating [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code) hash (also known as a signature).

Every call **MUST** include this header.

`Authorization: hmac <KEY>:<TIMESTAMP>:<SIGNATURE>`

<aside class="notice">
You must replace <code>&lt;KEY&gt;</code>, <code>&lt;TIMESTAMP&gt;</code> and <code>&lt;SIGNATURE&gt;</code> with the following...
</aside>

|               |        |
| ------------- | ------ |
| `<KEY>`       | lalala |
| `<TIMESTAMP>` | lalala |
| `<SIGNATURE>` | lalala |

# Get a quotation

```
POST https://rest.lalamove.com/v2/quotations
```

> Headers

```
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <UUID>
```

> Body

```json
{
  "scheduleAt": "2018-12-19T14:30:00.00Z",
  "serviceType": "VAN",
  "stops": [...],
  "deliveries": [...],
  "requesterContact": { "name": "Peter Pan", "phone": "81700091" },
  "specialRequests": ["COD", "HELP_BUY", "LALABAG"],
  "promoCode": "BLAH"
}
```

> Responses: `200`

```json
{
  "totalFee": "67",
  "totalFeeCurrency": "SGD"
}
```

Request a quotation.

Will return a with an object containing the fee amount and currency of based on information provided.

`POST` `/v2/quotations`

**Body**

✅ - _Required_

|                    |     |                  |                                                                                                                                  |
| ------------------ | --- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `scheduleAt`       | ✅  | `string`         | Pick up time in **UTC** time zone. In **ISO RFC3339** format                                                                     |
| `serviceType`      | ✅  | `string`         | `MOTORCYCLE`- **50 × 50 × 50 cm** or less <br>`MPV` - **115 × 115 × 80 cm** or less <br> `TRUCK`- **170 × 150 × 170 cm** or less |
| `stops`            | ✅  | `Waypoint[]`     | Array of [`Waypoint`](#waypoint) (minimum 2, maximum 10)                                                                         |
| `deliveries`       | ✅  | `DeliveryInfo[]` | Array of [`DeliveryInfo`](#deliveryinfo) like contact person, mobile phone number and remarks for each item                      |
| `requesterContact` | ✅  | `Contact`        | Person of contact at _pick up point_ aka `stop[0]`, see [`Contact`](#contact)                                                    |  |
| `specialRequests`  |     | `string[]`       | blah blah blah                                                                                                                   |
| `promoCode`        |     | `string`         | blah blah blah                                                                                                                   |

## Waypoint

> **Waypoint**
> talk about **Waypoint**

```json
{
  "location": { "lat": "13.740167", "lng": "100.535237" },
  "addresses": {
    "th_TH": {
      "displayString": "Siam Pathum Wan, Bangkok",
      "country": "TH"
    }
  }
}
```

hahblah blah

## DeliveryInfo

> **DeliveryInfo**

> hahahaha **DeliveryInfo**

```json
{
  "toStop": 1,
  "toContact": <Contact>
}
```

hahblah blah

## Contact

> **Contact**

> hahahaha **Contact**

```json
{ "name": "mm", "phone": "9999999" }
```

hahblah blah

# Place an order

```
POST https://rest.lalamove.com/v2/orders
```

> Headers

```
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <UUID>
```

> Body

```json
{
  "scheduleAt": "2018-12-19T14:30:00.00Z",
  "serviceType": "VAN",
  "stops": [...],
  "deliveries": [...],
  "requesterContact": { "name": "Peter Pan", "phone": "81700091" },
  "specialRequests": ["COD", "HELP_BUY", "LALABAG"],
  "promoCode": "BLAH"
}
```

> Responses: `200`

```json
{
  "totalFee": "67",
  "totalFeeCurrency": "SGD"
}
```

`POST` `/v2/orders`



