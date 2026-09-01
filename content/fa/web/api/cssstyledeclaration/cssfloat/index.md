---
title: "CSSStyleDeclaration: cssFloat property"
short-title: cssFloat
slug: Web/API/CSSStyleDeclaration/cssFloat
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.CSSStyleDeclaration.cssFloat
---

{{APIRef("CSSOM")}}{{deprecated_header}}

ویژگی **`cssFloat`** از رابط {{domxref("CSSStyleDeclaration")}} نتیجهٔ فراخوانی {{DOMxRef("CSSStyleDeclaration.getPropertyValue()")}} با آرگومان `float` را بازمی‌گرداند.

هنگام تنظیم، این ویژگی {{DOMxRef("CSSStyleDeclaration.setProperty()")}} را با `float` به عنوان آرگومان اول و مقدار داده‌شده به عنوان آرگومان دوم فراخوانی می‌کند. مقدار داده‌شده باید یک مقدار معتبر برای ویژگی {{cssxref("float")}} باشد.

## مقدار

یک رشته.

هنگام تنظیم به مقدار `null`، آن مقدار `null` به رشتهٔ خالی (`""`) تبدیل می‌شود، بنابراین `csd.cssFloat = null` معادل `csd.cssFloat = ""` است.

## مثال

در مثال زیر، شیوه‌نامه شامل یک قاعده برای `.box` است که ویژگی {{cssxref("float")}} را با مقدار `left` دارد. این مقدار توسط `cssFloat` بازگردانده می‌شود. سپس مقدار را با استفاده از `cssFloat` به `"right"` تنظیم می‌کنیم و مقدار جدید را بازمی‌گردانیم.

```css
.box {
  float: left;
  inline-size: 300px;
}
```

```js
let myRules = document.styleSheets[0].cssRules;
let rule = myRules[0];
console.log(rule.style.cssFloat); // "left"
rule.style.cssFloat = "right";
console.log(rule.style.cssFloat); // "right"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}