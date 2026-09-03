---
title: "Navigator: permissions property"
short-title: permissions
slug: Web/API/Navigator/permissions
page-type: web-api-instance-property
browser-compat: api.Navigator.permissions
---

{{APIRef("Permissions API")}}

خاصیت فقط خواندنی **`permissions`** در رابط {{domxref("Navigator")}} یک شیء {{domxref("Permissions")}} را برمی‌گرداند که می‌توان از آن برای پرس‌وجو و به‌روزرسانی وضعیت مجوز APIهای تحت پوشش [Permissions API](/en-US/docs/Web/API/Permissions_API) استفاده کرد.

## مقدار

یک شیء {{domxref("Permissions")}}.

## مثال‌ها

```js
navigator.permissions.query({ name: "geolocation" }).then((result) => {
  if (result.state === "granted") {
    showMap();
  } else if (result.state === "prompt") {
    showButtonToEnableMap();
  }
  // Don't do anything if the permission was denied.
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Permissions API](/en-US/docs/Web/API/Permissions_API)
- {{domxref("Navigator")}}