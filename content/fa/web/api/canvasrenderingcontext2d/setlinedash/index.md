---
title: "CanvasRenderingContext2D: setLineDash() method"
short-title: setLineDash()
slug: Web/API/CanvasRenderingContext2D/setLineDash
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.setLineDash
---

{{APIRef("Canvas API")}}

متد **`setLineDash()`** از رابط {{domxref("CanvasRenderingContext2D")}} در API Canvas 2D، الگوی خط‌چین را برای ترسیم خطوط تنظیم می‌کند. این متد از آرایه‌ای از مقادیر استفاده می‌کند که طول‌های متناوب خطوط و فاصله‌های خالی را مشخص می‌کنند و الگو را توصیف می‌نماید.

> [!NOTE]
> برای بازگشت به خطوط توپر، لیست خط‌چین را روی یک آرایه خالی تنظیم کنید.

## Syntax

```js-nolint
setLineDash(segments)
```

### Parameters

- `segments`
  - : یک {{jsxref("Array")}} از اعداد که فاصله‌ها را برای ترسیم متناوب یک خط و یک فاصله خالی مشخص می‌کند (بر حسب واحد فضای مختصات). اگر تعداد عناصر آرایه فرد باشد، عناصر آرایه کپی و به هم الحاق می‌شوند. به عنوان مثال، `[5, 15, 25]` به `[5, 15, 25, 5, 15, 25]` تبدیل می‌شود. اگر آرایه خالی باشد، لیست خط‌چین پاک می‌شود و خطوط به حالت توپر بازمی‌گردند.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### مثال پایه

این مثال از متد `setLineDash()` برای رسم یک خط چین بالای یک خط توپر استفاده می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// خط چین
ctx.beginPath();
ctx.setLineDash([5, 15]);
ctx.moveTo(0, 50);
ctx.lineTo(300, 50);
ctx.stroke();

// خط توپر
ctx.beginPath();
ctx.setLineDash([]);
ctx.moveTo(0, 100);
ctx.lineTo(300, 100);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Basic_example', 700, 180) }}

### چند الگوی رایج

این مثال انواع مختلفی از الگوهای رایج خط‌چین را نشان می‌دهد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

تابع `drawDashedLine()` که در زیر ساخته شده است، رسم چندین خط چین را ساده می‌کند. این تابع یک آرایه الگو را به عنوان تنها پارامتر خود دریافت می‌کند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let y = 15;

function drawDashedLine(pattern) {
  ctx.beginPath();
  ctx.setLineDash(pattern);
  ctx.moveTo(0, y);
  ctx.lineTo(300, y);
  ctx.stroke();
  y += 20;
}

drawDashedLine([]);
drawDashedLine([1, 1]);
drawDashedLine([10, 10]);
drawDashedLine([20, 5]);
drawDashedLine([15, 3, 3, 3]);
drawDashedLine([20, 3, 3, 3, 3, 3, 3, 3]);
drawDashedLine([12, 3, 3]); // برابر است با [12, 3, 3, 12, 3, 3]
```

#### نتیجه

{{ EmbedLiveSample('Some_common_patterns', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.getLineDash()")}}
- {{domxref("CanvasRenderingContext2D.lineDashOffset")}}