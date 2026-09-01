---
title: "GPUDevice: createBindGroup() method"
---

---
title: "GPUDevice: createBindGroup() method"
short-title: createBindGroup()
slug: Web/API/GPUDevice/createBindGroup
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createBindGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createBindGroup()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPUBindGroup")}} را بر اساس یک {{domxref("GPUBindGroupLayout")}} ایجاد می‌کند. این طرح‌بندی، مجموعه‌ای از منابع را تعریف می‌کند که قرار است به‌صورت گروهی به هم متصل شوند و نحوهٔ استفاده از آن‌ها را در مراحل سایه‌زن مشخص می‌کند.

## سینتکس

```js-nolint
createBindGroup(descriptor)
```

### پارامترها

- `descriptor`
  - : یک شیء حاوی ویژگی‌های زیر:
    - `entries`
      - : آرایه‌ای از اشیاء ورودی که منابعی را که باید در معرض دید سایه‌زن قرار بگیرند توصیف می‌کنند. به‌ازای هر ورودی متناظر که توسط {{domxref("GPUBindGroupLayout")}} ارجاع‌شده در `layout` توصیف شده است، یک مورد وجود خواهد داشت. هر شیء ورودی دارای ویژگی‌های زیر است:
        - `binding`
          - : عددی که شناسهٔ یکتا برای این اتصال منبع است و با مقدار `binding` یک ورودی متناظر در {{domxref("GPUBindGroupLayout")}} مطابقت دارد. همچنین با مقدار اندیس `n` ویژگی [`@binding(n)`](https://gpuweb.github.io/gpuweb/wgsl/#attribute-binding) در سایه‌زن ({{domxref("GPUShaderModule")}}) که در خط لولهٔ مرتبط استفاده می‌شود، مطابقت دارد.
        - `resource`
          - : منبعی که باید متصل شود. این می‌تواند یکی از موارد زیر باشد:
            - `GPUBufferBinding`: یک {{domxref("GPUBuffer")}} را در بر می‌گیرد؛ برای تعریف، [اشیاء GPUBufferBinding](#gpubufferbinding_objects) را ببینید.
            - {{domxref("GPUBuffer")}}: می‌تواند مستقیماً استفاده شود به‌جای اینکه در یک `GPUBufferBinding` پیچیده شود، به شرط استفاده از مقادیر پیش‌فرض [`offset`](#offset) و [`size`](#size).
            - {{domxref("GPUExternalTexture")}}
            - {{domxref("GPUTextureView")}}: می‌تواند به‌جای یک `GPUExternalTexture` استفاده شود، به شرط آنکه سازگار باشد (فرمت دوبعدی با یک زیرمنبع واحد، یعنی [`dimension: "2d"`](/en-US/docs/Web/API/GPUTexture/createView#dimension)).
            - {{domxref("GPUTexture")}}: می‌تواند به‌جای یک `GPUTextureView` استفاده شود، به شرط آنکه نمای پیش‌فرض مد نظر باشد. در این زمینه، `GPUTexture` معادل یک شیء `GPUTextureView` است که با فراخوانی {{domxref("GPUTexture.createView()")}} بدون مشخص‌کردن آرگومان ایجاد شده است.
            - {{domxref("GPUSampler")}}
    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `layout`
      - : {{domxref("GPUBindGroupLayout")}}ای که `entries` این گروه اتصال باید با آن مطابقت داشته باشند.

### اشیاء GPUBufferBinding

یک شیء `GPUBufferBinding` می‌تواند شامل ویژگی‌های زیر باشد:

- `buffer`
  - : شیء {{domxref("GPUBuffer")}} که می‌خواهید متصل کنید.
- `offset` {{optional_inline}}
  - : افست، بر حسب بایت، از ابتدای `buffer` تا ابتدای محدوده‌ای که توسط اتصال بافر در معرض دید سایه‌زن قرار می‌گیرد. اگر حذف شود، `offset` به‌طور پیش‌فرض ۰ است.
- `size` {{optional_inline}}
  - : اندازهٔ اتصال بافر، بر حسب بایت. اگر حذف شود، `size` محدوده‌ای خواهد بود که از `offset` شروع شده و به انتهای `buffer` ختم می‌شود. اگر هر دو `offset` و `size` حذف شوند، کل بافر در معرض دید سایه‌زن قرار می‌گیرد.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("GPUBindGroup")}}.

### اعتبارسنجی

هنگام فراخوانی **`createBindGroup()`** باید معیارهای زیر برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و یک شیء نامعتبر {{domxref("GPUBindGroup")}} بازگردانده می‌شود:

- تعداد ورودی‌های موجود در {{domxref("GPUBindGroupLayout")}} (`layout`) با تعداد اشیاء ورودی در `entries` برابر باشد.
- برای هر ورودی در {{domxref("GPUBindGroupLayout")}} (`layout`)، شیء ورودی متناظر در `entries` نوع منبع صحیح را متصل کند. برای مثال، یک شیء طرح‌بندی منبع از نوع `buffer` باید یک شیء `GPUBufferBinding` را در اتصال متناظر مشخص کرده باشد.
- اگر شیء طرح‌بندی منبع از نوع `buffer` باشد:
  - {{domxref("GPUBuffer")}} متصل‌شدهٔ متناظر:
    - قسمت متصل آن (که توسط `offset` و `size` مشخص شده) به‌طور کامل در داخل آن قرار داشته باشد و اندازه‌اش غیرصفر باشد.
    - اندازه‌ای بزرگ‌تر از `minBindingSize` در طرح‌بندی منبع `buffer` داشته باشد.
  - اگر `type` شیء طرح‌بندی منبع `"uniform"` باشد:
    - {{domxref("GPUBuffer")}} متصل‌شده دارای `usage` شامل `GPUBufferUsage.UNIFORM` باشد.
    - اندازهٔ مؤثر بخش بافر متصل‌شده کمتر یا مساوی `maxUniformBufferBindingSize` ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) در {{domxref("GPUDevice")}} باشد.
    - `offset` مشخص‌شده در `GPUBufferBinding` مضربی از `minUniformBufferOffsetAlignment` ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) در {{domxref("GPUDevice")}} باشد.
  - اگر `type` شیء طرح‌بندی منبع `"storage"` یا `"read-only-storage"` باشد:
    - {{domxref("GPUBuffer")}} متصل‌شده دارای `usage` شامل `GPUBufferUsage.STORAGE` باشد.
    - اندازهٔ مؤثر بخش بافر متصل‌شده کمتر یا مساوی `maxStorageBufferBindingSize` ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) در {{domxref("GPUDevice")}} باشد.
    - اندازهٔ مؤثر بخش بافر متصل‌شده مضربی از ۴ باشد.
    - `offset` مشخص‌شده در `GPUBufferBinding` مضربی از `minStorageBufferOffsetAlignment` ({{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) در {{domxref("GPUDevice")}} باشد.
- اگر شیء طرح‌بندی منبع از نوع `storageTexture` باشد، {{domxref("GPUTextureView")}} متصل‌شدهٔ متناظر:
  - دارای `dimension` برابر با `viewDimension` شیء طرح‌بندی منبع باشد (برای جزئیات بیشتر دربارهٔ تنظیمات نمای بافت، به {{domxref("GPUTexture.createView()")}} مراجعه کنید).
  - دارای `format` برابر با `sampleType` شیء طرح‌بندی منبع باشد.
  - دارای `mipLevelCount` برابر با ۱ باشد.
  - نمایی از یک {{domxref("GPUTexture")}} با `usage` شامل `GPUTextureUsage.STORAGE_BINDING` باشد.
- اگر شیء طرح‌بندی منبع از نوع `texture` باشد، {{domxref("GPUTextureView")}} متصل‌شدهٔ متناظر:
  - دارای `dimension` برابر با `viewDimension` شیء طرح‌بندی منبع باشد (برای جزئیات بیشتر دربارهٔ تنظیمات نمای بافت، به {{domxref("GPUTexture.createView()")}} مراجعه کنید).
  - دارای `format` سازگار با `sampleType` شیء طرح‌بندی منبع باشد.
  - نمایی از یک {{domxref("GPUTexture")}} با `usage` شامل `GPUTextureUsage.TEXTURE_BINDING` باشد.
  - اگر ویژگی `multisampled` شیء طرح‌بندی منبع `true` باشد، نمایی از یک {{domxref("GPUTexture")}} با `sampleCount` بزرگ‌تر از ۱ باشد، و اگر `false` باشد، با `sampleCount` برابر با ۱ باشد.

## مثال‌ها

> [!NOTE]
> [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) شامل مثال‌های بسیار بیشتری هستند.

### مثال پایه

[دموی محاسبات پایه](https://mdn.github.io/dom-examples/webgpu-compute-demo/) ما، نمونه‌ای از ایجاد یک طرح‌بندی گروه اتصال و سپس استفاده از آن به‌عنوان قالب هنگام ایجاد یک گروه اتصال را نشان می‌دهد.

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

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)