---
title: "HIDDevice: vendorId property"
---

---
title: "HIDDevice: vendorId property"
short-title: vendorId
slug: Web/API/HIDDevice/vendorId
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDDevice.vendorId
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

ویژگی فقط‌خواندنی **`vendorId`** در رابط {{domxref("HIDDevice")}} شناسه فروشنده (vendor ID) دستگاه HID متصل را بازمی‌گرداند. این مقدار فروشنده دستگاه را مشخص می‌کند.

## Value

یک عدد صحیح (integer). اگر دستگاه شناسه فروشنده نداشته باشد، یا شناسه فروشنده قابل دسترسی نباشد، این ویژگی مقدار `0` را برمی‌گرداند.

## Examples

مثال زیر دستگاه‌ها را با {{domxref("HID.getDevices()")}} دریافت می‌کند و مقدار `vendorId` را در کنسول ثبت می‌کند.

```js
let devices = await navigator.hid.getDevices();
devices.forEach((device) => {
  console.log(`HID: ${device.vendorId}`);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}