# Get a quotation

```
POST https://rest.lalamove.com/v2/quotations
```

> Headers

```yaml
Authorization: hmac <TOKEN>
Content-Type: application/json
X-LLM-Country: <YOUR_COUNTRY>
X-Request-ID: <NONCE>
```

> Body

```json
{
  "scheduleAt": "2018-12-19T14:30:00.00Z",
  "serviceType": "VAN",
  "stops": [<Waypoint>],
  "deliveries": [<DeliveryInfo>],
  "requesterContact": <Contact>,
  "specialRequests": ["COD", "HELP_BUY", "LALABAG"], // TODO
  "promoCode": "BLAH"
}
```

> Responses: `201`

```json
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
| `scheduleAt`       | ✅  | `string`         | Pick up time in **UTC** time zone. In **ISO RFC3339** format                                                                     |
| `serviceType`      | ✅  | `string`         | `MOTORCYCLE`- **50 × 50 × 50 cm** or less <br>`MPV` - **115 × 115 × 80 cm** or less <br> `TRUCK`- **170 × 150 × 170 cm** or less |
| `stops`            | ✅  | `Waypoint[]`     | Array of [`Waypoint`](#waypoint) (minimum 2, maximum 10)                                                                         |
| `deliveries`       | ✅  | `DeliveryInfo[]` | Array of [`DeliveryInfo`](#deliveryinfo) like contact person, mobile phone number and remarks for each item                      |
| `requesterContact` | ✅  | `Contact`        | Person of contact at _pick up point_ aka `stop[0]`, see [`Contact`](#contact)                                                    |  |
| `specialRequests`  |     | `string[]`       | blah blah blah                                                                                                                   |
| `promoCode`        |     | `string`         | blah blah blah                                                                                                                   |

✅ - _Required_

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
  "remarks": "XXXXX"
}
```

hahblah blah

## Contact

> **Contact**

> hahahaha **Contact**

```json
{ "name": "mm", "phone": "9999999" }
```

hahblah blah, talk about phone format etc.
