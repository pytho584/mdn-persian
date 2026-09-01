---
title: "GPUCommandEncoder: copyBufferToTexture() method"
short-title: copyBufferToTexture()
slug: Web/API/GPUCommandEncoder/copyBufferToTexture
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.copyBufferToTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}

متد **`copyBufferToTexture()`** از رابط {{domxref("GPUCommandEncoder")}} دستوری را رمزگذاری می‌کند که داده‌ها را از یک {{domxref("GPUBuffer")}} به یک {{domxref("GPUTexture")}} کپی می‌کند.

## Syntax

```js-nolint
copyBufferToTexture(source, destination, copySize)
```

### Parameters

- `source`
  - : یک شیء که بافر مبدأ و همچنین چیدمان داده‌های درون بافر که به بافت کپی می‌شوند را تعریف می‌کند. همراه با `copySize`، ناحیه‌ای از بافر مبدأ را مشخص می‌کند. `source` می‌تواند ویژگی‌های زیر را داشته باشد:
    - `buffer`
      - : {{domxref("GPUBuffer")}} مبدأ برای کپی.
    - `offset` {{optional_inline}}
      - : آفست (بر حسب بایت) از ابتدای `data` تا شروع داده‌های تصویری که باید کپی شوند. اگر حذف شود، `offset` به طور پیش‌فرض 0 است.
    - `bytesPerRow` {{optional_inline}}
      - : عددی که گام (stride) بر حسب بایت بین شروع هر ردیف بلوک (یعنی یک ردیف از بلوک‌های کامل تکسِل) و ردیف بلوک بعدی را نشان می‌دهد. اگر چندین ردیف بلوک وجود داشته باشد (یعنی ارتفاع یا عمق کپی بیش از یک بلوک باشد) این پارامتر الزامی است.
    - `rowsPerImage` {{optional_inline}}
      - : تعداد ردیف‌های بلوک در هر تصویر واحد درون داده‌ها. `bytesPerRow` × `rowsPerImage` گام (بر حسب بایت) بین شروع هر تصویر کامل را به شما می‌دهد. اگر چندین تصویر برای کپی وجود داشته باشد، این پارامتر الزامی است.
- `destination`
  - : یک شیء که بافت مقصد را برای نوشتن داده‌ها تعریف می‌کند. همراه با `copySize`، ناحیه‌ای از زیرمنبع بافت مقصد را مشخص می‌کند. `destination` می‌تواند ویژگی‌های زیر را داشته باشد:
    - `aspect` {{optional_inline}}
      - : یک مقدار شمارشی که مشخص می‌کند داده‌ها به کدام جنبه‌های بافت نوشته شوند. مقادیر ممکن عبارتند از:
        - `"all"`
          - : تمام جنبه‌های موجود قالب بافت نوشته می‌شود، که بسته به نوع قالبی که با آن کار می‌کنید، می‌تواند به معنای همه یا هر یک از رنگ، عمق و استنسیل باشد.
        - `"depth-only"`
          - : فقط جنبه عمق یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) نوشته می‌شود.
        - `"stencil-only"`
          - : فقط جنبه استنسیل یک قالب عمق-یا-استنسیل نوشته می‌شود.

        اگر حذف شود، `aspect` مقدار `"all"` می‌گیرد.

    - `mipLevel` {{optional_inline}}
      - : عددی که سطح mip-map بافت مقصد برای نوشتن داده‌ها را نشان می‌دهد. اگر حذف شود، `mipLevel` به طور پیش‌فرض 0 است.
    - `origin` {{optional_inline}}
      - : یک شیء یا آرایه که مبدأ کپی را مشخص می‌کند — کوچک‌ترین گوشه ناحیه بافت برای نوشتن داده‌ها. همراه با `size`، گستره کامل ناحیه کپی را تعریف می‌کند. مقادیر `x`، `y` و `z` در صورت حذف شدن `origin` به طور پیش‌فرض 0 هستند.

        به عنوان مثال، می‌توانید یک آرایه مانند `[0, 0, 0]` یا شیء معادل آن `{ x: 0, y: 0, z: 0 }` را پاس کنید.

    - `texture`
      - : یک شیء {{domxref("GPUTexture")}} که بافت مقصد برای نوشتن داده‌ها را نشان می‌دهد.

- `copySize`
  - : یک شیء یا آرایه که عرض، ارتفاع و تعداد لایه‌های عمق/آرایه داده‌های کپی‌شده را مشخص می‌کند. مقدار عرض همیشه باید مشخص شود، در حالی که ارتفاع و تعداد لایه‌های عمق/آرایه اختیاری هستند و در صورت حذف به طور پیش‌فرض 1 هستند.

    به عنوان مثال، می‌توانید یک آرایه `[16, 16, 2]` یا شیء معادل آن `{ width: 16, height: 16, depthOrArrayLayers: 2 }` را پاس کنید.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Validation

هنگام فراخوانی **`copyBufferToTexture()`**، معیارهای زیر باید رعایت شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و {{domxref("GPUCommandEncoder")}} نامعتبر می‌شود.

برای `source`:

- `source.bytesPerRow` مضربی از 256 است.
- {{domxref("GPUBuffer.usage")}} مربوط به `source.buffer` شامل پرچم `GPUBufferUsage.COPY_SRC` است.

برای `destination`:

- `mipLevel` کمتر از {{domxref("GPUTexture.mipLevelCount")}} است.
- `origin.x` مضربی از عرض بلوک تکسِل {{domxref("GPUTexture.format")}} است.
- `origin.y` مضربی از ارتفاع بلوک تکسِل {{domxref("GPUTexture.format")}} است.
- اگر {{domxref("GPUTexture.format")}} یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) باشد یا {{domxref("GPUTexture.sampleCount")}} بیشتر از 1 باشد، اندازه زیرمنبع برابر با `size` است.
- {{domxref("GPUTexture.usage")}} مربوط به `destination` شامل پرچم `GPUTextureUsage.COPY_DST` است.
- {{domxref("GPUTexture.sampleCount")}} مربوط به `destination` برابر با 1 است.
- `destination.aspect` به یک جنبه واحد از {{domxref("GPUTexture.format")}} اشاره می‌کند.
- آن جنبه یک مقصد معتبر برای کپی تصویر مطابق با [قالب‌های عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) است.
- `destination` با `copySize` سازگار است.

## Examples

```js
commandEncoder.copyBufferToTexture(
  {
    buffer: sourceBuffer,
  },
  {
    texture: destinationTexture,
  },
  {
    width: 16,
    height: 16,
    depthOrArrayLayers: 2,
  },
);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)