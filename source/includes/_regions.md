# Available countries

Lalamove API is currently open for the following countries and regions.

<aside class="success"><a href="#sales">Contact us</a> if you would like to expand your operations to more countries and regions.</aside>

| Countries and Regions | ISO 3166-1 alpha-2 | Locale keys      |
| --------------------- | ------------------ | ---------------- |
| 🇭🇰 Hong Kong          | `HK`               | `en_HK`, `zh_HK` |
| 🇲🇾 Malaysia           | `MY`               | `en_MY`, `ms_MY` |
| 🇵🇭 Philippines        | `PH`               | `en_PH`          |
| 🇸🇬 Singapore          | `SG`               | `en_SG`          |
| 🇹🇭 Thailand           | `TH`               | `th_TH`, `en_TH` |
| 🇹🇼 Taiwan             | `TW`               | `zh_TW`          |
| 🇻🇳 Viet Nam           | `VN`               | `en_VN`, `vi_VN` |

## Phone validations

The following table show how phone numbers are validated for each country or region.

<table>
  <thead>
    <tr>
      <th>Countries and Regions</th>
      <th>Sample</th>
      <th>Regex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>🇭🇰 Hong Kong</td>
      <td>51234567</td>
      <td><code>/^((?!999)([2-9][0-9]{7}))$/</code></td>
    </tr>
    <tr>
      <td>🇲🇾 Malaysia</td>
      <td>0376886555</td>
      <td><code>/^0(1[1,5]?\\d{8}|[4-7,9]\\d{7}|8[2-9]\\d{6}|3\\d{8})$/</code></td>
    </tr>
    <tr>
      <td>🇵🇭 Philippines</td>
      <td>09051234567</td>
      <td><code>/^09[0-9]{9}$|^0?2[0-9]{7}$|^0?32[0-9]{7}$/</code></td>
    </tr>
    <tr>
      <td>🇸🇬 Singapore</td>
      <td>81234567</td>
      <td><code>/^[689]{1}[0-9]{7}$/</code></td>
    </tr>
    <tr>
      <td>🇹🇭 Thailand</td>
      <td>0812345678</td>
      <td><code>/^(0[0-9]{8,9}|[0-9]{4})$/</code></td>
    </tr>
    <tr>
      <td>🇹🇼 Taiwan</td>
      <td>0912345678</td>
      <td><code>/^0([1-8]{1}[0-9]{7,8}|9[0-9]{8})$/</code></td>
    </tr>
    <tr>
      <td>🇻🇳 Viet Nam</td>
      <td>912345678</td>
      <td><code>/^0?(2|[35789])[0-9]{8}$|^02[48][0-9]{8}$/</code></td>
    </tr>
  </tbody>
</table>
