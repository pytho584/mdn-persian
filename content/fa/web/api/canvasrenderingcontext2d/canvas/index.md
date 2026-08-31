---
title: "CanvasRenderingContext2D: canvas property"
short-title: canvas
slug: Web/API/CanvasRenderingContext2D/canvas
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.canvas
---

{{APIRef("Canvas API")}}

خاصیت **`CanvasRenderingContext2D.canvas`**، بخشی از [Canvas API](/en-US/docs/Web/API/Canvas_API)، یک ارجاع فقط‌خواندنی به شیء {{domxref("HTMLCanvasElement")}} است که با یک بافتار (context) مشخص مرتبط است.

## مقدار

یک شیء {{domxref("HTMLCanvasElement")}}.

## مثال‌ها

با توجه به این عنصر {{HTMLElement("canvas")}}:

```html
<canvas id="canvas"></canvas>
```

… می‌توانید با استفاده از خاصیت `canvas`، یک ارجاع به عنصر `canvas` درون `CanvasRenderingContext2D` دریافت کنید:

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.canvas; // HTMLCanvasElement
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("CanvasRenderingContext2D")}}
- [Canvas API](/en-US/docs/Web/API/Canvas_API)