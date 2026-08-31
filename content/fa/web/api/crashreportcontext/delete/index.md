---
title: "CrashReportContext: delete() method"
short-title: delete()
slug: Web/API/CrashReportContext/delete
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CrashReportContext.delete
---

{{APIRef("Reporting API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`delete()`** از رابط {{domxref("CrashReportContext")}}، یک جفت کلید-مقدار که قبلاً ذخیره شده را حذف می‌کند.

## نحو (Syntax)

```js-nolint
delete(key)
```

### پارامترها

- `key`
  - : رشته‌ای که کلید جفت کلید-مقدار مورد نظر برای حذف را نشان می‌دهد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : در شرایط زیر پرتاب می‌شود:
    - سند فراخوانی‌شده کاملاً فعال (fully active) نباشد.
    - فروشگاه جفت کلید-مقدار گزارش خرابی هنوز از طریق فراخوانی {{domxref("CrashReportContext.initialize", "initialize()")}} مقداردهی اولیه نشده باشد.

## مثال‌ها

### استفاده پایه

```js
window.crashReport.initialize(1024).then(() => {
  // مقدار احتمالی که می‌تواند باعث خرابی شود را تنظیم کنید، و سعی کنید
  // عملیاتی را اجرا کنید که ممکن است باعث خرابی شود
  window.crashReport.set("crash-arg", "00031");
  operationThatMightCrash("00031");
  // اگر خرابی رخ نداد، جفت کلید-مقدار را حذف کنید
  window.crashReport.delete("crash-arg");
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Reporting API](/en-US/docs/Web/API/Reporting_API)