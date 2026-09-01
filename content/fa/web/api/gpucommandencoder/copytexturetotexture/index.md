---
title: "GPUCommandEncoder: copyTextureToTexture() method"
short-title: copyTextureToTexture()
slug: Web/API/GPUCommandEncoder/copyTextureToTexture
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.copyTextureToTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}

متد **`copyTextureToTexture()`** از رابط {{domxref("GPUCommandEncoder")}} دستوری را رمزگذاری می‌کند که داده‌ها را از یک {{domxref("GPUTexture")}} به دیگری کپی می‌کند.

## نحو (Syntax)

```js-nolint
copyTextureToTexture(source, destination, copySize)
```

### پارامترها

- `source`
  - : شیئی (به [ساختار شیء کپی بافت](#ساختار-شیء-کپی-بافت) مراجعه کنید) که بافت مبدأ برای کپی داده‌ها را تعریف می‌کند. این شیء به همراه `copySize`، ناحیه‌ی زیرمنبع (subresource) بافت مبدأ را مشخص می‌کند.
- `destination`
  - : شیئی (به [ساختار شیء کپی بافت](#ساختار-شیء-کپی-بافت) مراجعه کنید) که بافت مقصد برای نوشتن داده‌ها را تعریف می‌کند. این شیء به همراه `copySize`، ناحیه‌ی زیرمنبع بافت مقصد را مشخص می‌کند.
- `copySize`
  - : یک شیء یا آرایه که عرض، ارتفاع و تعداد لایه‌های عمق/آرایه را برای داده‌های کپی‌شده مشخص می‌کند. مقدار `width` همیشه باید مشخص شود، در حالی که مقادیر `height` و تعداد لایه‌های عمق/آرایه اختیاری هستند و در صورت حذف، پیش‌فرض ۱ خواهند بود.

    برای مثال، می‌توانید آرایه‌ای مانند `[16, 16, 2]` یا شیء معادل آن `{ width: 16, height: 16, depthOrArrayLayers: 2 }` را عبور دهید.

### ساختار شیء کپی بافت

یک شیء کپی بافت ساختار زیر را دارد:

- `aspect` {{optional_inline}}
  - : یک مقدار شمارشی که مشخص می‌کند کدام جنبه‌های بافت برای کپی داده‌ها مبدأ/مقصد قرار گیرند. مقادیر ممکن عبارت‌اند از:
    - `"all"`
      - : تمام جنبه‌های موجود قالب بافت کپی می‌شوند؛ این می‌تواند همه یا هر کدام از رنگ (color)، عمق (depth) و استنسیل (stencil) باشد، بسته به نوع قالبی که با آن سروکار دارید.
    - `"depth-only"`
      - : فقط جنبه‌ی عمق یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) کپی می‌شود.
    - `"stencil-only"`
      - : فقط جنبه‌ی استنسیل یک قالب عمق-یا-استنسیل کپی می‌شود.

    اگر حذف شود، `aspect` مقدار `"all"` می‌گیرد.

- `mipLevel` {{optional_inline}}
  - : عددی که سطح mip-map بافت را برای کپی داده‌ها از/به آن مشخص می‌کند. اگر حذف شود، `mipLevel` به‌طور پیش‌فرض ۰ است.
- `origin` {{optional_inline}}
  - : یک شیء یا آرایه که مبدأ کپی/مقصد را مشخص می‌کند — گوشه‌ی کمینه‌ی ناحیه‌ی بافت برای کپی داده‌ها از/به آن. همراه با `size`، این مقدار گستره‌ی کامل ناحیه‌ی کپی از/به را تعریف می‌کند. مقادیر `x`، `y` و `z` در صورت حذف `origin` (یا هر بخشی از آن) پیش‌فرض ۰ دارند.

    برای مثال، می‌توانید آرایه‌ای مانند `[0, 0, 0]` یا شیء معادل آن `{ x: 0, y: 0, z: 0 }` را عبور دهید.

- `texture`
  - : یک شیء {{domxref("GPUTexture")}} که بافت مبدأ/مقصد برای کپی داده‌ها را نشان می‌دهد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`copyTextureToTexture()`** معیارهای زیر باید برقرار باشند، در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد شده و {{domxref("GPUCommandEncoder")}} نامعتبر می‌شود.

برای `source`:

- {{domxref("GPUTexture.usage")}} مربوط به `source` شامل پرچم `GPUTextureUsage.COPY_SRC` باشد.

برای `destination`:

- {{domxref("GPUTexture.usage")}} مربوط به `source` شامل پرچم `GPUTextureUsage.COPY_DST` باشد.

برای `source` و `destination`:

- `mipLevel` کمتر از {{domxref("GPUTexture.mipLevelCount")}} باشد.
- `origin.x` مضربی از عرض بلوک تکسِل (texel block) در {{domxref("GPUTexture.format")}} باشد.
- `origin.y` مضربی از ارتفاع بلوک تکسِل در {{domxref("GPUTexture.format")}} باشد.
- {{domxref("GPUTexture.format")}} مربوط به `texture` در مبدأ و مقصد از نظر کپی سازگار باشند.
- {{domxref("GPUTexture.sampleCount")}} مربوط به `texture` در مبدأ و مقصد برابر باشند.
- اگر {{domxref("GPUTexture.format")}} یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) باشد یا {{domxref("GPUTexture.sampleCount")}} بیشتر از ۱ باشد، اندازه‌ی زیرمنبع برابر با `size` باشد.
- {{domxref("GPUTexture.sampleCount")}} مربوط به `texture` برابر ۱ باشد.
- `aspect` به یک جنبه‌ی واحد از {{domxref("GPUTexture.format")}} اشاره کند.
- آن جنبه طبق [قالب‌های عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) یک منبع/مقصد معتبر برای کپی تصویر باشد.
- `texture` با `copySize` سازگار باشد.

## مثال‌ها

```js
commandEncoder.copyTextureToTexture(
  {
    texture: sourceTexture,
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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)