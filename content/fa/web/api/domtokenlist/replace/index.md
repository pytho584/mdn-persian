---
title: "DOMTokenList: replace() method"
short-title: replace()
slug: Web/API/DOMTokenList/replace
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.replace
---

{{APIRef("DOM")}}

متد **`replace()`** در رابط {{domxref("DOMTokenList")}} یک توکن موجود را با یک توکن جدید جایگزین می‌کند.
اگر توکن اول وجود نداشته باشد، `replace()` بلافاصله `false` برمی‌گرداند،
بدون اینکه توکن جدید را به فهرست توکن‌ها اضافه کند.

## نحو (Syntax)

```js-nolint
replace(oldToken, newToken)
```

### پارامترها

- `oldToken`
  - : رشته‌ای که نشان‌دهنده توکنی است که می‌خواهید جایگزین کنید.
- `newToken`
  - : رشته‌ای که نشان‌دهنده توکنی است که می‌خواهید `oldToken` را با آن جایگزین کنید.

### مقدار بازگشتی

یک مقدار بولین که اگر `oldToken` با موفقیت جایگزین شده باشد `true` است، در غیر این صورت `false`.

## مثال‌ها

در مثال زیر، فهرست کلاس‌های تنظیم‌شده روی یک عنصر {{htmlelement("span")}} را به‌صورت یک `DOMTokenList` با استفاده از {{domxref("Element.classList")}} دریافت می‌کنیم. سپس یک توکن را در فهرست جایگزین می‌کنیم و فهرست را در {{domxref("Node.textContent")}} عنصر `<span>` می‌نویسیم.

ابتدا HTML:

```html
<span class="a b c"></span>
```

و سپس جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;

const result = classes.replace("c", "z");

span.textContent = result ? classes : "token not replaced successfully";
```

خروجی به این شکل است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}