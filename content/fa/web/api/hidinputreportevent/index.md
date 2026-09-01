---
title: HIDInputReportEvent
slug: Web/API/HIDInputReportEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.HIDInputReportEvent
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

رابط **`HIDInputReportEvent`** از [WebHID API](/en-US/docs/Web/API/WebHID_API) به رویداد {{domxref("HIDDevice.inputreport_event", "inputreport")}} از `HIDDevice` ارسال می‌شود زمانی که یک گزارش ورودی از هر دستگاه HID مرتبط دریافت می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("Event")}} به ارث می‌برد._

- {{domxref("HIDInputReportEvent.data")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{jsxref("DataView")}} که داده‌های گزارش ورودی را شامل می‌شود، به جز `reportId` اگر رابط HID از شناسه‌های گزارش استفاده کند.
- {{domxref("HIDInputReportEvent.device")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نمونه {{domxref("HIDDevice")}} که نشان‌دهنده رابط HID است که گزارش ورودی را ارسال کرده است.
- {{domxref("HIDInputReportEvent.reportId")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : پیشوند شناسایی یک‌بایتی برای این گزارش، یا 0 اگر رابط HID از شناسه‌های گزارش استفاده نکند.

## روش‌های نمونه

_این رابط روش‌هایی را از والد خود، {{domxref("Event")}} به ارث می‌برد._

## مثال‌ها

مثال زیر نحوه گوش دادن به یک `inputReport` را نشان می‌دهد که به برنامه امکان می‌دهد تشخیص دهد کدام دکمه روی یک دستگاه Joy-Con Right فشار داده شده است. مثال‌های بیشتر و دموهای زنده را در مقاله [اتصال به دستگاه‌های HID غیرمعمول](https://developer.chrome.com/docs/capabilities/hid) مشاهده کنید.

```js
device.addEventListener("inputreport", (event) => {
  const { data, device, reportId } = event;

  // Handle only the Joy-Con Right device and a specific report ID.
  if (device.productId !== 0x2007 && reportId !== 0x3f) return;

  const value = data.getUint8(0);
  if (value === 0) return;

  const someButtons = { 1: "A", 2: "X", 4: "B", 8: "Y" };
  console.log(`User pressed button ${someButtons[value]}.`);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}