---
title: "GPUQueue: writeTexture() method"
short-title: writeTexture()
slug: Web/API/GPUQueue/writeTexture
page-type: web-api-instance-method
browser-compat: api.GPUQueue.writeTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`writeTexture()`** از رابط {{domxref("GPUQueue")}} یک منبع دادهٔ ارائه‌شده را در یک {{domxref("GPUTexture")}} معین می‌نویسد.

این یک تابع کمکی است که جایگزینی برای تنظیم داده‌های بافت از طریق نگاشت بافر و کپی‌های بافر‑به‑بافت فراهم می‌کند. این تابع به عامل کاربر اجازه می‌دهد کارآمدترین روش کپی داده‌ها را تعیین کند.

## سینتکس

```js-nolint
writeTexture(destination, data, dataLayout, size)
```

## پارامترها

- `destination`
  - : شیئی است که زیرمنبع بافت و مبدأ نوشتن منبع داده را تعریف می‌کند و می‌تواند ویژگی‌های زیر را داشته باشد:
    - `aspect` {{optional_inline}}
      - : یک مقدار شمارشی که تعیین می‌کند داده به کدام جنبه‌های بافت نوشته شود. مقادیر ممکن عبارت‌اند از:
        - `"all"`
          - : تمام جنبه‌های موجود قالب بافت نوشته خواهد شد؛ بسته به نوع قالبی که با آن سروکار دارید، این می‌تواند شامل همه یا هر یک از جنبه‌های رنگ، عمق و استنسیل باشد.
        - `"depth-only"`
          - : تنها جنبه عمق یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) نوشته خواهد شد.
        - `"stencil-only"`
          - : تنها جنبه استنسیل یک قالب عمق-یا-استنسیل نوشته خواهد شد.

        اگر این ویژگی حذف شود، `aspect` مقدار `"all"` را می‌گیرد.

    - `mipLevel` {{optional_inline}}
      - : عددی است نشان‌دهنده سطح mip-map بافتی که داده به آن نوشته می‌شود. اگر حذف شود، `mipLevel` به‌طور پیش‌فرض 0 خواهد بود.
    - `origin` {{optional_inline}}
      - : یک شیء یا آرایه که مبدأ کپی را مشخص می‌کند — گوشه حداقل ناحیه بافت که داده به آن نوشته می‌شود. همراه با `size`، وسعت کامل ناحیه‌ای که باید به آن کپی شود را تعیین می‌کند. اگر هر یک یا همه مؤلفه‌های `origin` حذف شوند، مقادیر `x`، `y` و `z` به‌طور پیش‌فرض 0 خواهند بود.

        برای مثال، می‌توانید آرایه‌ای مانند `[0, 0, 0]` یا شیء معادل `{ x: 0, y: 0, z: 0 }` را ارسال کنید.

    - `texture`
      - : یک شیء {{domxref("GPUTexture")}} که بافتی را نشان می‌دهد که داده به آن نوشته می‌شود.
- `data`
  - : شیئی است که منبع داده را برای نوشتن در {{domxref("GPUTexture")}} نشان می‌دهد. این می‌تواند یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} باشد.
- `dataLayout`
  - : شیئی است که چیدمان محتوای موجود در `data` را تعریف می‌کند. مقادیر ممکن عبارت‌اند از:
    - `offset` {{optional_inline}}
      - : افست بر حسب بایت، از ابتدای `data` تا شروع داده تصویری که باید کپی شود. اگر حذف شود، `offset` به‌طور پیش‌فرض 0 خواهد بود.
    - `bytesPerRow` {{optional_inline}}
      - : عددی است که فاصله (stride) بر حسب بایت بین شروع هر ردیف بلوک (یعنی ردیفی از بلوک‌های کامل تکسِل) و ردیف بلوک بعدی را نشان می‌دهد. اگر چند ردیف بلوک وجود داشته باشد (یعنی ارتفاع یا عمق کپی بیشتر از یک بلوک باشد)، این ویژگی الزامی است.
    - `rowsPerImage` {{optional_inline}}
      - : تعداد ردیف‌های بلوک برای هر تصویر منفرد بافت. `bytesPerRow` &times; `rowsPerImage` فاصله بر حسب بایت بین شروع هر تصویر کامل را به شما می‌دهد. اگر چند تصویر برای کپی وجود داشته باشد، این ویژگی الزامی است.
