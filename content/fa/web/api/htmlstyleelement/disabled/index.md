---
title: "HTMLStyleElement: disabled property"
short-title: disabled
slug: Web/API/HTMLStyleElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLStyleElement.disabled
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLStyleElement.disabled`** برای خواندن و تنظیم اینکه آیا شیوه‌نامه غیرفعال است (`true`) یا نه (`false`) استفاده می‌شود.

توجه داشته باشید که هیچ ویژگی `disabled` متناظری روی [عنصر `<style>` در HTML](/en-US/docs/Web/HTML/Reference/Elements/style) وجود ندارد.

## مقدار

اگر شیوه‌نامه غیرفعال باشد یا شیوه‌نامه مرتبطی وجود نداشته باشد، `true` برمی‌گرداند؛ در غیر این صورت `false`.
مقدار پیش‌فرض `false` است (اگر شیوه‌نامه مرتبطی وجود داشته باشد).

از این ویژگی می‌توان برای فعال یا غیرفعال کردن یک شیوه‌نامه مرتبط استفاده کرد.
تنظیم این ویژگی روی `true` وقتی شیوه‌نامه مرتبطی وجود نداشته باشد، هیچ اثری ندارد.

## مثال‌ها

### غیرفعال کردن یک سبک درون‌خطی

این مثال تنظیم برنامه‌نویسی‌شده ویژگی `disabled` را بر روی یک سبک که در HTML با استفاده از [عنصر `<style>` در HTML](/en-US/docs/Web/HTML/Reference/Elements/style) تعریف شده است، نشان می‌دهد.
توجه داشته باشید که می‌توانید به همه شیوه‌نامه‌های سند نیز با استفاده از [`Document.styleSheets`](/en-US/docs/Web/API/Document/styleSheets) دسترسی داشته باشید.

#### HTML

HTML شامل یک عنصر [`<style>`](/en-US/docs/Web/HTML/Reference/Elements/style) است که عناصر پاراگراف را آبی می‌کند، یک عنصر پاراگراف، و یک دکمه که برای فعال و غیرفعال کردن سبک استفاده خواهد شد.

```html
<button>Enable</button>
<style id="InlineStyle">
  p {
    color: blue;
  }
</style>
<p>Text is black when style is disabled; blue when enabled.</p>
<p></p>
```

#### جاوااسکریپت

کد زیر عنصر `style` را با استفاده از شناسه آن دریافت می‌کند و سپس آن را غیرفعال می‌کند.
از آنجا که این سبک از قبل وجود دارد (چون در SVG تعریف شده است)، این عمل باید موفق باشد.

```js
const style = document.getElementById("InlineStyle");
style.disabled = true;
```

سپس یک رویدادگردان برای دکمه اضافه می‌کنیم که مقدار `disabled` و متن دکمه را تغییر می‌دهد.

```js
const button = document.querySelector("button");

button.addEventListener("click", () => {
  style.disabled = !style.disabled;
  const buttonText = style.disabled ? "Enable" : "Disable";
  button.innerText = buttonText;
});
```

#### نتیجه

نتیجه در زیر نمایش داده شده است.
دکمه را فشار دهید تا مقدار ویژگی `disabled` روی سبک مورد استفاده برای متن پاراگراف تغییر کند.

{{EmbedLiveSample("Disabling a style defined in the SVG")}}

### غیرفعال کردن یک سبک تعریف‌شده به صورت برنامه‌نویسی

این مثال بسیار شبیه به مثال بالا است، با این تفاوت که سبک به صورت برنامه‌نویسی تعریف می‌شود.

#### HTML

HTML مشابه حالت قبلی است، اما تعریف شامل هیچ استایل پیش‌فرضی نیست.

```html
<button>Enable</button>
<p>Text is black when style is disabled; blue when enabled.</p>
<p></p>
```

#### جاوااسکریپت

ابتدا عنصر سبک جدید را روی HTML ایجاد می‌کنیم.
این کار با ایجاد یک عنصر `style` با استفاده از [`Document.createElement()`](/en-US/docs/Web/API/Document/createElement)، ایجاد و افزودن یک گره متنی شامل تعریف سبک، و سپس افزودن عنصر سبک به بدنه سند انجام می‌شود.

```js
// Create the `style` element
const style = document.createElement("style");
const node = document.createTextNode("p { color: blue; }");
style.appendChild(node);
document.body.appendChild(style);
```

سپس می‌توانیم سبک را همانطور که در زیر نشان داده شده است غیرفعال کنیم.
توجه داشته باشید که این اولین نقطه‌ای است که تنظیم ویژگی روی `true` موفق خواهد بود.
قبل از این نقطه، سند سبک مرتبطی نداشت و بنابراین مقدار پیش‌فرض `false` است.

```js
// Disable the style
style.disabled = true;
```

در نهایت، یک رویدادگردان برای دکمه اضافه می‌کنیم که وضعیت غیرفعال و متن دکمه را تغییر می‌دهد (همانند مثال قبلی).

```js
const button = document.querySelector("button");

button.addEventListener("click", () => {
  style.disabled = !style.disabled;
  const buttonText = style.disabled ? "Enable" : "Disable";
  button.innerText = buttonText;
});
```

#### نتیجه

نتیجه در زیر نمایش داده شده است.
دکمه را فشار دهید تا وضعیت `disabled` روی سبک مورد استفاده برای متن تغییر کند.

{{EmbedLiveSample("Disabling a programmatically defined style")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SVGStyleElement.disabled")}}