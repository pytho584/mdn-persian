---
title: "DOMTokenList: values() method"
short-title: values()
slug: Web/API/DOMTokenList/values
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.values
---

{{APIRef("DOM")}}

متد **`values()`** در رابط {{domxref("DOMTokenList")}} یک {{jsxref("Iteration_protocols",'iterator')}} (تکرارکننده) برمی‌گرداند که به فراخواننده امکان می‌دهد از میان تمام مقادیر موجود در `DOMTokenList` عبور کند. هر یک از این مقادیر یک رشته است.

## نحو (Syntax)

```js-nolint
values()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Iteration_protocols","iterator")}} (تکرارکننده) برمی‌گرداند.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های اعمال‌شده بر روی یک عنصر {{htmlelement("span")}} را به‌صورت یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم. سپس با استفاده از `values()` یک تکرارکننده حاوی مقادیر به دست می‌آوریم و با یک حلقه [for...of](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) از میان آن مقادیر عبور می‌کنیم و هر کدام را در {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا HTML:

```html
<span class="a b c"></span>
```

حالا جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;
const iterator = classes.values();

for (const value of iterator) {
  span.textContent += `(${value}) `;
}
```

خروجی به این شکل است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}