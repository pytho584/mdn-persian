---
title: "HIDDevice: receiveFeatureReport() method"
short-title: receiveFeatureReport()
slug: Web/API/HIDDevice/receiveFeatureReport
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HIDDevice.receiveFeatureReport
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

متد **`receiveFeatureReport()`** از رابط {{domxref("HIDDevice")}} یک گزارش ویژگی (feature report) را از دستگاه HID دریافت می‌کند. گزارش‌های ویژگی راهی برای تبادل داده‌های HID غیراستاندارد بین دستگاه‌های HID و برنامه‌ها هستند.

`reportId` مربوط به هر یک از قالب‌های گزارشی که این دستگاه از آن‌ها پشتیبانی می‌کند، از طریق {{domxref("HIDDevice.collections")}} قابل بازیابی است.

## سینتکس

```js-nolint
receiveFeatureReport(reportId)
```

### پارامترها

- `reportId`
  - : یک شناسهٔ گزارش ۸ بیتی. اگر دستگاه HID از شناسه‌های گزارش استفاده نمی‌کند، مقدار `0` را ارسال کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء {{jsxref("DataView")}} حاوی گزارش ویژگی حل می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورت شکست دریافت گزارش به هر دلیلی، این خطا پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک گزارش از دستگاهی با `reportId` برابر با `1` دریافت می‌شود.

```js
const dataView = await device.receiveFeatureReport(1);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}