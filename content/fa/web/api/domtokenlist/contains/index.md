---
title: "DOMTokenList: contains() method"
short-title: contains()
slug: Web/API/DOMTokenList/contains
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.contains
---

{{APIRef("DOM")}}

متد **`contains()`** در {{domxref("DOMTokenList")}} یک مقدار بولین برمی‌گرداند؛ اگر فهرست زیرین شامل توکن داده‌شده باشد، مقدار `true` و در غیر این صورت `false` است.

## سینتکس

```js-nolint
contains(token)
```

### پارامترها

- `token`
  - : رشته‌ای که نمایانگر توکنی است که می‌خواهید وجود آن را در فهرست بررسی کنید.

### مقدار بازگشتی

یک مقدار بولین؛ اگر فهرست موردنظر شامل `token` باشد، مقدار `true` و در غیر این صورت `false` است.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های تنظیم‌شده روی یک عنصر {{htmlelement("span")}} را با استفاده از {{domxref("Element.classList")}} به‌صورت یک `DOMTokenList` دریافت می‌کنیم. سپس وجود `"c"` را در فهرست بررسی کرده و نتیجه را درون {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا HTML:

```html
<span class="a b c"></span>
```

سپس جاوااسکریپت:

```js
const span = document.querySelector("span");
span.textContent = span.classList.contains("c")
  ? "The classList contains 'c'"
  : "The classList does not contain 'c'";
```

خروجی به این صورت است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}