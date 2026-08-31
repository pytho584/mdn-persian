---
title: "CanvasRenderingContext2D: save() method"
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.save()`** از Canvas 2D API، کل وضعیت بوم (canvas) را با افزودن وضعیت فعلی به یک پشته (stack) ذخیره می‌کند.

## Syntax

```js-nolint
save()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Description

وضعیت ترسیم که روی یک پشته ذخیره می‌شود شامل موارد زیر است:

- ماتریس تبدیل فعلی.
- ناحیه برش فعلی.
- فهرست خط‌چین فعلی.
- مقادیر فعلی ویژگی‌های زیر:
  - {{domxref("CanvasRenderingContext2D.direction", "direction")}}
  - {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}}
  - {{domxref("CanvasRenderingContext2D.filter", "filter")}}
  - {{domxref("CanvasRenderingContext2D.font", "font")}}
  - {{domxref("CanvasRenderingContext2D.fontKerning", "fontKerning")}}
  - {{domxref("CanvasRenderingContext2D.fontStretch", "fontStretch")}}
  - {{domxref("CanvasRenderingContext2D.fontVariantCaps", "fontVariantCaps")}}
  - {{domxref("CanvasRenderingContext2D.globalAlpha", "globalAlpha")}}
  - {{domxref("CanvasRenderingContext2D.globalCompositeOperation", "globalCompositeOperation")}}
  - {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled", "imageSmoothingEnabled")}}
  - {{domxref("CanvasRenderingContext2D.imageSmoothingQuality", "imageSmoothingQuality")}}
  - {{domxref("CanvasRenderingContext2D.letterSpacing", "letterSpacing")}}
  - {{domxref("CanvasRenderingContext2D.lineCap", "lineCap")}}
  - {{domxref("CanvasRenderingContext2D.lineDashOffset", "lineDashOffset")}}
  - {{domxref("CanvasRenderingContext2D.lineJoin", "lineJoin")}}
  - {{domxref("CanvasRenderingContext2D.lineWidth", "lineWidth")}}
  - {{domxref("CanvasRenderingContext2D.miterLimit", "miterLimit")}}
  - {{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}}
  - {{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor")}}
  - {{domxref("CanvasRenderingContext2D.shadowOffsetX", "shadowOffsetX")}}
  - {{domxref("CanvasRenderingContext2D.shadowOffsetY", "shadowOffsetY")}}
  - {{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle")}}
  - {{domxref("CanvasRenderingContext2D.textAlign", "textAlign")}}
  - {{domxref("CanvasRenderingContext2D.textBaseline", "textBaseline")}}
  - {{domxref("CanvasRenderingContext2D.textRendering", "textRendering")}}
  - {{domxref("CanvasRenderingContext2D.wordSpacing", "wordSpacing")}}

## Examples

### ذخیره وضعیت ترسیم

این مثال از متد `save()` برای ذخیره وضعیت فعلی و از `restore()` برای بازگردانی آن بعداً استفاده می‌کند، تا بتوانید بعداً یک مستطیل با وضعیت فعلی رسم کنید.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Save the current state
ctx.save();

ctx.fillStyle = "green";
ctx.fillRect(10, 10, 100, 100);

// Restore to the state saved by the most recent call to save()
ctx.restore();

ctx.fillRect(150, 40, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Saving_the_drawing_state', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The interface defining this method: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.restore()")}}