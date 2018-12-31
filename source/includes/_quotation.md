# Get a quotation

```plaintext--prod
POST https://rest.lalamove.com/v2/quotations
```

```plaintext--sandbox
POST https://sandbox-rest.lalamove.com/v2/quotations
```

> Body

```json
{
  "scheduleAt": "2018-12-19T14:30:00.00Z",
  "serviceType": "MOTORCYCLE",
  "stops": [<Waypoint>],
  "deliveries": [<DeliveryInfo>],
  "requesterContact": <Contact>,
  "specialRequests": ["COD", "HELP_BUY", "LALABAG"]
}
```

> **Responses**

> `201`
> Quotation Created

```json
{ "totalFee": "67", "totalFeeCurrency": "THB" }
```

> `409`
> Stops and Deliveries mismatch, [see DeliveryInfo](#get-a-quotation-deliveryinfo)

```json
{ "message": "ERR_DELIVERY_MISMATCH" }
```

> `409`
> Not enough stops, number of stops should be between 2 and 10

```json
{ "message": "ERR_INSUFFICIENT_STOPS" }
```

> `409`
> Reached maximum stops, Number of stops should be between 2 and 10

```json
{ "message": "ERR_TOO_MANY_STOPS" }
```

> `409`
> Invalid payment method _when would this happen?_

```json
{ "message": "ERR_INVALID_PAYMENT_METHOD" }
```

> `409`
> Invalid locale, refer to [Waypoint](#get-a-quotation-waypoint)

```json
{ "message": "ERR_INVALID_LOCALE" }
```

> `409`
> Invalid phone number, refer to [Phone validations](#available-countries-phone-validations)

```json
{ "message": "ERR_INVALID_PHONE_NUMBER" }
```

> `409` `scheduleAt` datetime is in the past

> <aside class="warning">Be reminded that <code>scheduleAt</code> is in <b>UTC</b> timezone.</aside>

```json
{ "message": "ERR_INVALID_SCHEDULE_TIME" }
```

> `409`
> No such service type, make sure to stick to [Service types in your country/region](#service-types)

```json
{ "message": "ERR_INVALID_SERVICE_TYPE" }
```

> `409`
> No such special request(s), make sure that special requests match with selected [Service types](#service-types)

```json
{ "message": "ERR_INVALID_SPECIAL_REQUEST" }
```

> `409`
> Out of service area

```json
{ "message": "ERR_OUT_OF_SERVICE_AREA" }
```

> `409`
> Fail to reverse from address to location, provide `lat` and `lng`

```json
{ "message": "ERR_REVERSE_GEOCODE_FAILURE" }
```

`POST` `/v2/quotations`

Request a quotation.

Will return a with an object containing the fee amount and currency of based on information provided.

<aside class="warning"><b>IMPORTANT:</b> <code>scheduleAt</code> is in <b>UTC</b> timezone.</aside>

<script src="//cdnjs.cloudflare.com/ajax/libs/moment.js/2.23.0/moment.min.js"></script>

<script>
  (function() {
    window.now = moment()
  })()
</script>

<table>
  <thead>
    <tr>
      <th>Your local time</th>
      <th>UTC time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><script>document.write(now.toISOString(true))</script></td>
      <td><script>document.write(now.toISOString())</script></td>
    </tr>
  <tbody>
</table>

* [**ISO 8601**](https://en.wikipedia.org/wiki/ISO_8601) format

<aside class="warning">
The pick up location's (first stop) <code>DeliveryInfo</code> is <b>ALWAYS</b> tided to <code>requesterContact</code>.
</aside>

**Body**

|                    |     |                  |                                                                                                    |
| ------------------ | --- | ---------------- | -------------------------------------------------------------------------------------------------- |
| `scheduleAt`       |     | `string`         | Pick up time in **UTC** timezone and [**ISO 8601**](https://en.wikipedia.org/wiki/ISO_8601) format |
| `serviceType`      |     | `string`         | The type of vechicle. [See available service types](#service-types) in your country/region         |
| `stops`            |     | `Waypoint[]`     | Array of [`Waypoint`](#waypoint)s (minimum 2, maximum 10)                                          |
| `deliveries`       |     | `DeliveryInfo[]` | Array of [`DeliveryInfo`](#deliveryinfo)s                                                          |
| `requesterContact` |     | `Contact`        | Person of contact at _pick up point_ aka `stop[0]`, see [`Contact`](#get-a-quotation-contact)      |  |
| `specialRequests`  | 🤷‍♀️  | `string[]`       | [See available special requests](#service-types) in your country/region                            |

🤷‍♀️ - _Optional_

## Waypoint

> **Waypoint**

```json
{
  "location": { "lat": "13.740167", "lng": "100.535237" },
  "addresses": {
    "th_TH": {
      "displayString": "444 ถนน พญาไท แขวง วังใหม่ เขต ปทุมวัน กรุงเทพมหานคร 10330 ประเทศไทย",
      "country": "TH"
    }
  }
}
```

`LOCALE` is composed of [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) language code and [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code as follow:

`{ISO 639-1}_{ISO 3166-1 alpha-2}`.

[See what locale keys are available in your country/region](#available-countries)

|                                     |          |                                                                                                                           |
| ----------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------- |
| `location.lat`                      | `string` | Latitude                                                                                                                  |
| `location.lng`                      | `string` | Longitude                                                                                                                 |
| `addresses[<LOCALE>].displayString` | `string` | Street address in plain text. Use `remarks` in [DeliveryInfo](#get-a-quotation-deliveryinfo) for building, floor and flat (**Need to check usage**) |
| `addresses[<LOCALE>].country`       | `string` | [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2). [See Available countries](#available-countries)   |

## DeliveryInfo

> **DeliveryInfo**

```json
{
  "toStop": 1,
  "toContact": <Contact>
  "remarks": "บทที่ 34 ชั้น 4 อาคารเอบีซี"
}
```

Contact person, mobile phone number and remarks for each [Waypoint](#get-a-quotation-waypoint) excluding the pick up point.

|             |     |           |                                                                                                                                                            |
| ----------- | --- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `toStop`    |     | `number`  | The index of waypoint in `stops` this information associates with, has to be `>= 1`, since the first stop's Delivery Info is tided to `requesterContact` |
| `toContact` |     | `Contact` | See [`Contact`](#get-a-quotation-contact)                                                                                                                  |
| `remarks`   | 🤷‍♀️  | `string`  | Additional info about the delivery. eg. building, floor and flat                                                                                           |

🤷‍♀️ - _Optional_

## Contact

> **Contact**

```json
{ "name": "Donald Trump", "phone": "+668912121212" }
```

|         |          |                                                                                                                     |
| ------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| `name`  | `string` | The name of the person of contact                                                                                   |
| `phone` | `string` | Must be a valid phone number. [See how we validate](#available-countries-phone-validations) for each country/region |
