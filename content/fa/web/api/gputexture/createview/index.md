---
title: "GPUTexture: createView() method"
short-title: createView()
slug: Web/API/GPUTexture/createView
page-type: web-api-instance-method
browser-compat: api.GPUTexture.createView
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createView()`** از رابط {{domxref("GPUTexture")}} یک {{domxref("GPUTextureView")}} ایجاد می‌کند که نمای خاصی از `GPUTexture` را نشان می‌دهد.

## Syntax

```js-nolint
createView()
createView(descriptor)
```

### Parameters

- `descriptor` {{optional_inline}}
  - : یک شیء حاوی ویژگی‌های زیر:
    - `arrayLayerCount` {{optional_inline}}
      - : عددی که مشخص می‌کند چند لایه آرایه (array layer) برای نمای بافت قابل دسترسی است، که از مقدار `baseArrayLayer` شروع می‌شود.

        اگر `arrayLayerCount` حذف شود، مقدار آن به صورت زیر تعیین می‌گردد:
        - اگر `dimension` برابر `"1d"`، `"2d"` یا `"3d"` باشد، `arrayLayerCount` برابر 1 است.
        - اگر `dimension` برابر `"cube"` باشد، `arrayLayerCount` برابر 6 است.
        - اگر `dimension` برابر `"2d-array"` یا `"cube-array"` باشد، `arrayLayerCount` برابر {{domxref("GPUTexture.depthOrArrayLayers")}} - `baseArrayLayer` است.

    - `aspect` {{optional_inline}}
      - : یک مقدار شمارشی که مشخص می‌کند کدام جنبه(های) از بافت برای نمای بافت قابل دسترسی است. مقادیر ممکن:
        - `"all"`
          - : تمام جنبه‌های موجود از قالب بافت برای نمای بافت قابل دسترسی خواهد بود، که می‌تواند به معنای همه یا هر یک از جنبه‌های رنگ، عمق و استنسیل باشد، بسته به نوع قالبی که با آن کار می‌کنید.
        - `"depth-only"`
          - : فقط جنبه عمق یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) برای نمای بافت قابل دسترسی خواهد بود.
        - `"stencil-only"`
          - : فقط جنبه استنسیل یک قالب عمق-یا-استنسیل برای نمای بافت قابل دسترسی خواهد بود.

        اگر حذف شود، `aspect` مقدار `"all"` را می‌گیرد.

    - `baseArrayLayer` {{optional_inline}}
      - : عددی که ایندکس اولین لایه آرایه قابل دسترسی در نمای بافت را مشخص می‌کند. اگر حذف شود، `baseArrayLayer` مقدار 0 را می‌گیرد.
    - `baseMipLevel` {{optional_inline}}
      - : عددی که اولین (با بیشترین جزئیات) سطح mipmap قابل دسترسی در نمای بافت را نشان می‌دهد. اگر حذف شود، `baseMipLevel` مقدار 0 را می‌گیرد.
    - `dimension` {{optional_inline}}
      - : یک مقدار شمارشی که قالب مشاهده بافت را مشخص می‌کند. مقادیر ممکن:
        - `"1d"`: بافت به صورت یک تصویر یک‌بعدی مشاهده می‌شود.
        - `"2d"`: بافت به صورت یک تصویر دو‌بعدی تکی مشاهده می‌شود.
        - `"2d-array"`: بافت به صورت آرایه‌ای از تصاویر دو‌بعدی مشاهده می‌شود.
        - `"cube"`: بافت به صورت یک نقشه مکعبی (cubemap) مشاهده می‌شود. نمای بافت دارای 6 لایه آرایه است که متناظر با وجه‌های `[+X, -X, +Y, -Y, +Z, -Z]` مکعب هستند. نمونه‌برداری به صورت یکپارچه در سراسر وجه‌های نقشه مکعبی انجام می‌شود.
        - `"cube-array"`: بافت به صورت آرایه‌ای فشرده از N نقشه مکعبی مشاهده می‌شود، که هر کدام 6 لایه آرایه متناظر با وجه‌های `[+X, -X, +Y, -Y, +Z, -Z]` مکعب دارند. نمونه‌برداری به صورت یکپارچه در سراسر وجه‌های نقشه‌های مکعبی انجام می‌شود.
        - `"3d"`: بافت به صورت یک تصویر سه‌بعدی مشاهده می‌شود.

        اگر `dimension` حذف شود، مقدار آن به صورت زیر تعیین می‌گردد:
        - اگر {{domxref("GPUTexture.dimension")}} برابر `"1d"` باشد، `dimension` برابر `"1d"` است.
        - اگر {{domxref("GPUTexture.dimension")}} برابر `"2d"` و {{domxref("GPUTexture.depthOrArrayLayers")}} برابر 1 باشد، `dimension` برابر `"2d"` است.
        - اگر {{domxref("GPUTexture.dimension")}} برابر `"2d"` و {{domxref("GPUTexture.depthOrArrayLayers")}} بیشتر از 1 باشد، `dimension` برابر `"2d-array"` است.
        - اگر {{domxref("GPUTexture.dimension")}} برابر `"3d"` باشد، `dimension` برابر `"3d"` است.

    - `format` {{optional_inline}}
      - : یک مقدار شمارشی که قالب نمای بافت را مشخص می‌کند. بخش [Texture formats](https://gpuweb.github.io/gpuweb/#enumdef-gputextureformat) از مشخصات فنی را برای همه مقادیر ممکن مشاهده کنید.

        اگر `format` حذف شود، مقدار آن به صورت زیر تعیین می‌گردد:
        - اگر `aspect` برابر `"depth-only"` یا `"stencil-only"` باشد، و {{domxref("GPUTexture.format")}} یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) باشد، `format` برابر [قالب مختص جنبه](https://gpuweb.github.io/gpuweb/#aspect-specific-format) مناسب تنظیم می‌شود.
        - در غیر این صورت برابر {{domxref("GPUTexture.format")}} تنظیم می‌شود.

    - `label` {{optional_inline}}
      - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `mipLevelCount` {{optional_inline}}
      - : عددی که مشخص می‌کند چند سطح mipmap برای نمای بافت قابل دسترسی است، که از مقدار `baseMipLevel` شروع می‌شود.

        اگر `mipLevelCount` حذف شود، مقدار آن برابر {{domxref("GPUTexture.mipLevelCount")}} - `baseMipLevel` خواهد بود.

    - `swizzle` {{optional_inline}}
      - : رشته‌ای شامل چهار کاراکتر. موقعیت هر کاراکتر به ترتیب به مقادیر کانال قرمز، سبز، آبی و آلفای نمای بافت نگاشت می‌شود. مقدار هر کاراکتر مشخص می‌کند که هر یک از آن کانال‌ها هنگام دسترسی shader به نمای بافت چه مقداری خواهند داشت. مقادیر ممکن:
        - `r`
          - : مقدار کانال قرمز بافت.
        - `g`
          - : مقدار کانال سبز بافت.
        - `b`
          - : مقدار کانال آبی بافت.
        - `a`
          - : مقدار کانال آلفای بافت.
        - `0`
          - : مقدار `0` را اعمال می‌کند.
        - `1`
          - : مقدار `1` را اعمال می‌کند.

        به عنوان مثال، `swizzle: "grba"` باعث می‌شود مقادیر کانال قرمز و سبز بافت هنگام دسترسی shader به نمای بافت جابجا شوند. دگرگونی مؤلفه‌های بافت (texture component swizzle) به توسعه‌دهندگان اجازه می‌دهد عملکرد را بهینه کنند، عدم تطابق ترتیب مؤلفه‌ها را اصلاح کنند، و کد shader را در قالب‌های مختلف بافت هنگام نمونه‌برداری مجدداً استفاده کنند.

        > [!NOTE]
        > برای استفاده از ویژگی `swizzle`، باید [قابلیت](/en-US/docs/Web/API/GPUSupportedFeatures) `texture-component-swizzle` را در {{domxref("GPUDevice")}} خود با مشخص کردن آن در آرایه `requiredFeatures` توصیف‌گر {{domxref("GPUAdapter.requestDevice()")}} فعال کنید. اگر این قابلیت فعال نباشد، ویژگی `swizzle` هیچ تأثیری نخواهد داشت.

    - `usage` {{optional_inline}}
      - : مجموعه‌ای از {{glossary("bitwise flags", "پرچم‌های بیتی")}} که زیرمجموعه‌ای از پرچم‌های استفاده بافت مبدأ (موجود در ویژگی {{domxref("GPUTexture.usage")}}) را نشان می‌دهد که با قالب نمای انتخاب‌شده سازگار هستند. این می‌تواند برای محدود کردن استفاده مجاز نمای بافت در مواردی که قالب نمای بافت با برخی کاربردها ناسازگار است، استفاده شود. پرچم‌های استفاده موجود در [جدول مقدار `GPUTexture.usage`](/en-US/docs/Web/API/GPUTexture/usage#value) فهرست شده‌اند.

        مقدار پیش‌فرض `0` است که مجموعه کامل پرچم‌های استفاده بافت مبدأ را نشان می‌دهد. اگر [`format`](#format) نمای بافت از همه کاربردهای بافت پشتیبانی نکند، مقدار پیش‌فرض ناموفق خواهد بود و باید `usage` نمای بافت به صراحت مشخص شود.

### Return value

یک نمونه شیء از {{domxref("GPUTextureView")}}.

### Validation

معیارهای زیر باید هنگام فراخوانی **`createView()`** برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و یک شیء {{domutex("GPUTextureView")}} نامعتبر بازگردانده می‌شود:

- اگر `aspect` برابر `"all"` باشد، `format` برابر {{domxref("GPUTexture.format")}} یا یکی از `viewFormats` مشخص‌شده در شیء توصیف‌گر فراخوانی {{domxref("GPUDevice.createTexture()")}} مبدأ است.
- اگر `aspect` برابر `"depth-only"` یا `"stencil-only"` باشد، `format` برابر [قالب مختص جنبه](https://gpuweb.github.io/gpuweb/#aspect-specific-format) مناسب از [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) است.
- `mipLevelCount` بزرگتر از 0 است.
- `mipLevelCount` + `baseMipLevel` کمتر یا مساوی {{domxref("GPUTexture.mipLevelCount")}} است.
- `arrayLayerCount` بزرگتر از 0 است.
- `arrayLayerCount` + `baseArrayLayer` اگر {{domxref("GPUTexture.dimension")}} برابر `"2d"` باشد، کمتر یا مساوی {{domxref("GPUTexture.depthOrArrayLayers")}} است، و اگر {{domxref("GPUTexture.dimension")}} برابر `"1d"` یا `"3d"` باشد، کمتر یا مساوی 1 است.
- اگر `sampleCount` بزرگتر از 1 باشد، `dimension` برابر `"2d"` است.
- اگر `dimension` برابر:
  - `"1d"` باشد:
    - {{domxref("GPUTexture.dimension")}} برابر `"1d"` است.
    - `arrayLayerCount` برابر 1 است.
  - `"2d"` باشد:
    - {{domxref("GPUTexture.dimension")}} برابر `"2d"` است.
    - `arrayLayerCount` برابر 1 است.
  - `"2d-array"` باشد:
    - {{domxref("GPUTexture.dimension")}} برابر `"2d"` است.
  - `"cube"` باشد:
    - {{domxref("GPUTexture.dimension")}} برابر `"2d"` است.
    - `arrayLayerCount` برابر 6 است.
    - {{domxref("GPUTexture.width")}} برابر {{domxref("GPUTexture.height")}} است.
  - `"cube-array"` باشد:
    - {{domxref("GPUTexture.dimension")}} برابر `"2d"` است.
    - `arrayLayerCount` مضربی از 6 است.
    - {{domxref("GPUTexture.width")}} برابر {{domxref("GPUTexture.height")}} است.
  - `"3d"` باشد:
    - {{domxref("GPUTexture.dimension")}} برابر `"3d"` است.
    - `arrayLayerCount` برابر 1 است.
- [`format`](#format) نمای بافت از همه کاربردهای مشخص‌شده در ویژگی [`usage`](#usage) پشتیبانی می‌کند.

## Examples

### استفاده معمول از `createView()`

در نمونه WebGPU Samples [Cubemap demo](https://webgpu.github.io/webgpu-samples/samples/cubemap/)، چندین مثال از نحوه استفاده `createView()` مشاهده خواهید کرد، هم برای ایجاد یک `resource` نمای بافت برای فراخوانی {{domxref("GPUDevice.createBindGroup()")}} و هم برای ارائه یک `view` در شیء `depthStencilAttachment` توصیف‌گر {{domxref("GPUCommandEncoder.beginRenderPass()")}}.

```js
const uniformBindGroup = device.createBindGroup({
  layout: pipeline.getBindGroupLayout(0),
  entries: [
    {
      binding: 0,
      resource: {
        buffer: uniformBuffer,
        offset: 0,
        size: uniformBufferSize,
      },
    },
    {
      binding: 1,
      resource: sampler,
    },
    {
      binding: 2,
      resource: cubemapTexture.createView({
        dimension: "cube",
      }),
    },
  ],
});

const renderPassDescriptor: GPURenderPassDescriptor = {
  colorAttachments: [
    {
      view: undefined, // Assigned later
      loadOp: "clear",
      storeOp: "store",
    },
  ],
  depthStencilAttachment: {
    view: depthTexture.createView(),

    depthClearValue: 1.0,
    depthLoadOp: "clear",
    depthStoreOp: "store",
  },
};

// …

const commandEncoder = device.createCommandEncoder();
const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// …
```

### `createView()` با محدودیت استفاده

در این قطعه، یک بافت ایجاد می‌کنیم و سپس نمایی ایجاد می‌کنیم که استفاده آن از طریق ویژگی `usage` محدود شده است.

```js
const texture = myDevice.createTexture({
  size: [4, 4],
  format: "rgba8unorm",
  usage:
    GPUTextureUsage.RENDER_ATTACHMENT |
    GPUTextureUsage.TEXTURE_BINDING |
    GPUTextureUsage.STORAGE_BINDING,
  viewFormats: ["rgba8unorm-srgb"],
});

const view = texture.createView({
  format: "rgba8unorm-srgb",
  usage: GPUTextureUsage.RENDER_ATTACHMENT, // Restrict allowed usage
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)