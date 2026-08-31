---
title: "CSSGroupingRule: deleteRule() method"
---

---
title: "CSSGroupingRule: deleteRule() method"
short-title: deleteRule()
slug: Web/API/CSSGroupingRule/deleteRule
page-type: web-api-instance-method
browser-compat: api.CSSGroupingRule.deleteRule
---

{{ APIRef("CSSOM") }}

متد **`deleteRule()`** از رابط {{domxref("CSSGroupingRule")}} یک قانون CSS را از فهرست قوانین CSS فرزند حذف می‌کند.

## نحو

```js-nolint
deleteRule(index)
```

### پارامترها

- `index`
  - : شاخص قاعده‌ای که باید حذف شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر _index_ بزرگ‌تر یا مساوی تعداد قوانین CSS فرزند باشد، این استثنا پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر قاعده‌ای که حذف می‌شود یک at-rule از نوع `@namespace` باشد و فهرست قوانین CSS فرزند شامل چیزی غیر از at-rule‌های `@import` و at-rule‌های `@namespace` باشد، پرتاب می‌شود.

## مثال‌ها

```js
let myRules = document.styleSheets[0].cssRules;
myRules[0].deleteRule(2); /* deletes the rule at index 2 */
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}