---
title: "GPU: getPreferredCanvasFormat() method"
short-title: getPreferredCanvasFormat()
slug: Web/API/GPU/getPreferredCanvasFormat
page-type: web-api-instance-method
browser-compat: api.GPU.getPreferredCanvasFormat
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getPreferredCanvasFormat()`** از رابط {{domxref("GPU")}} فرمت بهینه بافت canvas را برای نمایش محتوای 8 بیتی با عمق رنگ استاندارد (standard dynamic range) در سیستم فعلی بازمی‌گرداند.

این متد معمولاً برای ارائه‌ی مقدار بهینه‌ی `format` به فراخوانی {{domxref("GPUCanvasContext.configure()")}} استفاده می‌شود. این کار توصیه می‌شود — اگر هنگام پیکربندی بافت canvas از فرمت ترجیحی استفاده نکنید، ممکن است سربار اضافی مانند کپی‌های اضافی بافت بر اساس پلتفرم متحمل شوید.

## Syntax

```js-nolint
getPreferredCanvasFormat()
```

### Parameters

هیچ.

### Return value

یک رشته که فرمت بافت canvas را مشخص می‌کند. مقدار می‌تواند `rgba8unorm` یا `bgra8unorm` باشد.

### Exceptions

هیچ.

## Examples

```js
const canvas = document.querySelector("#gpuCanvas");
const context = canvas.getContext("webgpu");

context.configure({
  device,
  format: navigator.gpu.getPreferredCanvasFormat(),
  alphaMode: "premultiplied",
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)