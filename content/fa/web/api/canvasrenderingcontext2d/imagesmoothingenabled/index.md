---
title: "CanvasRenderingContext2D: imageSmoothingEnabled property"
short-title: imageSmoothingEnabled
slug: Web/API/CanvasRenderingContext2D/imageSmoothingEnabled
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.imageSmoothingEnabled
---

{{APIRef("Canvas API")}}

خاصیت **`imageSmoothingEnabled`** از رابط {{domxref("CanvasRenderingContext2D")}} که بخشی از [Canvas API](/en-US/docs/Web/API/Canvas_API) است، تعیین می‌کند که آیا تصاویر مقیاس‌شده هموار (smooth) شوند (`true`، پیش‌فرض) یا خیر (`false`). هنگام خواندن خاصیت `imageSmoothingEnabled`، آخرین مقداری که به آن اختصاص داده شده است بازگردانده می‌شود.

این خاصیت برای بازی‌ها و سایر برنامه‌هایی که از پیکسل‌آرت (pixel art) استفاده می‌کنند مفید است. هنگام بزرگ کردن تصاویر، الگوریتم پیش‌فرض تغییر اندازه، پیکسل‌ها را تار می‌کند. این خاصیت را روی `false` تنظیم کنید تا وضوح پیکسل‌ها حفظ شود.

> [!NOTE]
> می‌توانید کیفیت هموارسازی را با خاصیت
> {{domxref("CanvasRenderingContext2D.imageSmoothingQuality", "imageSmoothingQuality")}}
> تنظیم کنید.

## Value

یک مقدار بولی (boolean) که نشان می‌دهد تصاویر مقیاس‌شده هموار شوند یا نه. مقدار پیش‌فرض `true` است.

## Examples

### غیرفعال کردن هموارسازی تصویر

این مثال سه تصویر را مقایسه می‌کند. تصویر اول در اندازه طبیعی خود رسم می‌شود، تصویر دوم با مقیاس ۳ برابر و با فعال بودن هموارسازی تصویر رسم می‌شود، و تصویر سوم نیز با مقیاس ۳ برابر اما با غیرفعال بودن هموارسازی تصویر رسم می‌شود.

#### HTML

```html
<canvas id="canvas" width="460" height="210"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");

const ctx = canvas.getContext("2d");
ctx.font = "16px sans-serif";
ctx.textAlign = "center";

const img = new Image();
img.src = "/shared-assets/images/examples/big-star.png";
img.onload = () => {
  const w = img.width,
    h = img.height;

  ctx.fillText("Source", w * 0.5, 20);
  ctx.drawImage(img, 0, 24, w, h);

  ctx.fillText("Smoothing = TRUE", w * 2.5, 20);
  ctx.imageSmoothingEnabled = true;
  ctx.drawImage(img, w, 24, w * 3, h * 3);

  ctx.fillText("Smoothing = FALSE", w * 5.5, 20);
  ctx.imageSmoothingEnabled = false;
  ctx.drawImage(img, w * 4, 24, w * 3, h * 3);
};
```

#### Result

{{ EmbedLiveSample('Disabling_image_smoothing', 700, 240) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The interface defining this property: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.imageSmoothingQuality")}}
- {{cssxref("image-rendering")}}