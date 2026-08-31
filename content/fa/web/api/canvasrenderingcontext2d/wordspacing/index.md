---
title: "CanvasRenderingContext2D: wordSpacing property"
short-title: wordSpacing
slug: Web/API/CanvasRenderingContext2D/wordSpacing
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.wordSpacing
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.wordSpacing`** از [Canvas API](/en-US/docs/Web/API/Canvas_API) فاصله بین کلمات را هنگام ترسیم متن مشخص می‌کند.

این ویژگی معادل ویژگی CSS {{cssxref("word-spacing")}} است.

## مقدار

فاصله کلمات به صورت یک رشته در قالب داده {{cssxref("length")}} CSS. پیش‌فرض `0px` است.

از این ویژگی می‌توان برای دریافت یا تنظیم فاصله استفاده کرد. اگر مقدار نامعتبر/غیرقابل‌پردازش تنظیم شود، مقدار ویژگی بدون تغییر باقی می‌ماند.

## مثال‌ها

در این مثال، متن "Hello World" را سه بار نمایش می‌دهیم و از ویژگی `wordSpacing` برای تغییر فاصله در هر مورد استفاده می‌کنیم. فاصله نیز برای هر مورد با استفاده از مقدار ویژگی نمایش داده می‌شود.

### HTML

```html
<canvas id="canvas" width="700"></canvas>
```

### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "30px serif";

// Default word spacing
ctx.fillText(`Hello world (default: ${ctx.wordSpacing})`, 10, 40);

// Custom word spacing: 10px
ctx.wordSpacing = "10px";
ctx.fillText(`Hello world (${ctx.wordSpacing})`, 10, 90);

// Custom word spacing: 30px
ctx.wordSpacing = "30px";
ctx.fillText(`Hello world (${ctx.wordSpacing})`, 10, 140);
```

### نتیجه

{{ EmbedLiveSample('Examples', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CanvasRenderingContext2D.letterSpacing")}}