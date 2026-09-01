---
title: "GPUDevice: createBindGroupLayout() method"
short-title: createBindGroupLayout()
slug: Web/API/GPUDevice/createBindGroupLayout
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createBindGroupLayout
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createBindGroupLayout()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPUBindGroupLayout")}} می‌سازد که ساختار و هدف منابع GPU مرتبط، مانند بافرهایی که در یک پایپلاین استفاده خواهند شد، را تعریف می‌کند و هنگام ایجاد {{domxref("GPUBindGroup")}}ها به‌عنوان قالب استفاده می‌شود.

## نحو (Syntax)

```js-nolint
createBindGroupLayout(descriptor)
```

### پارامترها

- `descriptor`
  - : یک شیء شامل ویژگی‌های زیر:
    - `entries`
      - : آرایه‌ای از [شیءهای ورودی](#entry_objects) که هر کدام یک اتصال (binding) منبع شیدر را توصیف می‌کند که قرار است در {{domxref("GPUBindGroupLayout")}} گنجانده شود. هر ورودی با یک ورودی تعریف‌شده در {{domxref("GPUBindGroup")}} (که از طریق یک فراخوانی {{domxref("GPUDevice.createBindGroup()")}} ایجاد شده) متناظر خواهد بود و از این شیء {{domxref("GPUBindGroupLayout")}} به‌عنوان قالب استفاده می‌کند.
    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

### شیءهای ورودی

یک شیء ورودی شامل ویژگی‌های زیر است:

- `binding`
  - : عددی که شناسه‌ای یکتا برای این ورودی خاص است و با مقدار `binding` یک ورودی متناظر در {{domxref("GPUBindGroup")}} مطابقت دارد. همچنین با مقدار اندیس `n` صفت [`@binding(n)`](https://gpuweb.github.io/gpuweb/wgsl/#attribute-binding) در شیدر ({{domxref("GPUShaderModule")}}) مورد استفاده در پایپلاین مرتبط مطابقت دارد.
- `visibility`
  - : یک یا چند {{glossary("Bitwise_flags", "bitwise flags")}} که مرحله‌های شیدری را تعریف می‌کنند که یک ورودی {{domxref("GPUBindGroup")}} متناظر با این ورودی در آن‌ها قابل مشاهده خواهد بود. مقادیر ممکن عبارت‌اند از:
    - `GPUShaderStage.COMPUTE`: ورودی bind group برای شیدرهای محاسباتی قابل دسترسی خواهد بود.
    - `GPUShaderStage.FRAGMENT`: ورودی bind group برای شیدرهای فرگمنت قابل دسترسی خواهد بود.
    - `GPUShaderStage.VERTEX`: ورودی bind group برای شیدرهای رأس قابل دسترسی خواهد بود.

    توجه داشته باشید که می‌توان چند مرحله را با جدا کردن مقادیر با [عملگر OR بیتی](/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR) مشخص کرد، برای مثال: `GPUShaderStage.FRAGMENT | GPUShaderStage.VERTEX`.

- "شیء طرح‌بندی منبع (resource layout object)"
  - : شیئی که نوع منبع اتصال الزامی و ساختار ورودی {{domxref("GPUBindGroup")}} متناظر با این ورودی را تعریف می‌کند. این ویژگی می‌تواند یکی از موارد `buffer`، `externalTexture`، `sampler`، `storageTexture` یا `texture` باشد که ساختار اشیاء آن‌ها در بخش بعد توضیح داده شده است.

### شیءهای طرح‌بندی منبع

شیء طرح‌بندی منبع می‌تواند یکی از موارد زیر باشد (همچنین به {{domxref("GPUDevice.createBindGroup()")}} مراجعه کنید تا جزئیات مربوط به ساختار منابع موردنیاز برای هر ورودی را مشاهده کنید):

- `buffer`: نشان می‌دهد که ورودی متناظر {{domxref("GPUBindGroup")}} یک شیء `GPUBufferBinding` خواهد بود، که شامل یک {{domxref("GPUBuffer")}} به همراه مقادیر `offset` و `size` است. یک شیء طرح‌بندی منبع `buffer` می‌تواند شامل ویژگی‌های زیر باشد:
  - `hasDynamicOffset` {{optional_inline}}
    - : یک مقدار بولین. اگر برابر با `true` باشد، نشان می‌دهد که این اتصال به یک آفست پویا (dynamic offset) نیاز دارد، مثلاً همان‌طور که در طی یک فراخوانی {{domxref("GPURenderPassEncoder.setBindGroup()")}} تنظیم می‌شود. اگر حذف شود، `hasDynamicOffset` به‌صورت پیش‌فرض `false` است.

  - `minBindingSize` {{optional_inline}}
    - : عددی که حداقل اندازه مجاز بافرهای متصل را بر حسب بایت نشان می‌دهد. اگر حذف شود، `minBindingSize` به‌صورت پیش‌فرض 0 است. اگر مقدار 0 باشد، حداقل اندازه بافر در هنگام ایجاد پایپلاین نادیده گرفته می‌شود و در عوض توسط دستورهای draw/dispatch صادرشده اعتبارسنجی می‌شود.

  - `type` {{optional_inline}}
    - : یک مقدار شمارشی که نوع موردنیاز برای {{domxref("GPUBuffer")}}های متصل به این اتصال را مشخص می‌کند (برای اطلاعات بیشتر درباره انواع بافر به {{domxref("GPUDevice.createBuffer()")}} مراجعه کنید). مقادیر ممکن عبارت‌اند از:
      - `"read-only-storage"`: یک بافر فقط‌خواندنی که با `usage` برابر با `GPUBufferUsage.STORAGE` ساخته شده است.
      - `"storage"`: یک بافر قابل‌نوشتن که با `usage` برابر با `GPUBufferUsage.STORAGE` ساخته شده است.
      - `"uniform"`: یک بافر که با `usage` برابر با `GPUBufferUsage.UNIFORM` ساخته شده است.

      اگر حذف شود، `type` به‌صورت پیش‌فرض `"uniform"` است.

- `externalTexture`: نشان می‌دهد که ورودی متناظر {{domxref("GPUBindGroup")}} یک شیء {{domxref("GPUExternalTexture")}} خواهد بود. یک شیء طرح‌بندی منبع `externalTexture` خالی است — `{}`.

- `sampler`: نشان می‌دهد که ورودی متناظر {{domxref("GPUBindGroup")}} یک شیء {{domxref("GPUSampler")}} خواهد بود. یک شیء طرح‌بندی منبع `sampler` می‌تواند شامل ویژگی‌های زیر باشد:
  - `type` {{optional_inline}}
    - : یک مقدار شمارشی که نوع موردنیاز برای {{domxref("GPUSampler")}}های متصل به این اتصال را مشخص می‌کند (برای اطلاعات بیشتر درباره انواع سمپلر به {{domxref("GPUDevice.createSampler()")}} مراجعه کنید). مقادیر ممکن عبارت‌اند از:
      - `"comparison"`: یک سمپلر مقایسه‌ای.
      - `"filtering"`: یک سمپلر فیلتردار.
      - `"non-filtering"`: یک سمپلر غیرفیلتردار.

      اگر حذف شود، `type` به‌صورت پیش‌فرض `"filtering"` است.

- `storageTexture`: نشان می‌دهد که ورودی متناظر {{domxref("GPUBindGroup")}} یک شیء {{domxref("GPUTextureView")}} خواهد بود. یک شیء طرح‌بندی منبع `storageTexture` می‌تواند شامل ویژگی‌های زیر باشد:
  - `access` {{optional_inline}}
    - : یک مقدار شمارشی که مشخص می‌کند آیا نمای بافت‌های متصل به این اتصال برای دسترسی خواندن و/یا نوشتن متصل خواهند شد. مقادیر ممکن عبارت‌اند از:
      - `"read-only"`: به کدهای WGSL اجازه می‌دهد تا بافت‌های ذخیره‌سازی (storage textures) را بخوانند.
      - `"read-write"`: به کدهای WGSL اجازه می‌دهد تا بافت‌های ذخیره‌سازی را بخوانند و بنویسند.
      - `"write-only"`: مقدار پیش‌فرض؛ به کدهای WGSL اجازه می‌دهد تا در بافت‌های ذخیره‌سازی بنویسند.

      مقادیر `"read-only"` و `"read-write"` فقط در صورتی قابل استفاده هستند که افزونه زبان WGSL [`"readonly_and_readwrite_storage_textures"`](/en-US/docs/Web/API/WGSLLanguageFeatures#readonly_and_readwrite_storage_textures) در {{domxref("WGSLLanguageFeatures")}} موجود باشد. اگر این‌طور نباشد، یک {{domxref("GPUValidationError")}} ایجاد می‌شود.

  - `format`
    - : یک مقدار شمارشی که قالب موردنیاز برای نمای بافت‌های متصل به این اتصال را مشخص می‌کند. برای مشاهده همه مقادیر `format` موجود به بخش [Texture Formats](https://gpuweb.github.io/gpuweb/#enumdef-gputextureformat) در مشخصات مراجعه کنید. همچنین [قالب‌های بافت Tier 1 و Tier 2](/en-US/docs/Web/API/GPUDevice/createTexture#tier_1_and_tier_2_texture_formats) را ببینید.
      > [!NOTE]
      > استفاده از قالب `bgra8unorm` برای بافت‌های ذخیره‌سازی فقط‌خواندنی منسوخ (deprecated) شده است. مشخصات به‌صراحت این کار را منع می‌کند، زیرا این قالب برای دسترسی فقط‌نوشتن در نظر گرفته شده است و قابل حمل نیست. هرگونه پشتیبانی مرورگر از این ترکیب به‌عنوان یک اشکال در نظر گرفته می‌شود.
  - `viewDimension` {{optional_inline}}
    - : یک مقدار شمارشی که بعد (dimension) موردنیاز برای نمای بافت‌های متصل به این اتصال را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
      - `"1d"`: بافت به‌عنوان یک تصویر یک‌بعدی دیده می‌شود.
      - `"2d"`: بافت به‌عنوان یک تصویر دو بعدی دیده می‌شود.
      - `"2d-array"`: بافت به‌عنوان آرایه‌ای از تصاویر دو بعدی دیده می‌شود.
      - `"cube"`: بافت به‌عنوان یک نقشه مکعبی (cubemap) دیده می‌شود. نمای شامل ۶ لایه آرایه‌ای است که با وجوه `[+X, -X, +Y, -Y, +Z, -Z]` مکعب متناظرند. نمونه‌برداری به‌صورت یکپارچه در سراسر وجوه نقشه مکعبی انجام می‌شود.
      - `"cube-array"`: بافت به‌عنوان آرایه‌ای فشرده از `n` نقشه مکعبی دیده می‌شود که هر کدام ۶ لایه آرایه‌ای متناظر با وجوه `[+X, -X, +Y, -Y, +Z, -Z]` مکعب دارند. نمونه‌برداری به‌صورت یکپارچه در سراسر وجوه نقشه‌های مکعبی انجام می‌شود.
      - `"3d"`: بافت به‌عنوان یک تصویر سه‌بعدی دیده می‌شود.

      اگر حذف شود، `viewDimension` به‌صورت پیش‌فرض `"2d"` است.

- `texture`: نشان می‌دهد که ورودی متناظر {{domxref("GPUBindGroup")}} یک شیء {{domxref("GPUTextureView")}} خواهد بود. یک شیء طرح‌بندی منبع `texture` می‌تواند شامل ویژگی‌های زیر باشد:
  - `multisampled` {{optional_inline}}
    - : یک مقدار بولین. مقدار `true` نشان می‌دهد که نمای بافت‌های متصل به این اتصال باید چندنمونه‌ای (multi-sampled) باشند. اگر حذف شود، `multisampled` به‌صورت پیش‌فرض `false` است.

  - `sampleType` {{optional_inline}}
    - : یک مقدار شمارشی که نوع نمونه موردنیاز برای نمای بافت‌های متصل به این اتصال را مشخص می‌کند (برای اطلاعات بیشتر درباره انواع نمای بافت به {{domxref("GPUDevice.createTexture()")}} مراجعه کنید). مقادیر ممکن عبارت‌اند از:
      - `"depth"`
      - `"float"`
      - `"sint"`
      - `"uint"`
      - `"unfilterable-float"`

      اگر حذف شود، `sampleType` به‌صورت پیش‌فرض `"float"` است.

  - `viewDimension` {{optional_inline}}
    - : یک مقدار شمارشی که بعد موردنیاز برای نمای بافت‌های متصل به این اتصال را مشخص می‌کند. مقادیر ممکن و پیش‌فرض مانند شیء طرح‌بندی منبع `storageTexture` است — به بالا مراجعه کنید.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("GPUBindGroupLayout")}}.

### اعتبارسنجی

هنگام فراخوانی **`createBindGroupLayout()`** معیارهای زیر باید برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد می‌شود و یک شیء نامعتبر {{domxref("GPUBindGroupLayout")}} بازگردانده می‌شود:

- مقدار `binding` هر ورودی یکتا است.
- مقدار `binding` هر ورودی کمتر از {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} مربوط به `maxBindingsPerBindGroup` در {{domxref("GPUDevice")}} است.
- تعداد ورودی‌ها از [محدودیت‌های اسلات binding](https://gpuweb.github.io/gpuweb/#exceeds-the-binding-slot-limits) تجاوز نمی‌کند.
- فقط ۱ شیء طرح‌بندی منبع برای هر ورودی تعریف شده است.
- اگر `visibility` یک ورودی شامل `GPUShaderStage.VERTEX` باشد:
  - اگر شیء طرح‌بندی منبع آن یک `buffer` است، `type` آن `"storage"` نباشد.
  - شیء طرح‌بندی منبع آن یک `storageTexture` نباشد.
- اگر شیء طرح‌بندی منبع یک ورودی یک `texture` است و مقدار `multisampled` آن `true` است:
  - `viewDimension` آن `"2d"` باشد.
  - `sampleType` آن `"float"` نباشد.
- اگر شیء طرح‌بندی منبع یک ورودی یک `storageTexture` است:
  - `viewDimension` آن `"cube"` یا `"cube-array"` نباشد.
  - `format` آن قالبی باشد که از استفاده ذخیره‌سازی پشتیبانی می‌کند.

## مثال‌ها

> [!NOTE]
> [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) شامل مثال‌های بسیار بیشتری هستند.

### مثال پایه

[دموی محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما نمونه‌ای از ایجاد یک bind group layout و سپس استفاده از آن به‌عنوان قالب هنگام ایجاد یک bind group را نشان می‌دهد.

```js
// …

const bindGroupLayout = device.createBindGroupLayout({
  entries: [
    {
      binding: 0,
      visibility: GPUShaderStage.COMPUTE,
      buffer: {
        type: "storage",
      },
    },
  ],
});

const bindGroup = device.createBindGroup({
  layout: bindGroupLayout,
  entries: [
    {
      binding: 0,
      resource: {
        buffer: output,
      },
    },
  ],
});

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط WebGPU API](/en-US/docs/Web/API/WebGPU_API)