---
title: "CanvasRenderingContext2D: createPattern() method"
short-title: createPattern()
slug: Web/API/CanvasRenderingContext2D/createPattern
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.createPattern
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.createPattern()`** از Canvas 2D API یک الگو (pattern) با استفاده از تصویر و تکرار مشخص شده ایجاد می‌کند.
این متد یک {{domxref("CanvasPattern")}} برمی‌گرداند.

این متد مستقیماً چیزی روی بوم (canvas) رسم نمی‌کند.
الگوی ایجاد شده باید به ویژگی‌های {{domxref("CanvasRenderingContext2D.fillStyle")}} یا {{domxref("CanvasRenderingContext2D.strokeStyle")}} اختصاص داده شود، پس از آن برای هر ترسیم بعدی اعمال می‌شود.

## Syntax

```js-nolint
createPattern(image, repetition)
```

### پارامترها

- `image`
  - : تصویری که به عنوان تصویر الگو استفاده می‌شود.
    می‌تواند هر یک از موارد زیر باشد:
    - {{domxref("HTMLImageElement")}} ({{HTMLElement("img")}})
    - {{domxref("SVGImageElement")}} ({{SVGElement("image")}})
    - {{domxref("HTMLVideoElement")}} ({{HTMLElement("video")}}، با استفاده از ضبط ویدیو)
    - {{domxref("HTMLCanvasElement")}} ({{HTMLElement("canvas")}})
    - {{domxref("ImageBitmap")}}
    - {{domxref("OffscreenCanvas")}}
    - {{domxref("VideoFrame")}}

- `repetition`
  - : رشته‌ای که نحوه تکرار تصویر الگو را مشخص می‌کند.
    مقادیر ممکن عبارتند از:
    - `"repeat"` (هر دو جهت)
    - `"repeat-x"` (فقط افقی)
    - `"repeat-y"` (فقط عمودی)
    - `"no-repeat"` (هیچ جهتی)

    مقدار [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) همانند رشته خالی (`""`) در نظر گرفته می‌شود: هر دو مترادف `"repeat"` هستند.

### مقدار بازگشتی

یک {{domxref("CanvasPattern")}} مبهم (opaque) که یک الگو را توصیف می‌کند.

اگر `image` به طور کامل بارگذاری نشده باشد ({{domxref("HTMLImageElement.complete")}} برابر `false` باشد)، مقدار [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برگردانده می‌شود.

## مثال‌ها

### ایجاد الگو از یک تصویر

این مثال از متد `createPattern()` برای ایجاد یک {{domxref("CanvasPattern")}} با یک تصویر منبع تکراری استفاده می‌کند.
پس از ایجاد، الگو به سبک پر کردن بوم (canvas context) اختصاص داده می‌شود و روی یک مستطیل اعمال می‌شود.

تصویر اصلی به این شکل است:

![یک الگوی گلدار](canvas_create_pattern.png)

#### HTML

```html
<canvas id="canvas" width="300" height="300"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const img = new Image();
img.src = "canvas_create_pattern.png";
// فقط پس از بارگذاری تصویر از آن استفاده کنید
img.onload = () => {
  const pattern = ctx.createPattern(img, "repeat");
  ctx.fillStyle = pattern;
  ctx.fillRect(0, 0, 300, 300);
};
```

{{ EmbedLiveSample('Creating_a_pattern_from_an_image', 700, 310) }}

### ایجاد الگو از یک بوم

در این مثال ما یک الگو از محتویات یک بوم خارج از صفحه (offscreen canvas) ایجاد می‌کنیم.
سپس آن را به سبک پر کردن بوم اصلی خود اعمال می‌کنیم و آن بوم را با الگو پر می‌کنیم.

#### JavaScript

```js
// ایجاد یک الگو، خارج از صفحه
const patternCanvas = document.createElement("canvas");
const patternContext = patternCanvas.getContext("2d");

// عرض و ارتفاع 50 به الگو بدهید
patternCanvas.width = 50;
patternCanvas.height = 50;

// به الگو یک رنگ پس‌زمینه بدهید و یک کمان رسم کنید
patternContext.fillStyle = "#ffeecc";
patternContext.fillRect(0, 0, patternCanvas.width, patternCanvas.height);
patternContext.arc(0, 0, 50, 0, 0.5 * Math.PI);
patternContext.stroke();

// بوم اصلی خود را ایجاد کنید و آن را با الگو پر کنید
const canvas = document.createElement("canvas");
const ctx = canvas.getContext("2d");
const pattern = ctx.createPattern(patternCanvas, "repeat");
ctx.fillStyle = pattern;
ctx.fillRect(0, 0, canvas.width, canvas.height);

// بوم اصلی خود را به صفحه وب اضافه کنید
document.body.appendChild(canvas);
```

#### نتیجه

{{ EmbedLiveSample('Creating_a_pattern_from_a_canvas', 700, 160) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasPattern")}}