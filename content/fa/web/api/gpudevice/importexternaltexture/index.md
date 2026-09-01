---
title: "GPUDevice: importExternalTexture() method"
short-title: importExternalTexture()
slug: Web/API/GPUDevice/importExternalTexture
page-type: web-api-instance-method
browser-compat: api.GPUDevice.importExternalTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`importExternalTexture()`** در رابط {{domxref("GPUDevice")}} یک شیء {{domxref("HTMLVideoElement")}} یا {{domxref("VideoFrame")}} را به عنوان ورودی می‌گیرد و یک شیء wrapper به نام {{domxref("GPUExternalTexture")}} برمی‌گرداند که شامل یک عکس فوری (snapshot) از ویدیو است و می‌تواند به عنوان یک فریم در عملیات رندر GPU استفاده شود.

## Syntax

```js-nolint
importExternalTexture(descriptor)
```

### Parameters

- `descriptor`
  - : یک شیء شامل ویژگی‌های زیر:
    - `colorSpace` {{optional_inline}}
      - : یک مقدار شمارشی (enumerated) که فضای رنگی مورد استفاده برای فریم ویدیو را مشخص می‌کند. مقادیر ممکن عبارت‌اند از `"srgb"` و `"display-p3"`. اگر حذف شود، `colorSpace` به صورت پیش‌فرض روی `"srgb"` قرار می‌گیرد.
    - `label` {{optional_inline}}
      - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `source`
      - : منبع {{domxref("HTMLVideoElement")}} یا {{domxref("VideoFrame")}} برای عکس فوری ویدیو.

### Return value

یک نمونه از شیء {{domxref("GPUExternalTexture")}}.

توجه داشته باشید که لحظه‌ای که شیء {{domxref("GPUExternalTexture")}} منقضی می‌شود (از بین می‌رود) به منبع آن بستگی دارد:

- اشیاء {{domxref("GPUExternalTexture")}} با منبع {{domxref("HTMLVideoElement")}} به محض استفاده (مثلاً در یک bind group) منقضی می‌شوند.
- اشیاء {{domxref("GPUExternalTexture")}} با منبع {{domxref("VideoFrame")}} فقط زمانی منقضی می‌شوند که `VideoFrame` بسته شود، مثلاً از طریق فراخوانی {{domxref("VideoFrame.close()")}}.

### Validation

برای فراخوانی **`importExternalTexture()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و یک شیء نامعتبر {{domxref("GPUExternalTexture")}} برگردانده می‌شود:

- عکس فوری ویدیو قابل استفاده باشد (مثلاً منبع ویدیو به درستی بارگذاری شده باشد و عرض یا ارتفاع آن ۰ نباشد).

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : اگر داده‌های منبع ویدیو از مبدأ متقاطع (cross-origin) باشند، پرتاب می‌شود.

## Examples

در نمونه‌های WebGPU، [نمونه آپلود ویدیو](https://webgpu.github.io/webgpu-samples/samples/videoUploading/)، از فراخوانی `importExternalTexture()` به عنوان مقدار یک ورودی bind group به نام `resource` استفاده شده است که هنگام ایجاد یک {{domxref("GPUBindGroup")}} از طریق فراخوانی {{domxref("GPUDevice.createBindGroup()")}} مشخص می‌شود:

```js
// …

const uniformBindGroup = device.createBindGroup({
  layout: pipeline.getBindGroupLayout(0),
  entries: [
    {
      binding: 1,
      resource: sampler,
    },
    {
      binding: 2,
      resource: device.importExternalTexture({
        source: video,
      }),
    },
  ],
});

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)