---
title: "OffscreenCanvas: OffscreenCanvas() constructor"
short-title: OffscreenCanvas()
slug: Web/API/OffscreenCanvas/OffscreenCanvas
page-type: web-api-constructor
browser-compat: api.OffscreenCanvas.OffscreenCanvas
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

سازنده **`OffscreenCanvas()`** یک شیء {{domxref("OffscreenCanvas")}} تازه نمونه‌سازی‌شده را برمی‌گرداند.

## نحو (Syntax)

```js-nolint
new OffscreenCanvas(width, height)
```

### پارامترها

- `width`
  - : عرض بوم خارج از صفحه (offscreen canvas).
- `height`
  - : ارتفاع بوم خارج از صفحه.

## مثال‌ها

این مثال یک بوم خارج از صفحه جدید با استفاده از سازنده `OffscreenCanvas()` ایجاد می‌کند. سپس با استفاده از متد {{domxref("OffscreenCanvas.getContext()", "getContext()")}} یک زمینه [WebGL](/en-US/docs/Web/API/WebGL_API) روی آن مقداردهی اولیه می‌کنیم.

```js
const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("OffscreenCanvas")}}، رابطی که این سازنده به آن تعلق دارد.