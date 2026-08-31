---
title: "CanvasRenderingContext2D: textRendering property"
short-title: textRendering
slug: Web/API/CanvasRenderingContext2D/textRendering
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.textRendering
---

{{APIRef("Canvas API")}}

خصوصیت **`CanvasRenderingContext2D.textRendering`** در [Canvas API](/en-US/docs/Web/API/Canvas_API) اطلاعاتی را در اختیار موتور رندر قرار می‌دهد که هنگام رندر کردن متن، چه چیزی باید بهینه شود.

مقادیر این خصوصیت با صفت SVG [`text-rendering`](/en-US/docs/Web/SVG/Reference/Attribute/text-rendering) (و خصوصیت CSS {{cssxref("text-rendering")}}) مطابقت دارند.

## مقدار

یک راهنمای text-rendering برای موتور مرورگر. این مقدار یکی از موارد زیر است:

- `auto`
  - : مرورگر هنگام رسم متن، حدس‌های آگاهانه‌ای درباره زمان بهینه‌سازی برای سرعت، خوانایی و دقت هندسی می‌زند.
- `optimizeSpeed`
  - : مرورگر هنگام رسم متن، سرعت رندر را بر خوانایی و دقت هندسی ترجیح می‌دهد. این مقدار کرنینگ و لیگاتورها را غیرفعال می‌کند.
- `optimizeLegibility`
  - : مرورگر خوانایی را بر سرعت رندر و دقت هندسی ترجیح می‌دهد. این مقدار کرنینگ و لیگاتورهای اختیاری را فعال می‌کند.
- `geometricPrecision`
  - : مرورگر دقت هندسی را بر سرعت رندر و خوانایی ترجیح می‌دهد. برخی از جنبه‌های فونت‌ها — مانند کرنینگ — به صورت خطی مقیاس‌پذیر نیستند. برای ضریب‌های مقیاس بزرگ، ممکن است رندر متنی با کیفیت کمتر از حد مطلوب ببینید، اما اندازه دقیقاً همان چیزی است که انتظار دارید (نه گرد شده به بالا و نه به پایین به نزدیک‌ترین اندازه فونت پشتیبانی‌شده توسط سیستم عامل).

از این خصوصیت می‌توان برای دریافت یا تنظیم مقدار استفاده کرد.

## مثال‌ها

در این مثال، متن «Hello World» را با استفاده از هر یک از مقادیر پشتیبانی‌شده خصوصیت `textRendering` نمایش می‌دهیم. مقدار برای هر حالت نیز با خواندن خصوصیت نمایش داده می‌شود.

### HTML

```html
<canvas id="canvas" width="700" height="220"></canvas>
```

### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.font = "20px serif";

// Default (auto)
ctx.fillText(`Hello world (default: ${ctx.textRendering})`, 5, 20);

// Text rendering: optimizeSpeed
ctx.textRendering = "optimizeSpeed";
ctx.fillText(`Hello world (${ctx.textRendering})`, 5, 50);

// Text rendering: optimizeLegibility
ctx.textRendering = "optimizeLegibility";
ctx.fillText(`Hello world (${ctx.textRendering})`, 5, 80);

// Text rendering: geometricPrecision
ctx.textRendering = "geometricPrecision";
ctx.fillText(`Hello world (${ctx.textRendering})`, 5, 110);
```

### نتیجه

{{ EmbedLiveSample('Examples', 700, 230) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}