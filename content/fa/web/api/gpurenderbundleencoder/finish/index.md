---
title: "GPURenderBundleEncoder: finish() method"
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`finish()`** از واسط {{domxref("GPURenderBundleEncoder")}}، ثبت توالی دستورات بسته رندر جاری را کامل می‌کند و یک شیء {{domxref("GPURenderBundle")}} برمی‌گرداند که می‌تواند در فراخوانی {{domxref("GPURenderPassEncoder.executeBundles()")}} برای اجرای آن دستورات در یک پاس رندر خاص استفاده شود.

## Syntax

```js-nolint
finish(descriptor)
```

### پارامترها

- `descriptor` {{optional_inline}}
  - : یک شیء حاوی ویژگی‌های زیر:
    - `label` {{optional_inline}}
      - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("GPURenderBundle")}}.

### اعتبارسنجی

هنگام فراخوانی **`finish()`**، معیارهای زیر باید رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderBundleEncoder")}} نامعتبر می‌شود:

- {{domxref("GPURenderBundleEncoder")}} باز است (یعنی قبلاً با یک فراخوانی `finish()` پایان نیافته است).
- پشته اشکال‌زدایی برای پاس رندر جاری خالی است (یعنی هیچ گروه اشکال‌زدایی پاس رندر در حال حاضر باز نیست، همانطور که توسط {{domxref("GPURenderBundleEncoder.pushDebugGroup", "pushDebugGroup()")}} باز شده است).

## مثال‌ها

```js
const renderBundleEncoder = device.createRenderBundleEncoder({
  colorFormats: [presentationFormat],
});
recordRenderPass(renderBundleEncoder);
const renderBundle = renderBundleEncoder.finish();
```

قطعه کد بالا از نمونه WebGPU Samples [Animometer example](https://webgpu.github.io/webgpu-samples/samples/animometer/) گرفته شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)