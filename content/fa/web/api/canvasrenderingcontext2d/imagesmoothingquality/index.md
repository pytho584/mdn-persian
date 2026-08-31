---
title: "CanvasRenderingContext2D: imageSmoothingQuality property"
short-title: imageSmoothingQuality
slug: Web/API/CanvasRenderingContext2D/imageSmoothingQuality
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.imageSmoothingQuality
---

{{APIRef("Canvas API")}}

خاصیت **`imageSmoothingQuality`** در رابط {{domxref("CanvasRenderingContext2D")}}، که بخشی از [Canvas API](/en-US/docs/Web/API/Canvas_API) است، به شما امکان می‌دهد کیفیت نرم‌سازی تصویر را تنظیم کنید.

> [!NOTE]
> برای اینکه این خاصیت اثر داشته باشد، باید {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled", "imageSmoothingEnabled")}} برابر با `true` باشد.

## مقدار

یکی از مقادیر زیر:

- `"low"`
  - : کیفیت پایین.
- `"medium"`
  - : کیفیت متوسط.
- `"high"`
  - : کیفیت بالا.

مقدار پیش‌فرض `"low"` است.

## مثال‌ها

### تنظیم کیفیت نرم‌سازی تصویر

این مثال از خاصیت `imageSmoothingQuality` همراه با یک تصویر تغییر اندازه‌داده‌شده استفاده می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

let img = new Image();
img.src = "canvas_create_pattern.png";
img.onload = () => {
  ctx.imageSmoothingQuality = "low";
  ctx.drawImage(img, 0, 0, 300, 150);
};
```

#### نتیجه

{{ EmbedLiveSample('Setting_image_smoothing_quality', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این خاصیت: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled")}}
- {{cssxref("image-rendering")}}