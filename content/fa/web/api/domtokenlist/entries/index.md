---
title: "DOMTokenList: entries() method"
short-title: entries()
slug: Web/API/DOMTokenList/entries
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.entries
---

{{APIRef("DOM")}}

متد **`entries()``** از رابط {{domxref("DOMTokenList")}} یک {{jsxref("Iteration_protocols","تکرارگر (iterator)")}} بازمی‌گرداند که به شما امکان می‌دهد تمام جفت‌های کلید/مقدار موجود در این شیء را پیمایش کنید. مقادیر، {{jsxref("Array")}}هایی هستند که هر کدام یک جفت [کلید, مقدار] را نشان می‌دهند و هر جفت نمایانگر یک توکن است.

## نحو

```js-nolint
entries()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Iteration_protocols","تکرارگر (iterator)")}} بازمی‌گرداند.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های تنظیم‌شده روی یک عنصر {{htmlelement("span")}} را به صورت یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم. سپس یک تکرارگر حاوی جفت‌های کلید/مقدار را با استفاده از `entries()` به دست می‌آوریم و با یک حلقه {{jsxref("Statements/for...of", "for...of")}} روی آن‌ها پیمایش می‌کنیم و هر جفت را در {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا، HTML:

```html
<span class="a b c"></span>
```

حالا جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;
const iterator = classes.entries();

for (const value of iterator) {
  span.textContent += `(${value})`;
}
```

خروجی به صورت زیر است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMTokenList.foreach()")}}, {{domxref("DOMTokenList.keys")}} و {{domxref("DOMTokenList.values")}}.