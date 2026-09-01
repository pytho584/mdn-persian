---
title: "CSSPropertyRule: inherits property"
short-title: inherits
slug: Web/API/CSSPropertyRule/inherits
page-type: web-api-instance-property
browser-compat: api.CSSPropertyRule.inherits
---

{{APIRef("CSS Properties and Values API")}}

ویژگی فقط‌خواندنی **`inherits`** از رابط {{domxref("CSSPropertyRule")}}، پرچم ارث‌بریِ ثبتِ ویژگی سفارشی را که توسط قانون {{cssxref("@property")}} نمایش داده می‌شود، برمی‌گرداند؛ یک مقدار بولی که مشخص می‌کند آیا آن ویژگی به‌صورت پیش‌فرض ارث‌بری می‌شود یا نه.

## مقدار

یک مقدار بولی.

## مثال‌ها

این استایل‌شیت شامل یک قانون {{cssxref("@property")}} است. اولین {{domxref("CSSRule")}} بازگشت‌داده‌شده یک `CSSPropertyRule` خواهد بود که این قانون را نمایش می‌دهد. ویژگی `inherits` مقدار بولی `false` را برمی‌گرداند؛ این همان مقداری است که برای ویژگی `inherits` در CSS تعیین شده است.

```css
@property --property-name {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].inherits); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}