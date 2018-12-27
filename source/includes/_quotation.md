# Get a quotation

```plaintext--prod
POST https://rest.lalamove.com/v2/quotations
```

```plaintext--sandbox
POST https://sandbox-rest.lalamove.com/v2/quotations
```

> Body

```js
{
  "scheduleAt": "2018-12-19T14:30:00.00Z",
  "serviceType": "VAN", // TODO
  "stops": [<Waypoint>],
  "deliveries": [<DeliveryInfo>],
  "requesterContact": <Contact>,
  "specialRequests": ["COD", "HELP_BUY", "LALABAG"], // TODO
  "promoCode": "BLAH"
}
```

> Responses: `201`

```js
{
  "totalFee": "67",
  "totalFeeCurrency": "SGD"
}
```

`POST` `/v2/quotations`

Request a quotation.

Will return a with an object containing the fee amount and currency of based on information provided.

**Body**

|                    |     |                  |                                                                                                                                  |
| ------------------ | --- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `scheduleAt`       |     | `string`         | Pick up time in **UTC** time zone. In **ISO RFC3339** format                                                                     |
| `serviceType`      |     | `string`         | `MOTORCYCLE`- **50 × 50 × 50 cm** or less <br>`MPV` - **115 × 115 × 80 cm** or less <br> `TRUCK`- **170 × 150 × 170 cm** or less |
| `stops`            |     | `Waypoint[]`     | Array of [`Waypoint`](#waypoint)s (minimum 2, maximum 10)                                                                        |
| `deliveries`       |     | `DeliveryInfo[]` | Array of [`DeliveryInfo`](#deliveryinfo)s                                                                                        |
| `requesterContact` |     | `Contact`        | Person of contact at _pick up point_ aka `stop[0]`, see [`Contact`](#get-a-quotation-contact)                                    |  |
| `specialRequests`  | 🤷‍♀️  | `string[]`       | blah blah blah                                                                                                                   |
| `promoCode`        | 🤷‍♀️  | `string`         | blah blah blah                                                                                                                   |

🤷‍♀️ - _Optional_

## Waypoint

> **Waypoint**

```js
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

`LOCALE` is composed of [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) language code and [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code as follow:

`{ISO 639-1}_{ISO 3166-1 alpha-2}`.

|                                     |          |                                                                        |
| ----------------------------------- | -------- | ---------------------------------------------------------------------- |
| `location.lat`                      | `string` |                                                                        |
| `location.lng`                      | `string` |                                                                        |
| `addresses[<LOCALE>].displayString` | `string` | becareful here blah blah blah                                          |
| `addresses[<LOCALE>].country`       | `string` | [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2). [See Available countries](#available-countries) |

## DeliveryInfo

> **DeliveryInfo**

```js
{
  "toStop": 1,
  "toContact": <Contact>
  "remarks": "XXXXX"
}
```

Contact person, mobile phone number and remarks for each [Waypoint](#get-a-quotation-waypoint) excluding the pick up point.

|             |     |           |                                                                                                                                                            |
| ----------- | --- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `toStop`    |     | `number`  | The index of waypoint in `stops` this Delivery Info associates with, has to be `>= 1`, since the first stop's Delivery Info is tided to `requesterContact` |
| `toContact` |     | `Contact` | See [`Contact`](#get-a-quotation-contact)                                                                                                                  |
| `remarks`   | 🤷‍♀️  | `string`  | Free form text the driver would see                                                                                                                        |

🤷‍♀️ - _Optional_

## Contact

> **Contact**

> hahahaha **Contact**

```js
{ "name": "mm", "phone": "9999999" }
```

hahblah blah, talk about phone format etc.

|         |          |     |
| ------- | -------- | --- |
| `name`  | `string` |     |
| `phone` | `string` |     |
