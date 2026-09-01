---
title: "CSSStyleDeclaration: getPropertyPriority() method"
short-title: getPropertyPriority()
slug: Web/API/CSSStyleDeclaration/getPropertyPriority
page-type: web-api-instance-method
browser-compat: api.CSSStyleDeclaration.getPropertyPriority
---

{{ APIRef("CSSOM") }}

متد **CSSStyleDeclaration.getPropertyPriority()** رشته‌ای را برمی‌گرداند که تمام اولویت‌های صریحاً تعیین‌شده را روی ویژگی CSS نشان می‌دهد.

## Syntax

```js-nolint
getPropertyPriority(property)
```

### پارامترها

- `property`
  - : رشته‌ای که نام ویژگی مورد بررسی را نشان می‌دهد.

### مقدار بازگشتی

رشته‌ای که اولویت (مثلاً `"important"`) را نشان می‌دهد، در صورتی که وجود داشته باشد. اگر هیچ اولویتی وجود نداشته باشد، رشتهٔ خالی را برمی‌گرداند.

## مثال‌ها

کد جاوااسکریپت زیر بررسی می‌کند که آیا `margin` در یک قانون انتخاب‌گر CSS به‌عنوان important علامت‌گذاری شده است:

```js
const declaration = document.styleSheets[0].cssRules[0].style;
const isImportant = declaration.getPropertyPriority("margin") === "important";
```

## Specifications

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}