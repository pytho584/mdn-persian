---
title: "HIDDevice: sendFeatureReport() method"
short-title: sendFeatureReport()
slug: Web/API/HIDDevice/sendFeatureReport
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HIDDevice.sendFeatureReport
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

متد **`sendFeatureReport()`** از رابط {{domxref("HIDDevice")}} یک گزارش ویژگی (Feature Report) به دستگاه HID ارسال می‌کند. گزارش‌های ویژگی یکی از روش‌های تبادل داده‌های HID غیراستاندارد بین دستگاه‌های HID و برنامه‌ها هستند.

`reportId` برای هر یک از قالب‌های گزارشی که این دستگاه پشتیبانی می‌کند را می‌توان از {{domxref("HIDDevice.collections")}} دریافت کرد.

## نحو (Syntax)

```js-nolint
sendFeatureReport(reportId, data)
```

### پارامترها

- `reportId`
  - : یک شناسه گزارش ۸ بیتی. اگر دستگاه HID از شناسه گزارش استفاده نمی‌کند، مقدار `0` ارسال کنید.
- `data`
  - : بایت‌ها به صورت یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}} یا یک {{jsxref("DataView")}}.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از ارسال گزارش با `undefined` مقداردهی می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر ارسال گزارش به هر دلیلی ناموفق باشد، این خطا پرتاب می‌شود.

## مثال‌ها

در مثال زیر `sendFeatureReport()` باعث چشمک زدن دستگاه می‌شود. مثال‌های بیشتر و دموهای زنده را در مقاله [اتصال به دستگاه‌های HID غیرمعمول](https://developer.chrome.com/docs/capabilities/hid) می‌توانید ببینید.

```js
const reportId = 1;
for (let i = 0; i < 10; i++) {
  // خاموش
  await device.sendFeatureReport(reportId, Uint32Array.from([0, 0]));
  await new Promise((resolve) => setTimeout(resolve, 100));
  // روشن
  await device.sendFeatureReport(reportId, Uint32Array.from([512, 0]));
  await new Promise((resolve) => setTimeout(resolve, 100));
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}