- `size`
  - : یک شیء یا آرایه که وسعت کپی را مشخص می‌کند — گوشه دور ناحیه بافت که داده به آن نوشته می‌شود. همراه با `destination.origin`، وسعت کامل ناحیه‌ای که باید به آن کپی شود را تعیین می‌کند. برای نمونه‌هایی از ساختار شیء/آرایه به `destination.origin` مراجعه کنید.

## مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## اعتبارسنجی

هنگام فراخوانی **`writeTexture()`** معیارهای زیر باید برآورده شوند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و {{domxref("GPUQueue")}} نامعتبر می‌گردد:

- `mipLevel` کمتر از {{domxref("GPUTexture.mipLevelCount")}} مقصد باشد.
- `origin.x` مضربی از عرض بلوک تکسِل {{domxref("GPUTexture.format")}} مقصد باشد.
- `origin.y` مضربی از ارتفاع بلوک تکسِل {{domxref("GPUTexture.format")}} مقصد باشد.
- اگر {{domxref("GPUTexture.format")}} مقصد یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) باشد یا {{domxref("GPUTexture.sampleCount")}} بیشتر از 1 باشد، اندازه زیرمنبع باید برابر با `size` باشد.
- {{domxref("GPUTexture.usage")}} مقصد شامل پرچم `GPUTextureUsage.COPY_DST` باشد.
- {{domxref("GPUTexture.sampleCount")}} مقصد برابر 1 باشد.
- `destination.origin.x` + {{domxref("GPUTexture.width")}} مقصد کمتر یا مساوی عرض زیرمنبعی باشد که قرار است در {{domxref("GPUTexture")}} مقصد نوشته شود.
- `destination.origin.y` + {{domxref("GPUTexture.height")}} مقصد کمتر یا مساوی ارتفاع زیرمنبعی باشد که قرار است در {{domxref("GPUTexture")}} مقصد نوشته شود.
- `destination.origin.z` + {{domxref("GPUTexture.depthOrArrayLayers")}} مقصد کمتر یا مساوی depthOrArrayLayers زیرمنبعی باشد که قرار است در {{domxref("GPUTexture")}} مقصد نوشته شود.
- {{domxref("GPUTexture.width")}} مقصد مضربی از عرض بلوک تکسِل {{domxref("GPUTexture.format")}} مقصد باشد.
- {{domxref("GPUTexture.height")}} مقصد مضربی از ارتفاع بلوک تکسِل {{domxref("GPUTexture.format")}} مقصد باشد.
- `destination.aspect` به یک جنبه واحد از {{domxref("GPUTexture.format")}} مقصد اشاره کند.
- آن جنبه طبق [قالب‌های عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) مقصد معتبری برای کپی تصویر باشد.
- از سایر جهات، `destination` باید با {{domxref("GPUTexture.format")}} سازگار باشد.

## مثال‌ها

در [رندر کارآمد مدل‌های glTF](https://toji.github.io/webgpu-gltf-case-study/)، تابعی برای ایجاد یک بافت با رنگ توپر تعریف شده است:

```js
function createSolidColorTexture(r, g, b, a) {
  const data = new Uint8Array([r * 255, g * 255, b * 255, a * 255]);
  const texture = device.createTexture({
    size: { width: 1, height: 1 },
    format: "rgba8unorm",
    usage: GPUTextureUsage.TEXTURE_BINDING | GPUTextureUsage.COPY_DST,
  });
  device.queue.writeTexture({ texture }, data, {}, { width: 1, height: 1 });
  return texture;
}
```

می‌توان از این تابع برای تعریف بافت‌های استاندارد جهت استفاده در کتابخانه‌های متریال بهره برد:

```js
const opaqueWhiteTexture = createSolidColorTexture(1, 1, 1, 1);
const transparentBlackTexture = createSolidColorTexture(0, 0, 0, 0);
const defaultNormalTexture = createSolidColorTexture(0.5, 0.5, 1, 1);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)