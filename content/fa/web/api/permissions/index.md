---
title: Permissions
slug: Web/API/Permissions
page-type: web-api-interface
browser-compat: api.Permissions
---

{{APIRef("Permissions API")}}{{AvailableInWorkers}}

رابط **`Permissions`** در [Permissions API](/en-US/docs/Web/API/Permissions_API) قابلیت‌های اصلی این API را فراهم می‌کند؛ مانند متدهایی برای پرس‌وجو کردن و لغو مجوزها.

## متدهای نمونه

- {{domxref("Permissions.query","Permissions.query()")}}
  - : وضعیت مجوز کاربر را برای یک API مشخص برمی‌گرداند.
- {{domxref("Permissions.revoke","Permissions.revoke()")}} {{Deprecated_Inline}}
  - : مجوزی را که در حال حاضر برای یک API مشخص تنظیم شده است لغو می‌کند.

## مثال

```js
navigator.permissions.query({ name: "geolocation" }).then((result) => {
  if (result.state === "granted") {
    showLocalNewsWithGeolocation();
  } else if (result.state === "prompt") {
    showButtonToEnableLocalNews();
  }
  // Don't do anything if the permission was denied.
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}