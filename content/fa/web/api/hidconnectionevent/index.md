---
title: "HIDConnectionEvent"
---

---
title: HIDConnectionEvent
slug: Web/API/HIDConnectionEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.HIDConnectionEvent
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

رابط **`HIDConnectionEvent`** در [WebHID API](/en-US/docs/Web/API/WebHID_API) رویدادهای اتصال HID را نشان می‌دهد و نوع رویدادی است که هنگام تغییر وضعیت اتصال یک دستگاه، به مدیریت‌کننده‌های رویداد {{domxref("HID/connect_event", "connect")}} و {{domxref("HID/disconnect_event", "disconnect")}} ارسال می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("HIDConnectionEvent.HIDConnectionEvent", "HIDConnectionEvent()")}} {{Experimental_Inline}}
  - : یک شیء `HIDConnectionEvent` جدید بازمی‌گرداند. معمولاً از این سازنده استفاده نمی‌شود؛ زیرا رویدادها هنگام تغییر وضعیت اتصال دستگاه ایجاد می‌شوند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("Event")}} به ارث می‌برد._

- {{domxref("HIDConnectionEvent.device")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نمونه {{domxref("HIDDevice")}} دستگاه مرتبط با رویداد اتصال را بازمی‌گرداند.

## مثال‌ها

مثال زیر شنونده‌های رویدادهای `connect` و `disconnect` را ثبت می‌کند و سپس {{domxref("HIDDevice.productName")}} را در کنسول چاپ می‌کند.

```js
navigator.hid.addEventListener("connect", ({ device }) => {
  console.log(`HID connected: ${device.productName}`);
});

navigator.hid.addEventListener("disconnect", ({ device }) => {
  console.log(`HID disconnected: ${device.productName}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}