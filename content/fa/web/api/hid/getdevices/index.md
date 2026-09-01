---
title: "HID: getDevices() method"
short-title: getDevices()
slug: Web/API/HID/getDevices
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HID.getDevices
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

متد **`getDevices()`** در رابط {{domxref("HID")}} فهرستی از دستگاه‌های HID متصل را دریافت می‌کند که کاربر قبلاً در پاسخ به فراخوانی {{domxref("HID.requestDevice","requestDevice()")}} به آن‌ها دسترسی داده است.

## نحو (Syntax)

```js-nolint
getDevices()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با فهرستی از اشیاء {{domxref("HIDDevice")}} حل می‌شود.

## مثال‌ها

مثال زیر فهرستی از دستگاه‌ها را دریافت کرده و نام دستگاه‌ها را در کنسول ثبت می‌کند.

```js
let devices = await navigator.hid.getDevices();
devices.forEach((device) => {
  console.log(`HID: ${device.productName}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}