---
title: "PermissionStatus"
slug: Web/API/PermissionStatus
page-type: web-api-interface
browser-compat: api.PermissionStatus
---

{{APIRef("Permissions API")}}{{AvailableInWorkers}}

واسط **`PermissionStatus`** در [Permissions API](/en-US/docs/Web/API/Permissions_API) وضعیت یک شیء و یک مدیریت‌کننده رویداد برای پایش تغییرات آن وضعیت را فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("PermissionStatus.name")}} {{ReadOnlyInline}}
  - : نام مجوز درخواست‌شده را برمی‌گرداند؛ همان مقداری که به {{domxref("Permissions.query")}} ارسال شده است.
- {{domxref("PermissionStatus.state")}} {{ReadOnlyInline}}
  - : وضعیت مجوز درخواست‌شده را برمی‌گرداند؛ یکی از `'granted'`، `'denied'` یا `'prompt'`.

### رویدادها

- {{domxref("PermissionStatus.change_event", "change")}}
  - : هنگام تغییر در `PermissionStatus.state` فراخوانی می‌شود.

## مثال

```js
navigator.permissions
  .query({ name: "geolocation" })
  .then((permissionStatus) => {
    console.log(`geolocation permission status is ${permissionStatus.state}`);
    permissionStatus.onchange = () => {
      console.log(
        `geolocation permission status has changed to ${permissionStatus.state}`,
      );
    };
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}