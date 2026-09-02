---
title: "ImageBitmapRenderingContext: canvas property"
---

---
title: "ImageBitmapRenderingContext: canvas property"
short-title: canvas
slug: Web/API/ImageBitmapRenderingContext/canvas
page-type: web-api-instance-property
browser-compat: api.ImageBitmapRenderingContext.canvas
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

ویژگی **`ImageBitmapRenderingContext.canvas`** که بخشی از [Canvas API](/en-US/docs/Web/API/Canvas_API) است، یک ارجاع فقط‌خواندنی به شیء {{domxref("HTMLCanvasElement")}} یا {{domxref("OffscreenCanvas")}} است که با context مورد نظر مرتبط است.

## مقدار

یک شیء {{domxref("HTMLCanvasElement")}} یا {{domxref("OffscreenCanvas")}}.

## مثال‌ها

این عنصر {{HTMLElement("canvas")}} را در نظر بگیرید:

```html
<canvas id="canvas"></canvas>
```

با استفاده از ویژگی `canvas`، می‌توانید ارجاعی به عنصر canvas را از طریق `ImageBitmapRenderingContext` به‌دست آورید:

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("bitmaprenderer");
console.log(ctx.canvas === canvas); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("ImageBitmapRenderingContext")}}
- [Canvas API](/en-US/docs/Web/API/Canvas_API)