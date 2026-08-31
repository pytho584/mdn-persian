---
title: "CSSGroupingRule: insertRule() method"
short-title: insertRule()
slug: Web/API/CSSGroupingRule/insertRule
page-type: web-api-instance-method
browser-compat: api.CSSGroupingRule.insertRule
---

{{ APIRef("CSSOM") }}

متد **`insertRule()`** از رابط {{domxref("CSSGroupingRule")}} یک قانون CSS جدید به فهرستی از قوانین CSS اضافه می‌کند.

## نحو (Syntax)

```js-nolint
insertRule(rule)
insertRule(rule, index)
```

### پارامترها

- `rule`
  - : یک رشته (string)
- `index` {{optional_inline}}
  - : یک ایندکس اختیاری که قانون در آن درج می‌شود؛ پیش‌فرض ۰ است.

### مقدار بازگشتی

ایندکس قانون جدید.

### استثناها (Exceptions)

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `index` بزرگ‌تر از تعداد قوانین CSS فرزند باشد، پرتاب می‌شود.
- `HierarchyRequestError` {{domxref("DOMException")}}
  - : اگر `rule` به دلیل برخی محدودیت‌های CSS در ایندکس مشخص‌شده قابل درج نباشد، پرتاب می‌شود.
- `HierarchyRequestError` {{domxref("DOMException")}}
  - : اگر `rule` یک دستور معتبر باشد اما یک [دستور تو در تو](/en-US/docs/Web/CSS/Guides/Syntax/Introduction#nested_statements) نباشد، پرتاب می‌شود.

## مثال‌ها

```js
let myRules = document.styleSheets[0].cssRules;
myRules[0].insertRule(
  "html {background-color: blue;}",
  0,
); /* inserts a rule for the HTML element at position 0 */
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
