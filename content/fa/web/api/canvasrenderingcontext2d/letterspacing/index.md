---
title: "CanvasRenderingContext2D: letterSpacing property"
short-title: letterSpacing
slug: Web/API/CanvasRenderingContext2D/letterSpacing
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.letterSpacing
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.letterSpacing`** از [Canvas API](/en-US/docs/Web/API/Canvas_API) فاصله بین حروف هنگام ترسیم متن را مشخص می‌کند.

این ویژگی معادل ویژگی CSS {{cssxref("letter-spacing")}} است.

## مقدار

فاصله بین حروف به صورت یک رشته در قالب داده {{cssxref("length")}} در CSS. مقدار پیش‌فرض `0px` است.

از این ویژگی می‌توان برای دریافت یا تنظیم فاصله استفاده کرد. اگر مقدار نامعتبر یا غیرقابل تجزیه تنظیم شود، مقدار ویژگی بدون تغییر باقی می‌ماند.

## مثال‌ها

در این مثال، متن "Hello World" را سه بار نمایش می‌دهیم و از ویژگی `letterSpacing` برای تغییر فاصله بین حروف در هر مورد استفاده می‌کنیم. همچنین فاصله برای هر مورد با استفاده از مقدار ویژگی نمایش داده می‌شود.

### HTML

```html
<canvas id="canvas" width="700"></canvas>
```

### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "30px serif";

// فاصله پیش‌فرض بین حروف
ctx.fillText(`Hello world (default: ${ctx.letterSpacing})`, 10, 40);

// فاصله سفارشی: 10px
ctx.letterSpacing = "10px";
ctx.fillText(`Hello world (${ctx.letterSpacing})`, 10, 90);

// فاصله سفارشی: 20px
ctx.letterSpacing = "20px";
ctx.fillText(`Hello world (${ctx.letterSpacing})`, 10, 140);
```

### نتیجه

{{ EmbedLiveSample('Examples', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CanvasRenderingContext2D.wordSpacing")}}