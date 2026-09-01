---
title: "DOMTokenList: keys() method"
short-title: keys()
slug: Web/API/DOMTokenList/keys
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.keys
---

{{APIRef("DOM")}}

متد **`keys()`** در رابط {{domxref("DOMTokenList")}} یک {{jsxref("Iteration_protocols",'iterator',"",1)}} برمی‌گرداند که امکان پیمایش همه کلیدهای موجود در این شیء را فراهم می‌کند. این کلیدها اعداد صحیح بدون علامت هستند.

## سینتکس

```js-nolint
keys()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Iteration_protocols","iterator","",1)}} را برمی‌گرداند.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های اعمال‌شده روی یک عنصر {{htmlelement("span")}} را به‌صورت یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم. سپس با استفاده از `keys()` یک تکرارگر شامل کلیدها به دست می‌آوریم و با یک حلقه [for...of](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) روی این کلیدها پیمایش می‌کنیم و هرکدام را در {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا، HTML:

```html
<span class="a b c"></span>
```

حالا کد جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;
const iterator = classes.keys();

for (let value of iterator) {
  span.textContent += `(${value}) `;
}
```

خروجی به این صورت است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("DOMTokenList.entries()")}}، {{domxref("DOMTokenList.forEach()")}} و {{domxref("DOMTokenList.values")}}.