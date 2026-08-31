---
title: "CanvasRenderingContext2D: lineTo() method"
short-title: lineTo()
slug: Web/API/CanvasRenderingContext2D/lineTo
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.lineTo
---

{{APIRef("Canvas API")}}

متد **`lineTo()`** از {{domxref("CanvasRenderingContext2D")}} که بخشی از Canvas 2D API است، یک خط مستقیم به زیرمسیر (sub-path) فعلی اضافه می‌کند و آخرین نقطهٔ زیرمسیر را به مختصات `(x, y)` مشخص‌شده متصل می‌نماید.

مانند سایر متدهایی که مسیر فعلی را تغییر می‌دهند، این متد مستقیماً چیزی را رندر نمی‌کند. برای رسم مسیر روی یک بوم (canvas)، می‌توانید از متدهای {{domxref("CanvasRenderingContext2D.fill", "fill()")}} یا {{domxref("CanvasRenderingContext2D.stroke", "stroke()")}} استفاده کنید.

## Syntax

```js-nolint
lineTo(x, y)
```

### Parameters

- `x`
  - : مختصات محور x نقطهٔ انتهای خط.
- `y`
  - : مختصات محور y نقطهٔ انتهای خط.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

### رسم یک خط مستقیم

این مثال با استفاده از متد `lineTo()` یک خط مستقیم رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

خط از (30, 50) شروع و به (150, 100) ختم می‌شود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath(); // شروع یک مسیر جدید
ctx.moveTo(30, 50); // حرکت قلم به (30, 50)
ctx.lineTo(150, 100); // رسم یک خط به (150, 100)
ctx.stroke(); // رندر کردن مسیر
```

#### Result

{{ EmbedLiveSample('Drawing_a_straight_line', 700, 180) }}

### رسم خطوط متصل

هر بار که `lineTo()` (و متدهای مشابه) فراخوانی می‌شود، به‌طور خودکار به زیرمسیر فعلی اضافه می‌گردد، به این معنی که همهٔ خطوط با هم stroke یا fill می‌شوند. این مثال حرف 'M' را با یک خط پیوسته رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.moveTo(90, 130);
ctx.lineTo(95, 25);
ctx.lineTo(150, 80);
ctx.lineTo(205, 25);
ctx.lineTo(210, 130);
ctx.lineWidth = 15;
ctx.stroke();
```

#### Result

{{ EmbedLiveSample('Drawing_connected_lines', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- واسط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.moveTo()")}}
- {{domxref("CanvasRenderingContext2D.stroke()")}}