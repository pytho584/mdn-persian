---
title: "CanvasRenderingContext2D: stroke() method"
short-title: stroke()
slug: Web/API/CanvasRenderingContext2D/stroke
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.stroke
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.stroke()`**
از Canvas 2D API، مسیر جاری یا مسیر داده‌شده را با استایل خط‌کشی (stroke) جاری، خط‌کشی (طرح‌ریزی) می‌کند.

خط‌کشی‌ها در مرکز مسیر تراز می‌شوند؛ به عبارت دیگر، نیمی از خط در سمت داخلی و نیمی در سمت خارجی رسم می‌شود.

خط‌کشی با استفاده از [قانون ناهمجهت (non-zero winding rule)](https://en.wikipedia.org/wiki/Nonzero-rule) رسم می‌شود، به این معنی که تقاطع‌های مسیر همچنان پر می‌شوند.

## نحو (Syntax)

```js-nolint
stroke()
stroke(path)
```

### پارامترها

- `path`
  - : یک مسیر {{domxref("Path2D")}} برای خط‌کشی.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### یک مستطیل ساده خط‌کشی‌شده

این مثال یک مستطیل با استفاده از متد `rect()` ایجاد می‌کند و سپس آن را با استفاده از `stroke()` روی بوم رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.rect(10, 10, 150, 100);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('A_simple_stroked_rectangle', 700, 180) }}

### خط‌کشی مجدد مسیرها

معمولاً برای هر چیز جدیدی که می‌خواهید خط‌کشی کنید، باید {{domxref("CanvasRenderingContext2D.beginPath()", "beginPath()")}} را فراخوانی کنید. اگر این کار را نکنید، زیرمسیرهای قبلی بخشی از مسیر جاری باقی می‌مانند و هر بار که متد `stroke()` را فراخوانی می‌کنید، خط‌کشی می‌شوند. با این حال، در برخی موارد ممکن است این اثر مطلوب باشد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

این کد مسیر اول را سه بار، مسیر دوم را دو بار و مسیر سوم را فقط یک بار خط‌کشی می‌کند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// First sub-path
ctx.lineWidth = 26;
ctx.strokeStyle = "orange";
ctx.moveTo(20, 20);
ctx.lineTo(160, 20);
ctx.stroke();

// Second sub-path
ctx.lineWidth = 14;
ctx.strokeStyle = "green";
ctx.moveTo(20, 80);
ctx.lineTo(220, 80);
ctx.stroke();

// Third sub-path
ctx.lineWidth = 4;
ctx.strokeStyle = "pink";
ctx.moveTo(20, 140);
ctx.lineTo(280, 140);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Re-stroking_paths', 700, 180) }}

### خط‌کشی و پر کردن

اگر می‌خواهید هم خط‌کشی و هم پر کردن یک مسیر انجام دهید، ترتیب انجام این عملیات تعیین‌کننده نتیجه خواهد بود. در این مثال، مربع سمت چپ با خط‌کشی روی پر شدن رسم شده است. مربع سمت راست با پر شدن روی خط‌کشی رسم شده است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.lineWidth = 16;
ctx.strokeStyle = "red";

// Stroke on top of fill
ctx.beginPath();
ctx.rect(25, 25, 100, 100);
ctx.fill();
ctx.stroke();

// Fill on top of stroke
ctx.beginPath();
ctx.rect(175, 25, 100, 100);
ctx.stroke();
ctx.fill();
```

#### نتیجه

{{ EmbedLiveSample('Stroking_and_filling', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}