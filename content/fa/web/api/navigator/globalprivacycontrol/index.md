---
title: "Navigator: globalPrivacyControl property"
---

---
title: "Navigator: globalPrivacyControl property"
short-title: globalPrivacyControl
slug: Web/API/Navigator/globalPrivacyControl
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.globalPrivacyControl
---

{{APIRef("DOM")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`Navigator.globalPrivacyControl`** تنظیمات [Global Privacy Control](https://globalprivacycontrol.org/) کاربر را برای وب‌سایت فعلی برمی‌گرداند.
این تنظیم نشان می‌دهد که آیا کاربر با فروش یا به اشتراک‌گذاری اطلاعات شخصی خود با اشخاص ثالث توسط وب‌سایت یا سرویس موافقت دارد یا خیر.

مقدار این ویژگی منعکس‌کنندهٔ هدر HTTP {{httpheader("Sec-GPC")}} است.

## مقدار

`true` اگر کاربر به صراحت رضایت خود را برای فروش یا به اشتراک‌گذاری داده‌هایش _ندهد_.
`false` اگر کاربر رضایت داده باشد، یا ترجیحی مشخص نکرده باشد.

## مثال

```js
console.log(navigator.globalPrivacyControl);
// "true" if the user has specifically indicated they do not want their data shared or sold, otherwise "false".
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTTPHeader("Sec-GPC")}} هدر
- [GlobalPrivacyControl.org](https://globalprivacycontrol.org/)
- [Do Not Track](https://en.wikipedia.org/wiki/Do_Not_Track) در ویکی‌پدیا