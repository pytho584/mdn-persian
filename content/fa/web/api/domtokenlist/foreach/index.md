---
title: "DOMTokenList: forEach() method"
short-title: forEach()
slug: Web/API/DOMTokenList/forEach
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.forEach
---

{{APIRef("DOM")}}

متد **`forEach()`** در رابط {{domxref("DOMTokenList")}}، تابعِ داده‌شده در پارامتر را یک‌بار برای هر جفت مقدار در فهرست، به ترتیب درج، فراخوانی می‌کند.

## نحو (Syntax)

```js-nolint
forEach(callback)
forEach(callback, thisArg)
```

### پارامترها

- `callback`
  - : تابعی که برای هر عنصر اجرا می‌شود و در نهایت سه آرگومان می‌گیرد:
    - `currentValue`
      - : عنصر فعلی که در آرایه در حال پردازش است.
    - `currentIndex`
      - : اندیس عنصر فعلی که در آرایه در حال پردازش است.
    - `listObj`
      - : آرایه‌ای که `forEach()` روی آن اعمال می‌شود.

- `thisArg` {{Optional_inline}}
  - : مقداری که هنگام اجرای `callback` به‌عنوان {{jsxref("this")}} استفاده می‌شود.

### مقدار بازگشتی

هیچ‌کدام.

## مثال

در مثال زیر، فهرست کلاس‌های تنظیم‌شده روی یک عنصر {{htmlelement("pre")}} را به‌عنوان یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم. سپس با استفاده از `forEach()` یک تکرارگر (iterator) حاوی مقادیر را دریافت کرده و هر مقدار را در داخل تابع داخلی `forEach()` در {{domxref("Node.textContent")}} عنصر `<pre>` می‌نویسیم.

### HTML

```html
<pre class="a b c"></pre>
```

### JavaScript

```js
const pre = document.querySelector("pre");
const classes = pre.classList;
const iterator = classes.values();

classes.forEach(function (value, key, listObj) {
  pre.textContent += `(${value} ${key})/${this}\n`;
}, "arg");
```

### نتیجه

{{ EmbedLiveSample('Example', '100%', 100) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMTokenList.entries()")}}، {{domxref("DOMTokenList.keys")}} و {{domxref("DOMTokenList.values")}}.