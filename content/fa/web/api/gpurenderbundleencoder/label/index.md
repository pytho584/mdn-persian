---
title: "GPURenderBundleEncoder: label property"
short-title: label
slug: Web/API/GPURenderBundleEncoder/label
page-type: web-api-instance-property
browser-compat: api.GPURenderBundleEncoder.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`label`** از رابط {{domxref("GPURenderBundleEncoder")}} یک رشته (string) است که برچسبی را برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا اخطارهای کنسول.

این برچسب را می‌توان با ارائه یک ویژگی `label` در شیء توصیف‌کننده‌ای که به فراخوانی مبدأ {{domxref("GPUDevice.createRenderBundleEncoder()")}} داده می‌شود تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPURenderBundleEncoder` دریافت و تنظیم کنید.

> [!NOTE]
> این ویژگی از نظر عملکردی با معادل خود در {{domxref("GPURenderPassEncoder")}} — {{domxref("GPURenderPassEncoder.label", "label")}} یکسان است.

## مقدار

یک رشته. اگر قبلاً هیچ مقدار برچسبی تنظیم نشده باشد، دریافت برچسب یک رشته خالی برمی‌گرداند.

## مثال‌ها

تنظیم و دریافت یک برچسب از طریق `GPURenderBundleEncoder.label`:

```js
const renderBundleEncoder = device.createRenderBundleEncoder({
  colorFormats: [presentationFormat],
});

renderBundleEncoder.label = "my_render_bundle_encoder";
console.log(renderBundleEncoder.label); // "my_render_bundle_encoder"
```

تنظیم یک برچسب از طریق فراخوانی مبدأ {{domxref("GPUDevice.createRenderBundleEncoder()")}} و سپس دریافت آن از طریق `GPURenderBundleEncoder.label`:

```js
const renderBundleEncoder = device.createRenderBundleEncoder({
  colorFormats: [presentationFormat],
  label: "my_render_bundle_encoder",
});

console.log(renderBundleEncoder.label); // "my_render_bundle_encoder"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)