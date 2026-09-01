---
title: "HTMLCanvasElement: transferControlToOffscreen() method"
short-title: transferControlToOffscreen()
slug: Web/API/HTMLCanvasElement/transferControlToOffscreen
page-type: web-api-instance-method
browser-compat: api.HTMLCanvasElement.transferControlToOffscreen
---

{{APIRef("Canvas API")}}

متد **`HTMLCanvasElement.transferControlToOffscreen()`** کنترل را به یک شیء {{domxref("OffscreenCanvas")}} منتقل می‌کند، چه در ترد اصلی و چه در یک worker.

## Syntax

```js-nolint
transferControlToOffscreen()
```

### Parameters

هیچ.

### Return value

یک شیء {{domxref("OffscreenCanvas")}}.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - برای بوم (canvas) با فراخوانی {{domxref("HTMLCanvasElement.getContext()")}} یک حالت زمینه (context mode) تنظیم شده باشد.
    - کنترل بوم قبلاً به حالت آف‌اسکرین منتقل شده باشد.

## Examples

مثال زیر نحوه انتقال کنترل به یک شیء {{domxref("OffscreenCanvas")}} را در ترد اصلی نشان می‌دهد.

```js
const htmlCanvas = document.createElement("canvas");
const offscreen = htmlCanvas.transferControlToOffscreen();
const gl = offscreen.getContext("webgl");

// Some drawing using the gl context…
```

مثال زیر نحوه انتقال کنترل به یک شیء {{domxref("OffscreenCanvas")}} را در یک worker نشان می‌دهد.

```js
const offscreen = document.querySelector("canvas").transferControlToOffscreen();
const worker = new Worker("my-worker-url.js");
worker.postMessage({ canvas: offscreen }, [offscreen]);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The interface defining this method, {{domxref("HTMLCanvasElement")}}
- {{domxref("OffscreenCanvas")}}