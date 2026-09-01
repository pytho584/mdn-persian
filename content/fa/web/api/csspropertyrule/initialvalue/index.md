---
title: "CSSPropertyRule: initialValue property"
short-title: initialValue
slug: Web/API/CSSPropertyRule/initialValue
page-type: web-api-instance-property
browser-compat: api.CSSPropertyRule.initialValue
---

{{APIRef("CSS Properties and Values API")}}

خاصیت فقط‌خواندنی **`initialValue`** از رابط {{domxref("CSSPropertyRule")}} مقدار اولیهٔ ثبتِ ویژگی سفارشی نمایش‌داده‌شده توسط قانون {{cssxref("@property")}} را برمی‌گرداند و مقدار اولیهٔ آن ویژگی را کنترل می‌کند.

## مقدار

یک رشته که یک [`<declaration-value>`](https://drafts.csswg.org/css-syntax/#typedef-declaration-value) است.

## مثال‌ها

این استایل‌شیت شامل یک قانون {{cssxref("@property")}} است. اولین {{domxref("CSSRule")}} برگشتی یک `CSSPropertyRule` خواهد بود که این قانون را نمایش می‌دهد. خاصیت `initialValue` رشتهٔ `"#c0ffee"` را برمی‌گرداند که همان مقدار خصوصیت `initial-value` در CSS است.

```css
@property --property-name {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].initialValue); // "#c0ffee"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```