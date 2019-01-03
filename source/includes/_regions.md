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

blah blah blah

| Countries and Regions | Regex                                                                               | Sample |
| --------------------- | ----------------------------------------------------------------------------------- | ------ |
| 🇭🇰 Hong Kong          | `/^((?!999)([23456789]{1}[0-9]{7}))$/`                                              |        |
| 🇲🇾 Malaysia           | <code>/^0(1[1,5]?\\d{8}&#124;[4-7,9]\\d{7}&#124;8[2-9]\\d{6}&#124;3\\d{8})$/</code> |        |
| 🇵🇭 Philippines        | <code>/^09[0-9]{9}$&#124;^0?2[0-9]{7}$&#124;^0?32[0-9]{7}$/</code>                  |        |
| 🇸🇬 Singapore          | `/^[689]{1}[0-9]{7}$/`                                                              |        |
| 🇹🇭 Thailand           | `/^0[0-9]{8,9}$/`                                                                   |        |
| 🇹🇼 Taiwan             | <code>/^0([1-8]{1}[0-9]{7,8}&#124;9[0-9]{8})$/</code>                               |        |
| 🇻🇳 Viet Nam           | <code>/^0?(1[2689]&#124;2&#124;[35789])[0-9]{8}$&#124;^028[0-9]{8}$/</code>         |        |
