---
title: "CSSFunctionRule: getParameters() method"
short-title: getParameters()
slug: Web/API/CSSFunctionRule/getParameters
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CSSFunctionRule.getParameters
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

متد **`getParameters()`** در رابط {{domxref("CSSFunctionRule")}} آرایه‌ای از اشیا را برمی‌گرداند که پارامترهای تابع سفارشی را نمایش می‌دهند.

## Syntax

```js-nolint
getParameters()
```

### پارامترها

هیچ.

### مقدار بازگشتی

آرایه‌ای از اشیا شامل ویژگی‌های زیر:

- `name`
  - : یک رشته که نام پارامتر تابع را نشان می‌دهد.
- `type`
  - : یک رشته که نوع داده پارامتر را نشان می‌دهد، یا اگر نوع داده‌ای مشخص نشده باشد `*` را برمی‌گرداند.
- `defaultValue`
  - : یک رشته که مقدار پیش‌فرض پارامتر را نشان می‌دهد، یا اگر مقدار پیش‌فرضی مشخص نشده باشد `null` را برمی‌گرداند.

اگر پارامتری در {{cssxref("@function")}} at-rule مرتبط مشخص نشده باشد، یک آرایه خالی برگردانده می‌شود.

## مثال‌ها

برای مشاهده مثال، به صفحه مرجع اصلی {{domxref("CSSFunctionRule")}} مراجعه کنید.

## Specifications

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@function")}}