---
title: "CrashReportContext: initialize() method"
short-title: initialize()
slug: Web/API/CrashReportContext/initialize
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CrashReportContext.initialize
---

{{APIRef("Reporting API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`initialize()`** در رابط {{domxref("CrashReportContext")}} بخشی از حافظه را برای ذخیره‌سازی داده‌های گزارش خرابی که توسط {{domxref("CrashReportContext.set", "set()")}} مشخص می‌شود، مقداردهی اولیه می‌کند. این متد باید قبل از هر متد دیگری روی شیء فراخوانی شود.

## Syntax

```js-nolint
initialize(length)
```

### Parameters

- `length`
  - : عددی که حداکثر تعداد بایت‌هایی را مشخص می‌کند که توسط هر فراخوانی `set()` جداگانه می‌توان در فروشگاه کلید-مقدار ذخیره کرد. حداکثر مقدار مجاز `65536` (۶۴ کیلوبایت) است که همچنین حداکثر حافظه گزارش خرابی مجاز برای یک مبدأ (origin) نیز می‌باشد.

### Return value

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} تکمیل می‌شود.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - سند فراخوانی‌کننده کاملاً فعال (fully active) نباشد.
    - فروشگاه کلید-مقدار گزارش خرابی قبلاً توسط یک فراخوانی `initialize()` مقداردهی اولیه شده باشد.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر `length` بیشتر از `65536` باشد.

## Examples

### استفاده پایه

```js
window.crashReport.initialize(1024).then(() => {
  // Do stuff with crash reporting API
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Reporting API](/en-US/docs/Web/API/Reporting_API)
```