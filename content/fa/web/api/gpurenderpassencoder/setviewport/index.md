---
title: "GPURenderPassEncoder: setViewport() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/GPURenderPassEncoder/setViewport"
---

---
title: "GPURenderPassEncoder: setViewport() method"
short-title: setViewport()
slug: Web/API/GPURenderPassEncoder/setViewport
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setViewport
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setViewport()`** در رابط {{domxref("GPURenderPassEncoder")}}، نمای دید (viewport) مورد استفاده در مرحلهٔ رasterization را برای نگاشت خطی از مختصات دستگاه نرمال‌شده به مختصات نمای دید تنظیم می‌کند.

## Syntax

```js-nolint
setViewport(x, y, width, height, minDepth, maxDepth)
```

### Parameters

- `x`
  - : عددی که کمینه مقدار X نمای دید را بر حسب پیکسل نشان می‌دهد.
- `y`
  - : عددی که کمینه مقدار Y نمای دید را بر حسب پیکسل نشان می‌دهد.
- `width`
  - : عددی که عرض نمای دید را بر حسب پیکسل نشان می‌دهد.
- `height`
  - : عددی که ارتفاع نمای دید را بر حسب پیکسل نشان می‌دهد.
- `minDepth`
  - : عددی که کمینه مقدار عمق نمای دید را نشان می‌دهد.
- `maxDepth`
  - : عددی که بیشینه مقدار عمق نمای دید را نشان می‌دهد.

> [!NOTE]
> اگر فراخوانی `setViewport()` انجام نشود، مقادیر پیش‌فرض برای هر پاس رندر `(0, 0, عرض پیوست, ارتفاع پیوست, 0, 1)` خواهد بود.

### Return value

هیچ ({{jsxref("undefined")}}).

### Validation

برای فراخوانی **`setViewport()`** باید معیارهای زیر برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPassEncoder")}} نامعتبر می‌شود:

- `x`، `y`، `width` و `height` همگی بزرگ‌تر یا مساوی ۰ هستند.
- `x` + `width` کمتر یا مساوی عرض پیوست‌های رندر پاس رندر است (به یادداشت زیر مراجعه کنید).
- `y` + `height` کمتر یا مساوی ارتفاع پیوست‌های رندر پاس رندر است (به یادداشت زیر مراجعه کنید).
- `minDepth` و `maxDepth` هر دو در بازه ۰٫۰ تا ۱٫۰ شامل قرار دارند.
- `minDepth` کوچک‌تر از `maxDepth` است.

> [!NOTE]
> به پیوست‌های رنگ و عمق/استنسیل مشخص‌شده در توصیفگر {{domxref("GPUCommandEncoder.beginRenderPass()")}} مراجعه کنید؛ عرض و ارتفاع بر اساس {{domxref("GPUTexture")}}ای که `view`های آن‌ها از آن منشأ می‌گیرند تعیین می‌شود.

## Examples

### Basic snippet

در یک رندر معمولی روی بوم (canvas)، می‌توان از کد زیر برای نصف کردن عرض و ارتفاع گرافیک رندر شده استفاده کرد:

```js
passEncoder.setViewport(0, 0, canvas.width / 2, canvas.height / 2, 0, 1);
```

### In context

در نمونه‌های WebGPU، در مثال [reversedZ](https://webgpu.github.io/webgpu-samples/samples/reversedZ/)، از `setViewport` چندین بار برای تنظیم نمای دید در پاس‌های رندر مختلف استفاده شده است. برای مشاهدهٔ کامل زمینه، فهرست کد مثال را مطالعه کنید.

مثلاً:

```js
// …

colorPass.setViewport(
  (canvas.width * m) / 2,
  0,
  canvas.width / 2,
  canvas.height,
  0,
  1,
);

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)