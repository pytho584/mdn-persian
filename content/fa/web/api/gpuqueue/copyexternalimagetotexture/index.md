---
title: "GPUQueue: copyExternalImageToTexture() method"
short-title: copyExternalImageToTexture()
slug: Web/API/GPUQueue/copyExternalImageToTexture
page-type: web-api-instance-method
browser-compat: api.GPUQueue.copyExternalImageToTexture
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`copyExternalImageToTexture()`** از رابط {{domxref("GPUQueue")}} یک عکس فوری گرفته‌شده از یک تصویر، ویدیو یا بوم (canvas) را در یک {{domxref("GPUTexture")}} مشخص کپی می‌کند.

استفاده از این تابع به عامل کاربر (user agent) اجازه می‌دهد کارآمدترین روش کپی داده‌ها را برای هر نوع منبع تعیین کند.

## نحو (Syntax)

```js-nolint
copyExternalImageToTexture(source, destination, copySize)
```

### پارامترها

- `source`
  - : یک شیء که منبع داده‌ای که باید در مقصد نوشته شود و مبدأ آن را نشان می‌دهد. این شیء می‌تواند ویژگی‌های زیر را داشته باشد:
    - `source`
      - : یک شیء که منبع عکس فوری را برای کپی فراهم می‌کند. این می‌تواند یک {{domxref("HTMLCanvasElement")}}، {{domxref("HTMLImageElement")}}، {{domxref("HTMLVideoElement")}}، {{domxref("ImageBitmap")}}، {{domxref("ImageData")}}، {{domxref("OffscreenCanvas")}} یا {{domxref("VideoFrame")}} باشد. داده‌های تصویر منبع دقیقاً در همان لحظه‌ای که `copyExternalImageToTexture()` فراخوانی می‌شود، ضبط می‌گردند.
    - `origin` {{optional_inline}}
      - : یک شیء یا آرایه که مبدأ کپی را مشخص می‌کند — گوشه‌ی بالا-چپ زیرناحیه‌ی منبع که باید از آن کپی شود. این مقدار به همراه `copySize`، کل محدوده‌ی زیرناحیه‌ی منبع را تعیین می‌کند. اگر `origin` به طور کلی یا جزئی حذف شود، مقادیر `x` و `y` به‌صورت پیش‌فرض 0 خواهند بود.

        برای مثال، می‌توانید آرایه‌ای مانند `[0, 0]` یا شیء معادل آن `{ x: 0, y: 0 }` را منتقل کنید.

    - `flipY` {{optional_inline}}
      - : یک مقدار بولین. اگر `true` تنظیم شود، تصویر گرفته‌شده به صورت عمودی برعکس می‌شود. اگر حذف شود، `flipY` به‌صورت پیش‌فرض `false` است.

- `destination`
  - : یک شیء که زیرمنبع بافت (texture subresource) و مبدأ نوشتن تصویر گرفته‌شده را تعریف می‌کند، به همراه فراداده‌ی رمزگذاری. این شیء می‌تواند ویژگی‌های زیر را داشته باشد:
    - `aspect` {{optional_inline}}
      - : یک مقدار شمارشی (enumerated value) که مشخص می‌کند کدام جنبه‌های بافت باید تصویر در آن‌ها نوشته شود. مقادیر ممکن عبارتند از:
        - `"all"`
          - : همه‌ی جنبه‌های موجود قالب بافت نوشته می‌شوند، که بسته به نوع قالبی که با آن سروکار دارید می‌تواند همه یا هر یک از جنبه‌های رنگ (color)، عمق (depth) و استنسیل (stencil) باشد.
        - `"depth-only"`
          - : فقط جنبه‌ی عمق یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) نوشته می‌شود.
        - `"stencil-only"`
          - : فقط جنبه‌ی استنسیل یک قالب عمق-یا-استنسیل نوشته می‌شود.

        اگر حذف شود، `aspect` مقدار `"all"` را می‌گیرد.

    - `colorSpace` {{optional_inline}}
      - : یک مقدار شمارشی که فضای رنگی و رمزگذاری مورد استفاده برای رمزگذاری داده‌ها در بافت مقصد را توصیف می‌کند. مقادیر ممکن `"srgb"` و `"display-p3"` هستند. اگر حذف شود، `colorSpace` به‌صورت پیش‌فرض `"srgb"` است.

        > [!NOTE]
        > رمزگذاری ممکن است منجر به نوشته‌شدن مقادیری خارج از بازه‌ی `[0, 1]` در بافت هدف شود، اگر قالب آن بتواند آن‌ها را نمایش دهد. در غیر این صورت، نتایج به محدوده‌ی قالب بافت هدف محدود (clamp) می‌شوند. اگر `colorSpace` با فضای رنگی تصویر منبع مطابقت داشته باشد، ممکن است تبدیل لازم نباشد.

    - `mipLevel` {{optional_inline}}
      - : یک عدد که سطح mip-map بافتی را که تصویر باید در آن نوشته شود مشخص می‌کند. اگر حذف شود، `mipLevel` به‌صورت پیش‌فرض 0 است.
    - `origin` {{optional_inline}}
      - : یک شیء یا آرایه که مبدأ کپی را مشخص می‌کند — کمترین گوشه‌ی ناحیه‌ی بافت که داده‌های تصویر باید در آن نوشته شوند. این مقدار به همراه `copySize`، کل محدوده‌ی ناحیه‌ای که باید به آن کپی شود را تعریف می‌کند. اگر `origin` به طور کلی یا جزئی حذف شود، مقادیر `x`، `y` و `z` به‌صورت پیش‌فرض 0 خواهند بود.

        برای مثال، می‌توانید آرایه‌ای مانند `[0, 0, 0]` یا شیء معادل آن `{ x: 0, y: 0, z: 0 }` را منتقل کنید.

    - `premultipliedAlpha` {{optional_inline}}
      - : یک مقدار بولین. اگر `true` تنظیم شود، داده‌های تصویر نوشته‌شده در بافت دارای کانال‌های RGB هستند که در کانال آلفا ضرب (premultiply) شده‌اند. اگر حذف شود، `premultipliedAlpha` به‌صورت پیش‌فرض `false` است.

        > [!NOTE]
        > اگر این گزینه `true` باشد و `source` نیز premultiplied باشد، مقادیر RGB منبع باید حفظ شوند حتی اگر از مقادیر آلفای مربوطه فراتر روند.

    - `texture`
      - : یک شیء {{domxref("GPUTexture")}} که بافتی را که داده‌ها باید در آن نوشته شوند نشان می‌دهد.

