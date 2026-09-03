---
title: "PermissionStatus: state property"
short-title: state
slug: Web/API/PermissionStatus/state
page-type: web-api-instance-property
browser-compat: api.PermissionStatus.state
---

{{APIRef("Permissions API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`state`** از رابط {{domxref("PermissionStatus")}}، وضعیت یک مجوز درخواست‌شده را برمی‌گرداند. این ویژگی یکی از مقادیر `'granted'`، `'denied'` یا `'prompt'` را برمی‌گرداند.

## مقدار

- `'granted'`
  - : کاربر، یا عامل کاربر به نمایندگی از کاربر، اجازه صریح برای استفاده از یک [قابلیت قدرتمند](https://w3c.github.io/permissions/#dfn-powerful-feature) را داده است. فراخواننده می‌تواند از آن قابلیت استفاده کند، بدون اینکه الزاماً عامل کاربر از کاربر اجازه بگیرد.
- `'denied'`
  - : کاربر، یا عامل کاربر به نمایندگی از کاربر، دسترسی به این [قابلیت قدرتمند](https://w3c.github.io/permissions/#dfn-powerful-feature) را رد کرده است. فراخواننده نمی‌تواند از آن قابلیت استفاده کند.
- `'prompt'`
  - : کاربر اجازه صریح برای استفاده از قابلیت را نداده است (_یعنی همانند وضعیت «denied» است_). همچنین این به این معناست که اگر یک فراخواننده تلاش کند از قابلیت استفاده کند، عامل کاربر یا از کاربر درخواست اجازه خواهد کرد، یا دسترسی به آن قابلیت رد خواهد شد.

## مثال‌ها

```js
navigator.permissions
  .query({ name: "geolocation" })
  .then((permissionStatus) => {
    console.log(`geolocation permission state is ${permissionStatus.state}`);
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