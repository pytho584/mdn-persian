---
title: "HIDDevice: opened property"
---

---
title: "HIDDevice: opened property"
short-title: opened
slug: Web/API/HIDDevice/opened
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDDevice.opened
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

خصوصیت فقطخواندنی **`opened`** در رابط {{domxref("HIDDevice")}} در صورتی که اتصال به {{domxref("HIDDevice")}} باز و برای انتقال داده آماده باشد، مقدار `true` را بازمیگرداند.

## مقدار

یک مقدار بولین (Boolean)؛ اگر اتصال باز باشد، این مقدار `true` است.

## مثالها

مثال زیر دستگاهها را با استفاده از {{domxref("HID.getDevices()")}} دریافت میکند و مقدار `opened` را در کنسول ثبت میکند.

```js
let devices = await navigator.hid.getDevices();
devices.forEach((device) => {
  console.log(`HID: ${device.opened}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}