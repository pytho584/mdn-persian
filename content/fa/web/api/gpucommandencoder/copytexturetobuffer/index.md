---
title: "GPUCommandEncoder: copyTextureToBuffer() method"
short-title: copyTextureToBuffer()
slug: Web/API/GPUCommandEncoder/copyTextureToBuffer
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.copyTextureToBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}

متد **`copyTextureToBuffer()`** از رابط {{domxref("GPUCommandEncoder")}} دستوری را رمزگذاری می‌کند که داده‌ها را از یک {{domxref("GPUTexture")}} به یک {{domxref("GPUBuffer")}} کپی می‌کند.

## نحو (Syntax)

```js-nolint
copyTextureToBuffer(source, destination, copySize)
```

### پارامترها

- `source`
  - : شیئی که بافت مبدأ برای کپی داده‌ها را تعریف می‌کند. همراه با `copySize`، ناحیه‌ی زیرمنبع (subresource) بافت مبدأ را مشخص می‌کند. `source` می‌تواند ویژگی‌های زیر را داشته باشد:
    - `aspect` {{optional_inline}}
      - : یک مقدار شمارشی (enumerated value) که مشخص می‌کند کدام جنبه‌های (aspects) بافت برای کپی داده‌ها استفاده شوند. مقادیر ممکن عبارتند از:
        - `"all"`
          - : تمام جنبه‌های موجود از قالب بافت کپی می‌شوند. بسته به نوع قالبی که با آن سروکار دارید، این می‌تواند شامل رنگ (color)، عمق (depth)، و استنسیل (stencil) باشد.
        - `"depth-only"`
          - : تنها جنبه‌ی عمق از یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) کپی می‌شود.
        - `"stencil-only"`
          - : تنها جنبه‌ی استنسیل از یک قالب عمق-یا-استنسیل کپی می‌شود.

        اگر حذف شود، `aspect` مقدار `"all"` را می‌گیرد.

    - `mipLevel` {{optional_inline}}
      - : عددی که سطح mip-map بافت مبدأ را برای کپی داده‌ها مشخص می‌کند. اگر حذف شود، `mipLevel` به‌طور پیش‌فرض 0 است.
    - `origin` {{optional_inline}}
      - : یک شیء یا آرایه که مبدأ کپی را مشخص می‌کند — گوشه‌ی حداقلی ناحیه‌ی بافت برای کپی داده‌ها. همراه با `size`، کل وسعت ناحیه‌ای که از آن کپی می‌شود را تعریف می‌کند. اگر `origin` به طور کامل یا جزئی حذف شود، مقادیر `x`، `y` و `z` به‌طور پیش‌فرض 0 هستند.

        به عنوان مثال، می‌توانید آرایه‌ی `[0, 0, 0]` یا معادل شیء آن `{ x: 0, y: 0, z: 0 }` را عبور دهید.

    - `texture`
      - : یک شیء {{domxref("GPUTexture")}} که بافت مبدأ را برای کپی داده‌ها نشان می‌دهد.

- `destination`
  - : شیئی که بافر مقصد برای نوشتن داده‌ها و همچنین چیدمان (layout) داده‌هایی که در بافر نوشته می‌شوند را تعریف می‌کند. همراه با `copySize`، ناحیه‌ی بافر مقصد را مشخص می‌کند. `destination` می‌تواند ویژگی‌های زیر را داشته باشد:
    - `buffer`
      - : {{domxref("GPUBuffer")}} که داده‌ها در آن نوشته می‌شوند.
    - `offset` {{optional_inline}}
      - : افست، بر حسب بایت، از ابتدای `data` تا موقعیت شروع برای نوشتن داده‌های کپی‌شده. اگر حذف شود، `offset` به‌طور پیش‌فرض 0 است.
    - `bytesPerRow` {{optional_inline}}
      - : عددی که گام (stride)، بر حسب بایت، بین شروع هر ردیف بلوکی (block row) (یعنی ردیفی از بلوک‌های کامل تکسِل) و ردیف بلوکی بعدی را مشخص می‌کند. این مقدار در صورت وجود چندین ردیف بلوکی (یعنی ارتفاع یا عمق کپی بیشتر از یک بلوک باشد) الزامی است.
    - `rowsPerImage` {{optional_inline}}
      - : تعداد ردیف‌های بلوکی در هر تصویر واحد درون داده‌ها. `bytesPerRow` &times; `rowsPerImage` گام، بر حسب بایت، بین شروع هر تصویر کامل را به شما می‌دهد. این مقدار در صورت وجود چندین تصویر برای کپی الزامی است.

- `copySize`
  - : یک شیء یا آرایه که عرض، ارتفاع، و تعداد لایه‌های عمق/آرایه (depth/array layer count) داده‌های کپی‌شده را مشخص می‌کند. مقدار عرض همیشه باید مشخص شود، در حالی که ارتفاع و تعداد لایه‌های عمق/آرایه اختیاری هستند و در صورت حذف، به‌طور پیش‌فرض 1 خواهند بود.

    به عنوان مثال، می‌توانید آرایه‌ی `[16, 16, 2]` یا معادل شیء آن `{ width: 16, height: 16, depthOrArrayLayers: 2 }` را عبور دهید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

معیارهای زیر باید هنگام فراخوانی **`copyTextureToBuffer()`** برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPUCommandEncoder")}} نامعتبر می‌شود.

برای `source`:

- `mipLevel` کمتر از {{domxref("GPUTexture.mipLevelCount")}} است.
- `origin.x` مضربی از عرض بلوک تکسِل {{domxref("GPUTexture.format")}} است.
- `origin.y` مضربی از ارتفاع بلوک تکسِل {{domxref("GPUTexture.format")}} است.
- اگر {{domxref("GPUTexture.format")}} یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) باشد یا {{domxref("GPUTexture.sampleCount")}} بیشتر از 1 باشد، اندازه‌ی زیرمنبع برابر با `size` است.
- {{domxref("GPUTexture.usage")}} مربوط به `source` شامل پرچم `GPUTextureUsage.COPY_SRC` است.
- {{domxref("GPUTexture.sampleCount")}} مربوط به `source` برابر با 1 است.
- `source.aspect` به یک جنبه‌ی واحد از {{domxref("GPUTexture.format")}} اشاره می‌کند.
- آن جنبه طبق [قالب‌های عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) یک منبع کپی تصویر معتبر است.
- `source` با `copySize` سازگار است.

برای `destination`:

- `destination.bytesPerRow` مضربی از 256 است.
- {{domxref("GPUBuffer.usage")}} مربوط به `destination.buffer` شامل پرچم `GPUBufferUsage.COPY_DST` است.

## مثال‌ها

```js
commandEncoder.copyTextureToBuffer(
  {
    texture: sourceTexture,
  },
  {
    buffer: destinationBuffer,
  },
  {
    width: 16,
    height: 16,
    depthOrArrayLayers: 2,
  },
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)