---
title: "CanvasRenderingContext2D: getLineDash() method"
short-title: getLineDash()
slug: Web/API/CanvasRenderingContext2D/getLineDash
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.getLineDash
---

{{APIRef("Canvas API")}}

متد **`getLineDash()`** در رابط {{domxref("CanvasRenderingContext2D")}} مربوط به Canvas 2D API، الگوی خط‌چین فعلی را برمی‌گرداند.

## Syntax

```js-nolint
getLineDash()
```

### Parameters

هیچ.

### Return value

یک {{jsxref("Array")}} از اعداد که فاصله‌ها را برای رسم متناوب خط و فاصله (بر حسب واحد فضای مختصات) مشخص می‌کند. اگر تعداد عناصر، هنگام تنظیم، فرد باشد، عناصر آرایه کپی و به هم الحاق می‌شوند. برای مثال، تنظیم خط‌چین روی
`[5, 15, 25]` باعث می‌شود که مقدار بازگشتی
`[5, 15, 25, 5, 15, 25]` باشد.

## Examples

### دریافت تنظیمات فعلی خط‌چین

این مثال متد `getLineDash()` را نشان می‌دهد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

همان‌طور که توسط {{domxref("CanvasRenderingContext2D.setLineDash()", "setLineDash()")}} تنظیم شده، ضربه‌های قلم شامل خطوطی به عرض ۱۰ واحد هستند که بین هر خط، فاصله‌ای به اندازه ۲۰ واحد وجود دارد.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.setLineDash([10, 20]);
console.log(ctx.getLineDash()); // [10, 20]

// Draw a dashed line
ctx.beginPath();
ctx.moveTo(0, 50);
ctx.lineTo(300, 50);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Getting_the_current_line_dash_setting', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.setLineDash()")}}
- {{domxref("CanvasRenderingContext2D.lineDashOffset")}}