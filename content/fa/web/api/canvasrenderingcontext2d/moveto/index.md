---
title: "CanvasRenderingContext2D: moveTo() method"
short-title: moveTo()
slug: Web/API/CanvasRenderingContext2D/moveTo
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.moveTo
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.moveTo()`**
در Canvas 2D API یک زیرمسیر جدید را در نقطه‌ای که با مختصات
`(x, y)` مشخص شده آغاز می‌کند.

## Syntax

```js-nolint
moveTo(x, y)
```

### Parameters

- `x`
  - : مختصات نقطه در محور x (افقی).
- `y`
  - : مختصات نقطه در محور y (عمودی).

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### ایجاد چند زیرمسیر

این مثال از `moveTo()` برای ایجاد دو زیرمسیر در یک مسیر واحد استفاده می‌کند.
هر دو زیرمسیر سپس با یک فراخوانی `stroke()` ترسیم می‌شوند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

خط اول از (50, 50) شروع شده و به (200, 50) ختم می‌شود. خط دوم از (50,
90\) شروع شده و به (280, 120) ختم می‌شود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.moveTo(50, 50); // Begin first sub-path
ctx.lineTo(200, 50);
ctx.moveTo(50, 90); // Begin second sub-path
ctx.lineTo(280, 120);
ctx.stroke();
```

#### Result

{{ EmbedLiveSample('Creating_multiple_sub-paths', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.lineTo()")}}
- {{domxref("CanvasRenderingContext2D.stroke()")}}