---
title: "HID: connect event"
---

---
title: "HID: connect event"
short-title: connect
slug: Web/API/HID/connect_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.HID.connect_event
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

رویداد **`connect`** از رابط {{domxref("HID")}} زمانی رخ می‌دهد که عامل کاربر به یک دستگاه HID متصل می‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("connect", (event) => { })

onconnect = (event) => { }
```

## نوع رویداد

یک {{domxref("HIDConnectionEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("HIDConnectionEvent")}}

## مثال‌ها

در مثال زیر، یک شنونده رویداد برای گوش دادن به اتصال یک دستگاه ثبت شده است. سپس نام دستگاه با استفاده از {{domxref("HIDDevice.productName")}} در کنسول چاپ می‌شود.

```js
navigator.hid.addEventListener("connect", ({ device }) => {
  console.log(`HID connected: ${device.productName}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}