---
title: "CanvasRenderingContext2D: closePath() method"
short-title: closePath()
slug: Web/API/CanvasRenderingContext2D/closePath
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.closePath
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.closePath()`** از Canvas 2D API تلاش می‌کند یک خط مستقیم از نقطهٔ کنونی به آغاز زیرمسیر کنونی اضافه کند. اگر شکل از قبل بسته شده باشد یا فقط یک نقطه داشته باشد، این تابع هیچ کاری انجام نمی‌دهد.

این متد مستقیماً چیزی روی بوم رسم نمی‌کند. می‌توانید مسیر را با استفاده از متدهای {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} یا {{domxref("CanvasRenderingContext2D.fill()", "fill()")}} رندر کنید.

## Syntax

```js-nolint
closePath()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### Closing a triangle

این مثال دو ضلع نخست (مورب) یک مثلث را با استفاده از متد `lineTo()` می‌سازد. پس از آن، قاعدهٔ مثلث با متد `closePath()` ایجاد می‌شود که به‌طور خودکار نخستین و آخرین نقطهٔ شکل را به یکدیگر متصل می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

گوشه‌های مثلث در نقاط (20, 140)، (120, 10) و (220, 140) قرار دارند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.moveTo(20, 140); // Move pen to bottom-left corner
ctx.lineTo(120, 10); // Line to top corner
ctx.lineTo(220, 140); // Line to bottom-right corner
ctx.closePath(); // Line to bottom-left corner
ctx.stroke();
```

#### Result

{{ EmbedLiveSample('Closing_a_triangle', 700, 180) }}

### Closing just one sub-path

این مثال یک شکلک خندان (smiley face) شامل سه زیرمسیر نامتصل را رسم می‌کند.

> [!NOTE]
> اگرچه `closePath()` پس از ایجاد همهٔ کمان‌ها فراخوانی می‌شود، فقط آخرین کمان (زیرمسیر) بسته می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

دو کمان نخست چشم‌های صورت را می‌سازند. آخرین کمان دهان را می‌سازد.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.arc(240, 20, 40, 0, Math.PI);
ctx.moveTo(100, 20);
ctx.arc(60, 20, 40, 0, Math.PI);
ctx.moveTo(215, 80);
ctx.arc(150, 80, 65, 0, Math.PI);
ctx.closePath();
ctx.lineWidth = 6;
ctx.stroke();
```

#### Result

{{ EmbedLiveSample('Closing_just_one_sub-path', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.beginPath()")}}