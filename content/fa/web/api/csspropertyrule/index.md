---
title: "CSSPropertyRule"
slug: Web/API/CSSPropertyRule
page-type: web-api-interface
browser-compat: api.CSSPropertyRule
---

{{APIRef("CSS Properties and Values API")}}

رابط **`CSSPropertyRule`** از [CSS Properties and Values API](/en-US/docs/Web/API/CSS_Properties_and_Values_API) یک قانون CSS {{cssxref("@property")}} را نمایش می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

ویژگی‌های جد خود {{domxref("CSSRule")}} را به ارث می‌برد.

- {{domxref("CSSPropertyRule.inherits")}} {{ReadOnlyInline}}
  - : پرچم inherit (به‌ارث‌بری) ویژگی سفارشی را برمی‌گرداند.
- {{domxref("CSSPropertyRule.initialValue")}} {{ReadOnlyInline}}
  - : مقدار اولیه ویژگی سفارشی را برمی‌گرداند.
- {{domxref("CSSPropertyRule.name")}} {{ReadOnlyInline}}
  - : نام ویژگی سفارشی را برمی‌گرداند.
- {{domxref("CSSPropertyRule.syntax")}} {{ReadOnlyInline}}
  - : نحو (syntax) تحت‌اللفظی ویژگی سفارشی را برمی‌گرداند.

## روش‌های نمونه

روش خاصی ندارد؛ روش‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد.

## مثال‌ها

این شیوه‌نامه (stylesheet) شامل یک قانون {{cssxref("@property")}} است. اولین {{domxref("CSSRule")}} که بازگردانده می‌شود یک `CSSPropertyRule` با ویژگی‌ها و مقادیر تعریف‌شده توسط قانون در CSS خواهد بود.

```css
@property --property-name {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0]); // A CSSPropertyRule
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}