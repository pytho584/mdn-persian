---
title: "HID: disconnect event"
---

---
title: "HID: disconnect event"
short-title: disconnect
slug: Web/API/HID/disconnect_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.HID.disconnect_event
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

رویداد **`disconnect`** از رابط {{domxref("HID")}} زمانی رخ می‌دهد که عامل کاربر (user agent) یک دستگاه HID را قطع می‌کند.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) را تنظیم کنید.

```js-nolint
addEventListener("disconnect", (event) => { })

ondisconnect = (event) => { }
```

## نوع رویداد

یک {{domxref("HIDConnectionEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("HIDConnectionEvent")}}

## مثال‌ها

در مثال زیر، یک شنونده رویداد (event listener) برای گوش دادن به قطع اتصال دستگاه ثبت شده است. سپس نام دستگاه با استفاده از {{domxref("HIDDevice.productName")}} در کنسول چاپ می‌شود.

```js
navigator.hid.addEventListener("disconnect", ({ device }) => {
  console.log(`HID disconnected: ${device.productName}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}