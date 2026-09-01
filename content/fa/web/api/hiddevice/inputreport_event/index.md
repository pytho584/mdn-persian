---
title: "HIDDevice: inputreport event"
short-title: inputreport
slug: Web/API/HIDDevice/inputreport_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.HIDDevice.inputreport_event
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

رویداد **`inputreport`** از رابط {{domxref("HIDDevice")}} زمانی رخ می‌دهد که یک گزارش جدید از دستگاه HID دریافت شود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("inputreport", (event) => { })

oninputreport = (event) => { }
```

## نوع رویداد

یک {{domxref("HIDInputReportEvent")}}. به ارث‌برده از {{domxref("Event")}}.

{{InheritanceDiagram("HIDInputReportEvent")}}

## مثال

مثال زیر گوش دادن به رویداد `inputreport` را نشان می‌دهد که به برنامه اجازه می‌دهد تشخیص دهد کدام دکمه روی دستگاه Joy-Con Right فشرده شده است. نمونه‌های بیشتر و نسخه‌های نمایشی زنده را در مقاله [اتصال به دستگاه‌های HID غیرمعمول](https://developer.chrome.com/docs/capabilities/hid) می‌توانید ببینید.

```js
device.addEventListener("inputreport", (event) => {
  const { data, device, reportId } = event;

  // فقط دستگاه Joy-Con Right و یک شناسه گزارش خاص را پردازش کن.
  if (device.productId !== 0x2007 && reportId !== 0x3f) return;

  const value = data.getUint8(0);
  if (value === 0) return;

  const someButtons = { 1: "A", 2: "X", 4: "B", 8: "Y" };
  console.log(`User pressed button ${someButtons[value]}.`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}