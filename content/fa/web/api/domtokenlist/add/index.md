---
title: "DOMTokenList: add() method"
short-title: add()
slug: Web/API/DOMTokenList/add
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.add
---

{{APIRef("DOM")}}

روش **`add()`** از رابط {{domxref("DOMTokenList")}} توکن‌های داده شده را به لیست اضافه می‌کند و هر توکنی که از قبل وجود دارد را نادیده می‌گیرد.

## نحو

```js-nolint
add(token1)
add(token1, token2)
add(token1, token2, /* …, */ tokenN)
```

### پارامترها

- `tokenN`
  - : یک رشته که نشان‌دهنده یک توکن (یا توکن‌هایی) است که به `DOMTokenList` اضافه می‌شود.

### مقدار بازگشتی

هیچ‌کدام.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر یکی از آرگومان‌ها یک رشته خالی باشد، پرتاب می‌شود.
- `InvalidCharacterError` {{domxref("DOMException")}}
  - : اگر یک توکن حاوی فضای خالی ASCII باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، لیست کلاس‌های تنظیم شده روی یک عنصر {{htmlelement("span")}} را به عنوان یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} بازیابی می‌کنیم. سپس یک توکن جدید به لیست اضافه می‌کنیم و لیست را در {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا، HTML:

```html
<span class="a b c"></span>
```

حالا جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;
classes.add("d");
span.textContent = classes;
```

خروجی به این شکل است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

همچنین می‌توانید چندین توکن را اضافه کنید:

```js
span.classList.add("d", "e", "f");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}