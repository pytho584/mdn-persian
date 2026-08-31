---
title: "CanvasRenderingContext2D: clearRect() method"
short-title: clearRect()
slug: Web/API/CanvasRenderingContext2D/clearRect
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.clearRect
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.clearRect()`** از Canvas 2D API، پیکسل‌های یک ناحیه مستطیلی را با تنظیم آن‌ها به رنگ سیاه شفاف (transparent black) پاک می‌کند.

> [!NOTE]
> توجه داشته باشید که `clearRect()` ممکن است عوارض جانبی ناخواسته‌ای ایجاد کند اگر [از مسیرها به درستی استفاده نکنید](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes#drawing_paths). پس از فراخوانی `clearRect()`، قبل از شروع ترسیم آیتم‌های جدید، حتماً {{domxref("CanvasRenderingContext2D.beginPath", "beginPath()")}} را فراخوانی کنید.

## Syntax

```js-nolint
clearRect(x, y, width, height)
```

متد `clearRect()` پیکسل‌های یک ناحیه مستطیلی را به حالت شفاف تنظیم می‌کند. گوشه بالا-چپ مستطیل در مختصات `(x, y)` قرار دارد و اندازه آن توسط `width` و `height` مشخص می‌شود.

### Parameters

- `x`
  - : مختصات محور x نقطه شروع مستطیل.
- `y`
  - : مختصات محور y نقطه شروع مستطیل.
- `width`
  - : عرض مستطیل. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند.
- `height`
  - : ارتفاع مستطیل. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### پاک کردن کل بوم (canvas)

این قطعه کد کل بوم را پاک می‌کند. این کار معمولاً در شروع هر فریم در یک انیمیشن مورد نیاز است. ابعاد ناحیه پاک‌شده برابر با ویژگی‌های `width` و `height` عنصر {{HtmlElement("canvas")}} تنظیم می‌شود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.clearRect(0, 0, canvas.width, canvas.height);
```

### پاک کردن بخشی از یک بوم

این مثال یک مثلث آبی را روی یک پس‌زمینه مایل به زرد رسم می‌کند. سپس متد `clearRect()` بخشی از بوم را پاک می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

ناحیه پاک‌شده به شکل مستطیل است که گوشه بالا-چپ آن در (10, 10) قرار دارد. این ناحیه دارای عرض 120 و ارتفاع 100 است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Draw yellow background
ctx.beginPath();
ctx.fillStyle = "#ffff66";
ctx.fillRect(0, 0, canvas.width, canvas.height);

// Draw blue triangle
ctx.beginPath();
ctx.fillStyle = "blue";
ctx.moveTo(20, 20);
ctx.lineTo(180, 20);
ctx.lineTo(130, 130);
ctx.closePath();
ctx.fill();

// Clear part of the canvas
ctx.clearRect(10, 10, 120, 100);
```

#### Result

{{EmbedLiveSample('Erasing_part_of_a_canvas', 700, 180)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.fillRect()")}}
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}