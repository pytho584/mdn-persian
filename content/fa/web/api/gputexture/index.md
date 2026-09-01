---
title: "GPUTexture"
---

---
title: GPUTexture
slug: Web/API/GPUTexture
page-type: web-api-interface
browser-compat: api.GPUTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابطهٔ **`GPUTexture`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} نمایانگر یک ظرف برای ذخیرهسازی آرایههای یکبعدی، دوبعدی یا سهبعدی از دادهها، مانند تصاویر، جهت استفاده در عملیات رندر GPU است.

یک نمونه از شیء `GPUTexture` با استفاده از متد {{domxref("GPUDevice.createTexture()")}} ساخته میشود.

{{InheritanceDiagram}}

## ویژگیهای نمونه

- {{domxref("GPUTexture.depthOrArrayLayers", "depthOrArrayLayers")}} {{ReadOnlyInline}}
  - : عددی که عمق یا تعداد لایههای `GPUTexture` را نشان میدهد (پیکسل یا تعداد لایهها).
- {{domxref("GPUTexture.dimension", "dimension")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی که ابعاد مجموعهٔ texelها را برای هر زیرمنبع `GPUTexture` نشان میدهد.
- {{domxref("GPUTexture.format", "format")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی که قالب `GPUTexture` را نشان میدهد. برای همهٔ مقادیر ممکن به بخش [Texture formats](https://gpuweb.github.io/gpuweb/#enumdef-gputextureformat) در مشخصات مراجعه کنید. همچنین [Tier 1 and Tier 2 texture formats](/en-US/docs/Web/API/GPUDevice/createTexture#tier_1_and_tier_2_texture_formats) را ببینید.
- {{domxref("GPUTexture.height", "height")}} {{ReadOnlyInline}}
  - : عددی که ارتفاع `GPUTexture` را بر حسب پیکسل نشان میدهد.
- {{domxref("GPUTexture.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم میکند، مثلاً در پیامهای {{domxref("GPUError")}} یا هشدارهای کنسول.
- {{domxref("GPUTexture.mipLevelCount", "mipLevelCount")}} {{ReadOnlyInline}}
  - : عددی که تعداد سطحهای مایپ (mip levels) `GPUTexture` را نشان میدهد.
- {{domxref("GPUTexture.sampleCount", "sampleCount")}} {{ReadOnlyInline}}
  - : عددی که تعداد نمونههای `GPUTexture` را نشان میدهد.
- {{domxref("GPUTexture.usage", "usage")}} {{ReadOnlyInline}}
  - : {{glossary("bitwise flags")}} که کاربردهای مجاز `GPUTexture` را نشان میدهد.
- {{domxref("GPUTexture.width", "width")}} {{ReadOnlyInline}}
  - : عددی که عرض `GPUTexture` را بر حسب پیکسل نشان میدهد.

## روشهای نمونه

- {{domxref("GPUTexture.createView", "createView()")}}
  - : یک {{domxref("GPUTextureView")}} میسازد که نمای خاصی از `GPUTexture` را نشان میدهد.
- {{domxref("GPUTexture.destroy", "destroy()")}}
  - : `GPUTexture` را از بین میبرد.

## مثالها

در نمونههای WebGPU، [نمونهٔ مکعب با بافت](https://webgpu.github.io/webgpu-samples/samples/texturedCube/)، یک بافت برای استفاده روی وجههای مکعب به این صورت ساخته میشود:

- بارگذاری تصویر در یک {{domxref("HTMLImageElement")}} و ساخت bitmap تصویر با استفاده از {{domxref("Window.createImageBitmap", "createImageBitmap()")}}.
- ساخت یک `GPUTexture` جدید با استفاده از `createTexture()`.
- کپی کردن bitmap تصویر در بافت با استفاده از {{domxref("GPUQueue.copyExternalImageToTexture()")}}.

```js
// …
let cubeTexture;
{
  const img = document.createElement("img");

  img.src = new URL(
    "../../../assets/img/Di-3d.png",
    import.meta.url,
  ).toString();

  await img.decode();

  const imageBitmap = await createImageBitmap(img);

  cubeTexture = device.createTexture({
    size: [imageBitmap.width, imageBitmap.height, 1],
    format: "rgba8unorm",
    usage:
      GPUTextureUsage.TEXTURE_BINDING |
      GPUTextureUsage.COPY_DST |
      GPUTextureUsage.RENDER_ATTACHMENT,
  });

  device.queue.copyExternalImageToTexture(
    { source: imageBitmap },
    { texture: cubeTexture },
    [imageBitmap.width, imageBitmap.height],
  );
}
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)