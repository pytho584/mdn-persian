---
title: "Navigator: contacts property"
short-title: contacts
slug: Web/API/Navigator/contacts
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.contacts
---

{{APIRef("Contact Picker API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`contacts`** در رابط {{domxref("Navigator")}} یک رابط {{domxref('ContactsManager')}} برمی‌گرداند که به کاربران امکان می‌دهد ورودی‌هایی را از فهرست مخاطبان خود انتخاب کنند و جزئیات محدودی از ورودی‌های انتخاب‌شده را با یک وب‌سایت یا برنامه به اشتراک بگذارند.

## مقدار

یک شیء {{domxref('ContactsManager')}}. دو فراخوانی متوالی همان شیء را برمی‌گردانند.

## مثال‌ها

کد زیر بررسی می‌کند که آیا Contact Picker API پشتیبانی می‌شود یا نه.

```js
const supported = "contacts" in navigator && "ContactsManager" in window;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [A Contact Picker for the Web](https://developer.chrome.com/docs/capabilities/web-apis/contact-picker)
- [Contact Picker API live demo](https://mdn.github.io/dom-examples/contact-picker/)