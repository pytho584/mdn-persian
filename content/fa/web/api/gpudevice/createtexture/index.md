---
title: "GPUDevice: createTexture() method"
short-title: createTexture()
slug: Web/API/GPUDevice/createTexture
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createTexture()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPUTexture")}} برای ذخیره‌سازی آرایه‌های داده‌های یک‌بعدی، دو‌بعدی یا سه‌بعدی (مانند تصاویر) ایجاد می‌کند که در عملیات رندرگیری GPU استفاده می‌شوند.

## نحو

```js-nolint
createTexture(descriptor)
```

### پارامترها

- `descriptor`
  - : شیئی شامل ویژگی‌های زیر:
    - `dimension` {{optional_inline}}
      - : یک مقدار شمارشی که سطح بعد (dimension) بافت را مشخص می‌کند. مقادیر ممکن عبارتند از:
        - `"1d"`: بافت یک‌بعدی است.
        - `"2d"`: بافت دو‌بعدی یا آرایه‌ای از لایه‌های دو‌بعدی است.
        - `"3d"`: بافت سه‌بعدی است.

        اگر این مقدار حذف شود، پیش‌فرض `"2d"` است.

    - `format`
      - : یک مقدار شمارشی که قالب (format) بافت را مشخص می‌کند. برای مشاهدهٔ تمام مقادیر ممکن، بخش [Texture formats](https://gpuweb.github.io/gpuweb/#enumdef-gputextureformat) مشخصات را ببینید.

        > [!NOTE]
        >
        > - برای ایجاد {{domputed("GPUTexture")}}هایی با قالب `depth32float-stencil8`، باید [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `depth32float-stencil8` فعال باشد.
        > - برای ایجاد `GPUTexture`های فشرده‌شدهٔ BC دو‌بعدی (`dimension: "2d"`) با قالب‌های `bc1-rgba-unorm`، `bc1-rgba-unorm-srgb`، `bc2-rgba-unorm`، `bc2-rgba-unorm-srgb`، `bc3-rgba-unorm`، `bc3-rgba-unorm-srgb`، `bc4-r-unorm`، `bc4-r-snorm`، `bc5-rg-unorm`، `bc5-rg-snorm`، `bc6h-rgb-ufloat`، `bc6h-rgb-float`، `bc7-rgba-unorm` و `bc7-rgba-unorm-srgb`، باید ویژگی `texture-compression-bc` فعال باشد.
        > - برای ایجاد `GPUTexture`های فشرده‌شدهٔ BC سه‌بعدی (همان مقادیر `format` در مورد قبلی، اما با `dimension` برابر `3d`)، باید ویژگی‌های `texture-compression-bc` و `texture-compression-bc-sliced-3d` فعال باشند.
        > - برای ایجاد `GPUTexture`های فشرده‌شدهٔ ASTC دو‌بعدی (`dimension: "2d"`) با قالب‌های `astc-4x4-unorm`، `astc-4x4-unorm-srgb`، `astc-5x4-unorm`، `astc-5x4-unorm-srgb`، `astc-5x5-unorm`، `astc-5x5-unorm-srgb`، `astc-6x5-unorm`، `astc-6x5-unorm-srgb`، `astc-6x6-unorm`، `astc-6x6-unorm-srgb`، `astc-8x5-unorm`، `astc-8x5-unorm-srgb`، `astc-8x6-unorm`، `astc-8x6-unorm-srgb`، `astc-8x8-unorm`، `astc-8x8-unorm-srgb`، `astc-10x5-unorm`، `astc-10x5-unorm-srgb`، `astc-10x6-unorm`، `astc-10x6-unorm-srgb`، `astc-10x8-unorm`، `astc-10x8-unorm-srgb`، `astc-10x10-unorm`، `astc-10x10-unorm-srgb`، `astc-12x10-unorm`، `astc-12x10-unorm-srgb`، `astc-12x12-unorm` و `astc-12x12-unorm-srgb`، باید ویژگی `texture-compression-astc` فعال باشد.
        > - برای ایجاد `GPUTexture`های فشرده‌شدهٔ ASTC سه‌بعدی (همان مقادیر `format` در مورد قبلی، اما با `dimension` برابر `3d`)، باید ویژگی‌های `texture-compression-astc` و `texture-compression-astc-sliced-3d` فعال باشند.
        > - برای ایجاد `GPUTexture`های فشرده‌شدهٔ ETC2 دو‌بعدی با قالب‌های `etc2-rgb8unorm`، `etc2-rgb8unorm-srgb`، `etc2-rgb8a1unorm`، `etc2-rgb8a1unorm-srgb`، `etc2-rgba8unorm`، `etc2-rgba8unorm-srgb`، `eac-r11unorm`، `eac-r11snorm`، `eac-rg11unorm` و `eac-rg11snorm`، باید ویژگی `texture-compression-etc2` فعال باشد.
        > - برای اطلاعات بیشتر دربارهٔ مجموعه‌های قالب‌های بافت Tier 1 و Tier 2 و الزامات ایجاد آن‌ها، بخش [Tier 1 and Tier 2 texture formats](#tier_1_and_tier_2_texture_formats) را ببینید.

    - `label` {{optional_inline}}
      - : یک رشته که برچسبی برای شناسایی شیء ارائه می‌دهد، مثلاً در پیام‌های {{domputed("GPUError")}} یا هشدارهای کنسول.
    - `mipLevelCount` {{optional_inline}}
      - : عددی که تعداد سطوح mip را که بافت شامل خواهد شد مشخص می‌کند. اگر حذف شود، پیش‌فرض ۱ است.
    - `sampleCount` {{optional_inline}}
      - : عددی که تعداد نمونه (sample count) بافت را مشخص می‌کند. برای معتبر بودن، مقدار باید ۱ یا ۴ باشد. اگر حذف شود، پیش‌فرض ۱ است. مقدار بیشتر از ۱ نشان‌دهندهٔ بافت چندنمونه‌ای (multi-sampled) است.
    - `size`
      - : یک شیء یا آرایه که عرض، ارتفاع و تعداد لایه‌های عمق/آرایه بافت را مشخص می‌کند. مقدار عرض همیشه باید مشخص شود، در حالی که ارتفاع و تعداد لایه‌های عمق/آرایه اختیاری هستند و در صورت حذف پیش‌فرض ۱ می‌گیرند.

        به عنوان مثال، می‌توانید آرایه‌ای مانند `[16, 16, 2]` یا شیء معادل آن `{ width: 16, height: 16, depthOrArrayLayers: 2 }` را ارسال کنید.

    - `usage`
      - : {{glossary("Bitwise_flags", "پرچم‌های بیتی")}} که کاربردهای مجاز `GPUTexture` را نشان می‌دهند. مقادیر ممکن در [جدول مقادیر `GPUTexture.usage`](/en-US/docs/Web/API/GPUTexture/usage#value) آمده است.

        توجه داشته باشید که با جدا کردن مقادیر با [OR بیتی](/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR) می‌توان چندین کاربرد ممکن را مشخص کرد، مثلاً: `GPUTextureUsage.COPY_DST | GPUTextureUsage.RENDER_ATTACHMENT`.

        > [!NOTE]
        >
        > - برای مشخص کردن کاربرد `STORAGE_BINDING` برای یک {{domputed("GPUTexture")}} با [`format`](#format) برابر `bgra8unorm`، باید [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `bgra8unorm-storage` فعال باشد.
        > - برای مشخص کردن کاربرد `RENDER_ATTACHMENT` برای یک {{domputed("GPUTexture")}} با [`format`](#format) برابر `rg11b10ufloat`، و همچنین ترکیب (blending) و چندنمونه‌گیری (multisampling) آن، باید [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `rg11b10ufloat-renderable` فعال باشد.

    - `viewFormats` {{optional_inline}}
      - : آرایه‌ای از مقادیر شمارشی که سایر [قالب‌های بافت](https://gpuweb.github.io/gpuweb/#enumdef-gputextureformat) مجاز را هنگام فراخوانی {{domputed("GPUTexture.createView()")}} روی این بافت مشخص می‌کنند، علاوه بر قالبی که در `format` آن مشخص شده است.

### مقدار بازگشتی

یک نمونهٔ شیء {{domputed("GPUTexture")}}.

### اعتبارسنجی

هنگام فراخوانی **`createTexture()`** معیارهای زیر باید رعایت شوند، در غیر این صورت یک {{domputed("GPUValidationError")}} تولید شده و یک شیء {{domputed("GPUTexture")}} نامعتبر بازگردانده می‌شود:

- یک `usage` معتبر مشخص شده است.
- مقادیر مشخص‌شده در `size` (عرض، ارتفاع یا تعداد لایه‌های عمق/آرایه) بزرگ‌تر از ۰ هستند.
- `mipLevelCount` بزرگ‌تر از ۰ است.
- `sampleCount` برابر ۱ یا ۴ است.
- اگر `dimension` برابر `"1d"` تعیین شود:
  - مقدار عرض `size` کمتر یا مساوی {{domputed("GPUDevice")}}'s `maxTextureDimension1D` {{domputed("GPUSupportedLimits", "limit", "", "nocode")}} است.
  - مقادیر ارتفاع و تعداد لایه‌های عمق/آرایه `size` برابر ۱ هستند.
  - `sampleCount` برابر ۱ است.
  - `format` برابر با یک [قالب فشرده](https://gpuweb.github.io/gpuweb/#compressed-format) یا [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#depth-or-stencil-format) نیست.
- اگر `dimension` برابر `"2d"` تعیین شود:
  - مقادیر عرض و ارتفاع `size` کمتر یا مساوی {{domputed("GPUDevice")}}'s `maxTextureDimension2D` {{domputed("GPUSupportedLimits", "limit", "", "nocode")}} هستند.
  - مقدار تعداد لایه‌های عمق/آرایه `size` کمتر یا مساوی {{domputed("GPUDevice")}}'s `maxTextureArrayLayers` {{domputed("GPUSupportedLimits", "limit", "", "nocode")}} است.
- اگر `dimension` برابر `"3d"` تعیین شود:
  - مقادیر عرض، ارتفاع و تعداد لایه‌های عمق/آرایه `size` کمتر یا مساوی {{domputed("GPUDevice")}}'s `maxTextureDimension3D` {{domputed("GPUSupportedLimits", "limit", "", "nocode")}} هستند.
  - مقدار `sampleCount` برابر ۱ است.
  - `format` برابر با یک [قالب فشرده](https://gpuweb.github.io/gpuweb/#compressed-format) یا [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#depth-or-stencil-format) نیست.
- مقدار عرض `size` مضربی از [عرض بلوک تکسِل](https://gpuweb.github.io/gpuweb/#texel-block-width) است.
- مقدار ارتفاع `size` مضربی از [ارتفاع بلوک تکسِل](https://gpuweb.github.io/gpuweb/#texel-block-height) است.
- اگر `sampleCount` بزرگ‌تر از ۱ باشد:
  - `mipLevelCount` برابر ۱ است.
  - مقدار تعداد لایه‌های عمق/آرایه `size` برابر ۱ است.
  - `usage` شامل پرچم `GPUTextureUsage.RENDER_ATTACHMENT` است.
  - `usage` شامل پرچم `GPUTextureUsage.STORAGE_BINDING` نیست.
  - قالب مشخص‌شده از چندنمونه‌گیری پشتیبانی می‌کند.
- مقدار `mipLevelCount` کمتر یا مساوی [حداکثر تعداد miplevel](https://gpuweb.github.io/gpuweb/#abstract-opdef-maximum-miplevel-count) است.
- قالب‌های مشخص‌شده در `format` و `viewFormats` با یکدیگر [سازگار](https://gpuweb.github.io/gpuweb/#texture-view-format-compatible) هستند.
- اگر `usage` شامل پرچم `GPUTextureUsage.RENDER_ATTACHMENT` باشد:
  - `format` یک قالب قابل رندرگیری (یعنی یک قالب قابل رندرگیری رنگی یا یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#depth-or-stencil-format)) است.
  - `dimension` برابر `"2d"` تعیین شده است.
- اگر `usage` شامل پرچم `GPUTextureUsage.STORAGE_BINDING` باشد:
  - `format` مشخص‌شده شامل قابلیت `STORAGE_BINDING` است (برای مرجع به جدول [Plain color formats](https://gpuweb.github.io/gpuweb/#plain-color-formats) مراجعه کنید).
- اگر `usage` شامل پرچم `GPUTextureUsage.TRANSIENT_ATTACHMENT` باشد:
  - `usage` برابر `TRANSIENT_ATTACHMENT | RENDER_ATTACHMENT` است.
  - `dimension` برابر `"2d"` است.
  - `mipLevelCount` برابر `1` است.
  - `size.depthOrArrayLayers` برابر `1` است.

## قالب‌های بافت Tier 1 و Tier 2

این بخش قالب‌های بافت Tier1 و Tier2 WebGPU را توصیف می‌کند.

### Tier 1

مجموعه قالب‌های بافت Tier 1 به گونه‌ای طراحی شده است که به توسعه‌دهندگان اجازه دهد محتوای موجود را بدون نیاز به بازنویسی برای استفاده از قابلیت‌های سطح پایین WebGPU، به وب منتقل کنند. برای استفاده از این مجموعه، ویژگی `texture-formats-tier1` را فعال کنید (به {{domputed("GPUSupportedFeatures")}} مراجعه کنید).

فعال کردن این ویژگی امکان موارد زیر را فراهم می‌کند:

- استفاده از [`format`](#format)های زیر با [`usage`](#usage)های `RENDER_ATTACHMENT` (شامل قابلیت‌های ترکیب‌پذیری و چندنمونه‌گیری) و `STORAGE_BINDING` (با [`access`](/en-US/docs/Web/API/GPUDevice/createBindGroupLayout#access) `read-only` و `write-only`):
  - `r16unorm`
  - `r16snorm`
  - `rg16unorm`
  - `rg16snorm`
  - `rgba16unorm`
  - `rgba16snorm`
- استفاده از [`format`](#format)های زیر با [`usage`](#usage) `RENDER_ATTACHMENT` (شامل قابلیت‌های ترکیب‌پذیری و چندنمونه‌گیری):
  - `r8snorm`
  - `rg8snorm`
  - `rgba8snorm`
- استفاده از [`format`](#format)های زیر با [`usage`](#usage) `STORAGE_BINDING` (با [`access`](/en-US/docs/Web/API/GPUDevice/createBindGroupLayout#access) `read-only` و `write-only`):
  - `r8unorm`
  - `r8snorm`
  - `r8uint`
  - `r8sint`
  - `rg8unorm`
  - `rg8snorm`
  - `rg8uint`
  - `rg8sint`
  - `r16uint`
  - `r16sint`
  - `r16float`
  - `rg16uint`
  - `rg16sint`
  - `rg16float`
  - `rgb10a2uint`
  - `rgb10a2unorm`
  - `rg11b10ufloat`
- استفاده از قالب‌های `GPUTexture` زیر در [`texture`](/en-US/docs/Web/API/GPUQueue/copyExternalImageToTexture#texture) مقصد در فراخوانی‌های {{domputed("GPUQueue.copyExternalImageToTexture()")}}:
  - `r16unorm`
  - `rg16unorm`
  - `rgba16unorm`

> [!NOTE]
> فعال کردن ویژگی `texture-formats-tier1` به طور خودکار ویژگی `rg11b10ufloat-renderable` را فعال می‌کند که امکان استفاده از بافت `rg11b10ufloat` را با کاربرد `RENDER_ATTACHMENT`، از جمله ترکیب و چندنمونه‌گیری، فراهم می‌کند.

### Tier2

مجموعه قالب‌های بافت Tier 2 از قالب‌های بافت ذخیره‌سازی پشتیبانی می‌کند که در WebGPU "هسته" پشتیبانی نمی‌شوند و برای استفاده پیشرفته ضروری هستند. برای استفاده از این مجموعه، ویژگی `texture-formats-tier2` را فعال کنید (به {{domputed("GPUSupportedFeatures")}} مراجعه کنید).

فعال کردن این ویژگی امکان استفاده از [`format`](#format)های زیر را با [`usage`](#usage) `STORAGE_BINDING` (با [`access`](/en-US/docs/Web/API/GPUDevice/createBindGroupLayout#access) `read-write`) فراهم می‌کند:

- `r8unorm`
- `r8uint`
- `r8sint`
- `rgba8unorm`
- `rgba8uint`
- `rgba8sint`
- `r16uint`
- `r16sint`
- `r16float`
- `rgba16uint`
- `rgba16sint`
- `rgba16float`
- `rgba32uint`
- `rgba32sint`
- `rgba32float`

> [!NOTE]
> فعال کردن ویژگی `texture-formats-tier2` به طور خودکار ویژگی‌های `rg11b10ufloat-renderable` و `texture-formats-tier1` را فعال می‌کند.

## مثال‌ها

در نمونه WebGPU [Textured Cube sample](https://webgpu.github.io/webgpu-samples/samples/texturedCube/)، یک بافت برای استفاده روی وجوه یک مکعب به صورت زیر ایجاد می‌شود:

- بارگذاری تصویر در یک {{domputed("HTMLImageElement")}} و ایجاد یک bitmap تصویر با استفاده از {{domputed("Window.createImageBitmap", "createImageBitmap()")}}.
- ایجاد یک بافت جدید با استفاده از `createTexture()`.
- کپی کردن bitmap تصویر به داخل بافت با استفاده از {{domputed("GPUQueue.copyExternalImageToTexture()")}}.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)