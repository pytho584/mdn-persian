---
title: "GPURenderPassEncoder: setScissorRect() method"
short-title: setScissorRect()
slug: Web/API/GPURenderPassEncoder/setScissorRect
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setScissorRect
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setScissorRect()`** از رابط {{domxref("GPURenderPassEncoder")}} مستطیل برش (scissor rectangle) مورد استفاده در مرحله راستری‌سازی را تنظیم می‌کند. پس از تبدیل به مختصات viewport، هر قطعه‌ای که خارج از مستطیل برش قرار گیرد، دور انداخته می‌شود.

## Syntax

```js-nolint
setScissorRect(x, y, width, height)
```

### Parameters

- `x`
  - : عددی که نشان‌دهنده حداقل مقدار X مستطیل برش، بر حسب پیکسل است.
- `y`
  - : عددی که نشان‌دهنده حداقل مقدار Y مستطیل برش، بر حسب پیکسل است.
- `width`
  - : عددی که نشان‌دهنده عرض مستطیل برش، بر حسب پیکسل است.
- `height`
  - : عددی که نشان‌دهنده ارتفاع مستطیل برش، بر حسب پیکسل است.

> [!NOTE]
> اگر فراخوانی `setScissorRect()` انجام نشود، مقادیر پیش‌فرض برای هر رندر پاس `(0, 0, عرض attachment, ارتفاع attachment)` خواهد بود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Validation

معیارهای زیر باید هنگام فراخوانی **`setViewport()`** رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- `x` + `width` کمتر یا مساوی عرض attachment‌های رندر رندر پاس است (به یادداشت زیر مراجعه کنید).
- `y` + `height` کمتر یا مساوی ارتفاع attachment‌های رندر رندر پاس است (به یادداشت زیر مراجعه کنید).

> [!NOTE]
> به attachment‌های رنگ و عمق/استنسیل مشخص‌شده در توصیف‌گر {{domxref("GPUCommandEncoder.beginRenderPass()")}} مراجعه کنید؛ عرض و ارتفاع بر اساس عرض و ارتفاع {{domxref("GPUTexture")}}ای است که `view`های آن از آن منشأ می‌گیرند.

## Examples

### مثال پایه

در یک رندر معمولی canvas، می‌توان از کد زیر برای دور انداختن هر رندرگیری خارج از ربع بالا-چپ canvas استفاده کرد:

```js
passEncoder.setScissorRect(0, 0, canvas.width / 2, canvas.height / 2);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)