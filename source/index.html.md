---
title: Lalamove API Reference

toc_footers:
  - <a href='#api-access'>Sign Up for Developer Keys</a>

language_tabs:
  - plaintext--sandbox: Sandbox
  - plaintext--prod: Production

includes:
  - auth
  - quotation
  - place-order
  - get-order
  - cancel-order
  - services
  - errors
  - regions
  - form

search: true
---

# Introduction

The lalamove API lets you integrate your application and business with express delivery, including following end points for our client to use.

**APIPurpose**1QuotationAllow the user to get quotation of an order, delivery with multiple stops and schedule order of a specific time2Place orderAllow the user to place an order with a defined value from our quotation API3Get order detailsAllow the user to retrieve the order information4Get order's driver informationAllow the user to retrieve the driver information of an order5Get order's driver locationAllow the user to retrieve the driver latest location6Cancel orderAllow the user to cancel the order before the driver is matched and less than 3 mins after driver is matched. (cannot cancel after driver has arrived first stop)
