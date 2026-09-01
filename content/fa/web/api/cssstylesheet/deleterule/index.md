---
title: "CSSStyleSheet: deleteRule() method"
short-title: deleteRule()
slug: Web/API/CSSStyleSheet/deleteRule
page-type: web-api-instance-method
browser-compat: api.CSSStyleSheet.deleteRule
---

{{APIRef("CSSOM")}}

متد **`deleteRule()`** در {{domxref("CSSStyleSheet")}} یک قانون را از شیء شیوه‌نامه حذف می‌کند.

## نحو

```js-nolint
deleteRule(index)
```

### پارامترها

- `index`
  - : شاخص درون {{domxref("CSSRuleList")}} شیوه‌نامه که قانون مورد نظر برای حذف را مشخص می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این مثال اولین قانون را از شیوه‌نامه `myStyles` حذف می‌کند.

```js
myStyles.deleteRule(0);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model)
- [Constructable Stylesheets](https://web.dev/articles/constructable-stylesheets) (web.dev)
- [استفاده از اطلاعات سبک‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)
- {{domxref("CSSStyleSheet.insertRule", "insertRule()")}}