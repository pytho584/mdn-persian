---
title: "Node: baseURI property"
short-title: baseURI
slug: Web/API/Node/baseURI
page-type: web-api-instance-property
browser-compat: api.Node.baseURI
---

{{APIRef("DOM")}}

خصوصیتِ فقط‌خواندنی **`baseURI`** در رابط {{domxref("Node")}}، آدرس پایهٔ مطلق (absolute base URL) سندِ حاوی آن گره را بازمی‌گرداند.

از آدرس پایه برای تبدیل آدرس‌های نسبی به آدرس مطلق استفاده می‌شود، مثلاً وقتی مرورگر نیاز به دریافت آدرس مطلق دارد؛ مانند پردازش ویژگیِ `src` عنصر HTML {{HTMLElement("img")}}، یا ویژگی‌های `xlink:href` {{deprecated_inline}} و `href` در SVG.

اگرچه این خصوصیت فقط‌خواندنی است، مقدار آن هر بار که به خصوصیت دسترسی پیدا می‌شود توسط یک الگوریتم تعیین می‌گردد و در صورت تغییر شرایط، ممکن است تغییر کند.

آدرس پایه به ترتیب زیر تعیین می‌شود:

1. به‌طور پیش‌فرض، آدرس پایه همان مکان سند است (که توسط {{domxref("window.location")}} تعیین می‌شود).
2. اگر سند، یک سند HTML باشد و عنصر {{HTMLElement("Base")}} در آن وجود داشته باشد، مقدار ویژگیِ `href` از _اولین_ عنصر `Base` که دارای چنین ویژگی‌ای باشد، جایگزین می‌شود.

## مقدار

یک رشته (string) که نشان‌دهندهٔ آدرس پایهٔ {{domxref("Node")}} است.

## مثال‌ها

### بدون `<base>`

```html
<output>Not calculated</output>
```

```js
const output = document.querySelector("output");
output.value = output.baseURI;
```

{{EmbedLiveSample("Without_base", "100%", 40)}}

### با `<base>`

```html
<base href="https://developer.mozilla.org/modified_base_uri/" />
<output>Not calculated</output>
```

```js
const output = document.querySelector("output");
output.value = output.baseURI;
```

{{EmbedLiveSample("With_base", "100%", 40)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("base")}}