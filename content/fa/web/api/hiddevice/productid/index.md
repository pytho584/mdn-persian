---
title: "HIDDevice: productId property"
short-title: productId
slug: Web/API/HIDDevice/productId
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDDevice.productId
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

ویژگی فقط‌خواندنی **`productId`** در رابط {{domxref("HIDDevice")}}، شناسه محصول دستگاه HID متصل را برمی‌گرداند.

## مقدار

یک عدد صحیح. اگر دستگاه شناسه محصول نداشته باشد یا شناسه محصول قابل دسترسی نباشد، این ویژگی مقدار `0` برمی‌گرداند.

## مثال‌ها

مثال زیر دستگاه‌ها را با {{domxref("HID.getDevices()")}} بازیابی می‌کند و مقدار `productId` را در کنسول ثبت می‌کند.

```js
let devices = await navigator.hid.getDevices();
devices.forEach((device) => {
  console.log(`HID: ${device.productId}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}