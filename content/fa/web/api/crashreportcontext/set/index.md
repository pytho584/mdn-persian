---
title: "CrashReportContext: set() method"
---

---
title: "CrashReportContext: set() method"
short-title: set()
slug: Web/API/CrashReportContext/set
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CrashReportContext.set
---

{{APIRef("Reporting API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`set()`** از رابط {{domxref("CrashReportContext")}} یک جفت کلید-مقدار را در حافظه‌ای که توسط {{domxref("CrashReportContext.initialize", "initialize()")}} مقداردهی اولیه شده است، ذخیره می‌کند.

## نحو (Syntax)

```js-nolint
set(key, value)
```

### پارامترها

- `key`
  - : یک رشته (string) که کلید جفت کلید-مقدار مورد نظر برای ذخیره‌سازی را نشان می‌دهد.
- `value`
  - : یک رشته که مقدار جفت کلید-مقدار مورد نظر برای ذخیره‌سازی را نشان می‌دهد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : در شرایط زیر پرتاب می‌شود:
    - سند فراخوانی‌کننده به طور کامل فعال (fully active) نیست.
    - ذخیره‌گاه جفت‌کلید-مقدار گزارش خرابی هنوز از طریق فراخوانی {{domxref("CrashReportContext.initialize", "initialize()")}} مقداردهی اولیه نشده است.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اندازه جفت کلید-مقدار سریال‌شده بزرگ‌تر از مقدار [`length`](/en-US/docs/Web/API/CrashReportContext/initialize#length) تعیین‌شده هنگام مقداردهی اولیه ذخیره‌گاه است.

## مثال‌ها

### استفاده پایه

```js
window.crashReport.initialize(1024).then(() => {
  // یک مقدار بالقوهٔ crash‌آور تنظیم می‌کند و
  // عملیاتی را که ممکن است باعث crash شود اجرا می‌کند
  window.crashReport.set("crash-arg", "00031");
  operationThatMightCrash("00031");
  // اگر crash رخ نداد، جفت کلید-مقدار را حذف می‌کند
  window.crashReport.delete("crash-arg");
});
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [Reporting API](/en-US/docs/Web/API/Reporting_API)