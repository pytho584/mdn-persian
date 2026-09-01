---
title: "HIDDevice: sendReport() method"
short-title: sendReport()
slug: Web/API/HIDDevice/sendReport
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HIDDevice.sendReport
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

متد **`sendReport()`** از رابط {{domxref("HIDDevice")}} یک گزارش خروجی به دستگاه HID ارسال می‌کند.

مقدار `reportId` برای هر یک از قالب‌های گزارشی که این دستگاه پشتیبانی می‌کند را می‌توانید از {{domxref("HIDDevice.collections")}} دریافت کنید.

## نحو

```js-nolint
sendReport(reportId, data)
```

### پارامترها

- `reportId`
  - : یک شناسهٔ گزارش ۸ بیتی. اگر دستگاه HID از شناسه‌های گزارش استفاده نمی‌کند، مقدار `0` را ارسال کنید.
- `data`
  - : بایت‌ها به‌صورت یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}}.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از ارسال گزارش با مقدار `undefined` حل می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر ارسال گزارش به هر دلیلی ناموفق باشد، پرتاب می‌شود.

## مثال‌ها

مثال زیر نشان می‌دهد که چگونه می‌توانید با استفاده از گزارش‌های خروجی، دستگاه Joy-Con را به لرزش درآورید. می‌توانید مثال‌های بیشتر و دموهای زنده را در مقالهٔ [اتصال به دستگاه‌های HID غیرمعمول](https://developer.chrome.com/docs/capabilities/hid) ببینید.

```js
// First, send a command to enable vibration.
// Magical bytes come from https://github.com/mzyy94/joycon-toolweb
const enableVibrationData = [1, 0, 1, 64, 64, 0, 1, 64, 64, 0x48, 0x01];
await device.sendReport(0x01, new Uint8Array(enableVibrationData));

// Then, send a command to make the Joy-Con device rumble.
// Actual bytes are available in the sample.
const rumbleData = [/* … */];
await device.sendReport(0x10, new Uint8Array(rumbleData));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}