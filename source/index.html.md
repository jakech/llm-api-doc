---
title: Lalamove API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - quotation
  - place-order
  - get-order
  - cancel-order
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




