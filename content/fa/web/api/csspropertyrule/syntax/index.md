---
title: "CSSPropertyRule: syntax property"
short-title: syntax
slug: Web/API/CSSPropertyRule/syntax
page-type: web-api-instance-property
browser-compat: api.CSSPropertyRule.syntax
---

{{APIRef("CSS Properties and Values API")}}

خاصیت فقط‌خواندنی **`syntax`** از رابط {{domxref("CSSPropertyRule")}}، نحوِ (syntax) تحت‌اللفظی ثبتِ ویژگی سفارشی را که توسط قانون {{cssxref("@property")}} نمایش داده می‌شود، برمی‌گرداند. این نحو نحوهٔ تجزیهٔ مقدار ویژگی را در زمان مقدار محاسبه‌شده کنترل می‌کند.

## مقدار

یک رشته (string).

## مثال‌ها

این شیوه‌نامه (stylesheet) شامل یک قانون {{cssxref("@property")}} است. اولین {{domxref("CSSRule")}} بازگشت‌داده‌شده، یک `CSSPropertyRule` خواهد بود که این قانون را نمایش می‌دهد. خاصیت `syntax` رشتهٔ تحت‌اللفظی `"<color>"` را برمی‌گرداند.

```css
@property --property-name {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].syntax); // "<color>"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}