- `copySize`
  - : یک شیء یا آرایه که `width`، `height` و `depthOrArrayLayers` ناحیه‌ی مورد نظر برای کپی از/به را مشخص می‌کند.

    برای مثال، می‌توانید آرایه‌ای مانند `[16, 1, 1]` یا شیء معادل آن `{ width: 16, height: 1, depthOrArrayLayers: 1 }` را منتقل کنید.

    مقدار `width` باید حتماً گنجانده شود. اگر مقادیر `height` یا `depthOrArrayLayers` حذف شوند، به‌صورت پیش‌فرض 1 هستند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `OperationError` {{domxref("DOMException")}}
  - : این متد یک `OperationError` پرتاب می‌کند اگر معیارهای زیر برآورده نشوند:
    - `source.origin.x` + عرض ناحیه‌ی مورد نظر برای کپی، کمتر یا مساوی عرض تصویر منبع باشد.
    - `source.origin.y` + ارتفاع ناحیه‌ی مورد نظر برای کپی، کمتر یا مساوی ارتفاع تصویر منبع باشد.
    - `source.origin.z` + depthOrArrayLayers ناحیه‌ی مورد نظر برای کپی، کمتر یا مساوی 1 باشد.
    - `dataOffset` کوچک‌تر یا مساوی اندازه‌ی `data` باشد.
    - اندازه‌ی `data` (هنگامی که در مورد `TypedArray`ها به بایت تبدیل شود) مضربی از 4 باشد.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر داده‌های تصویر منبع دارای مبدأ متقاطع (cross-origin) باشند، پرتاب می‌شود.

### اعتبارسنجی

معیارهای زیر باید هنگام فراخوانی **`writeTexture()`** برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPUQueue")}} نامعتبر می‌شود:

- `mipLevel` کمتر از {{domxref("GPUTexture.mipLevelCount")}} مقصد باشد.
- `origin.x` مضربی از عرض بلوک تکسِل (texel block width) قالب {{domxref("GPUTexture.format")}} مقصد باشد.
- `origin.y` مضربی از ارتفاع بلوک تکسِل قالب {{domxref("GPUTexture.format")}} مقصد باشد.
- اگر قالب {{domxref("GPUTexture.format")}} مقصد یک [قالب عمق-یا-استنسیل](https://gpuweb.github.io/gpuweb/#combined-depth-stencil-format) باشد، اندازه‌ی تصویر گرفته‌شده برابر با `size` باشد.
- {{domxref("GPUTexture.usage")}} مقصد شامل پرچم‌های `GPUTextureUsage.COPY_DST` و `GPUTextureUsage.RENDER_ATTACHMENT` باشد.
- {{domxref("GPUTexture.dimension")}} مقصد `"2d"` باشد.
- {{domxref("GPUTexture.sampleCount")}} مقصد 1 باشد.
- {{domxref("GPUTexture.format")}} مقصد یکی از موارد زیر باشد (که از کاربرد `GPUTextureUsage.RENDER_ATTACHMENT` پشتیبانی می‌کنند):
  - `"r8unorm"`
  - `"r16float"`
  - `"r32float"`
  - `"rg8unorm"`
  - `"rg16float"`
  - `"rg32float"`
  - `"rgba8unorm"`
  - `"rgba8unorm-srgb"`
  - `"bgra8unorm"`
  - `"bgra8unorm-srgb"`
  - `"rgb10a2unorm"`
  - `"rgba16float"`
  - `"rgba32float"`
- `destination.origin.x` + `copySize.width` کمتر یا مساوی {{domxref("GPUTexture.width", "width")}} بافت {{domxref("GPUTexture")}} مقصد باشد.
- `destination.origin.y` + `copySize.height` کمتر یا مساوی {{domxref("GPUTexture.height", "height")}} بافت {{domxref("GPUTexture")}} مقصد باشد.
- `destination.origin.z` + `copySize.depthOrArrayLayers` کمتر یا مساوی {{domxref("GPUTexture.depthOrArrayLayers", "depthOrArrayLayers")}} بافت {{domxref("GPUTexture")}} مقصد باشد.
- {{domxref("GPUTexture.width")}} مقصد مضربی از عرض بلوک تکسِل قالب {{domxref("GPUTexture.format")}} مقصد باشد.
- {{domxref("GPUTexture.height")}} مقصد مضربی از ارتفاع بلوک تکسِل قالب {{domxref("GPUTexture.format")}} مقصد باشد.

## مثال‌ها

در نمونه‌ی [Textured Cube](https://webgpu.github.io/webgpu-samples/samples/texturedCube/) از نمونه‌های WebGPU، از قطعه‌کد زیر برای دریافت یک تصویر و بارگذاری آن در یک {{domxref("GPUTexture")}} استفاده شده است:

```js
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
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API WebGPU](/en-US/docs/Web/API/WebGPU_API)