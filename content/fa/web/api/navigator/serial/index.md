---
title: "Navigator: serial property"
short-title: serial
slug: Web/API/Navigator/serial
page-type: web-api-instance-property
browser-compat: api.Navigator.serial
---

{{APIRef("Web Serial API")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`serial`** در رابط {{domxref("Navigator")}} یک شیء {{domxref("Serial")}} بازمی‌گرداند که نقطهٔ ورود به [Web Serial API](/en-US/docs/Web/API/Web_Serial_API) را نشان می‌دهد.

همواره همان نمونهٔ مشترک از شیء {{domxref("Serial")}} بازگردانده می‌شود.

## مقدار

یک شیء {{domxref("Serial")}}.

## مثال‌ها

### فهرست کردن پورت‌های موجود

مثال زیر از متد `getPorts()` برای مقداردهی اولیهٔ فهرست پورت‌های موجود استفاده می‌کند.

```js
navigator.serial.getPorts().then((ports) => {
  // Initialize the list of available ports with `ports` on page load.
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [خواندن و نوشتن در پورت سریال](https://developer.chrome.com/docs/capabilities/serial)
- [شروع کار با Web Serial API](https://codelabs.developers.google.com/codelabs/web-serial#0)
