---
title: "CSSPropertyRule: name property"
short-title: name
slug: Web/API/CSSPropertyRule/name
page-type: web-api-instance-property
browser-compat: api.CSSPropertyRule.name
---

{{APIRef("CSS Properties and Values API")}}

ویژگی فقط‌خواندنی **`name`** از رابط {{domxref("CSSPropertyRule")}} نمایانگر نام ویژگی (property) است؛ این نام همان نمایش رشته‌ای (serialization) از نامی است که به ویژگی سفارشی در مقدمه (prelude) قاعده {{cssxref("@property")}} داده شده است.

## مقدار

یک رشته (string).

## مثال‌ها

این شیوه‌نامه (stylesheet) شامل یک قاعده {{cssxref("@property")}} است. اولین {{domxref("CSSRule")}} بازگشتی یک `CSSPropertyRule` خواهد بود که این قاعده را نشان می‌دهد. ویژگی `name` رشته `"--property-name"` را برمی‌گرداند که همان نام داده شده به ویژگی سفارشی در CSS است.

```css
@property --property-name {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].name); // "--property-name"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}