---
title: "GPUCanvasContext: configure() method"
short-title: configure()
slug: Web/API/GPUCanvasContext/configure
page-type: web-api-instance-method
browser-compat: api.GPUCanvasContext.configure
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`configure()`** از رابط {{domxref("GPUCanvasContext")}}، بافت (context) را برای استفاده در رندرینگ با یک {{domxref("GPUDevice")}} مشخص پیکربندی می‌کند. هنگام فراخوانی، بوم (canvas) ابتدا به رنگ مشکی شفاف پاک می‌شود.

## نحو (Syntax)

```js-nolint
configure(configuration)
```

### پارامترها

- `configuration`
  - : یک شیء حاوی ویژگی‌های زیر:
    - `alphaMode` {{optional_inline}}
      - : یک مقدار شمارشی که تأثیر مقادیر آلفا را بر محتوای بافت‌های بازگردانده شده توسط {{domposxref("GPUCanvasContext.getCurrentTexture()", "getCurrentTexture()")}} هنگام خواندن، نمایش یا استفاده به عنوان منبع تصویر مشخص می‌کند. مقادیر ممکن عبارتند از:
        - `opaque`: مقادیر آلفا نادیده گرفته می‌شوند – اگر بافت از قبل مات نباشد، کانال آلفا هنگام استفاده به عنوان منبع تصویر یا نمایش روی صفحه به ۱.۰ پاک می‌شود. این مقدار پیش‌فرض است.
        - `premultiplied`: مقادیر رنگ در مقدار آلفا ضرب می‌شوند. برای مثال، قرمز ۱۰۰٪ با آلفای ۵۰٪ برابر است با `[0.5, 0, 0, 0.5]`.
    - `colorSpace` {{optional_inline}}
      - : فضای رنگی که مقادیر نوشته شده در بافت‌های بازگردانده شده توسط `getCurrentTexture()` باید با آن نمایش داده شوند. مقادیر ممکن عبارتند از `srgb` (پیش‌فرض) و `display-p3`.
    - `device`
      - : {{domxref("GPUDevice")}}ای که اطلاعات رندرینگ مربوط به بافت از آن می‌آید.
    - `format`
      - : قالبی که بافت‌های بازگردانده شده توسط `getCurrentTexture()` خواهند داشت. این می‌تواند `bgra8unorm`، `rgba8unorm` یا `rgba16float` باشد. قالب بهینه بافت بوم برای سیستم فعلی را می‌توان با {{domxref("GPU.getPreferredCanvasFormat()")}} به دست آورد. استفاده از این توصیه می‌شود – اگر هنگام پیکربندی بافت بوم از قالب ترجیحی استفاده نکنید، ممکن است سربار اضافی مانند کپی بافت اضافی، بسته به پلتفرم، داشته باشید.
    - `toneMapping` {{optional_inline}}
      - : یک شیء که پارامترهای تعریف‌کننده تن‌مپینگ (نقشه‌ی تن) برای بافت را مشخص می‌کند – نحوه نمایش محتوای بافت‌های مرتبط. این به WebGPU اجازه می‌دهد رنگ‌هایی روشن‌تر از `white` (`#FFFFFF`) را ترسیم کند. ویژگی‌های ممکن:
        - `mode` {{optional_inline}}
          - : یک مقدار شمارشی که حالت تن‌مپینگ برای بوم را مشخص می‌کند. مقادیر ممکن عبارتند از:
            - `standard`
              - : مقدار پیش‌فرض. محتوای رندر شده را به محدوده دینامیک استاندارد (SDR) نمایش محدود می‌کند. این حالت با محدود کردن تمام مقادیر رنگ در فضای رنگی صفحه به بازه `[0, 1]` انجام می‌شود.
            - `extended`
              - : اجازه می‌دهد محتوا در محدوده دینامیک بالا (HDR) کامل نمایش، در صورت موجود بودن، رندر شود. حالت HDR امکان نمایش طیف وسیع‌تری از رنگ‌ها و سطوح روشنایی را با دستورالعمل‌های دقیق‌تر در مورد رنگ مورد نمایش در هر مورد فراهم می‌کند. این حالت در بازه `[0, 1]` صفحه با حالت `"standard"` مطابقت دارد. برش یا طرح‌ریزی (clamping or projection) به محدوده دینامیک گسترده صفحه انجام می‌شود، نه `[0, 1]`.
    - `usage` {{optional_inline}}
      - : {{glossary("Bitwise flags")}} که استفاده مجاز برای بافت‌های بازگردانده شده توسط `getCurrentTexture()` را مشخص می‌کند. مقادیر ممکن عبارتند از:
        - `GPUTextureUsage.COPY_SRC`: بافت می‌تواند به عنوان منبع یک عملیات کپی استفاده شود، برای مثال آرگومان منبع یک فراخوانی {{domxref("GPUCommandEncoder.copyTextureToBuffer()")}}.
        - `GPUTextureUsage.COPY_DST`: بافت می‌تواند به عنوان مقصد یک عملیات کپی/نوشتن استفاده شود، برای مثال آرگومان مقصد یک فراخوانی {{domxref("GPUCommandEncoder.copyTextureToTexture()")}}.
        - `GPUTextureUsage.RENDER_ATTACHMENT`: بافت می‌تواند به عنوان پیوست رنگ (color attachment) در یک پاس رندر استفاده شود، برای مثال در نمای پیوست رنگ در یک فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}}. `GPUTextureUsage.RENDER_ATTACHMENT` مقدار پیش‌فرض `usage` است، اما توجه داشته باشید که اگر مقدار متفاوتی به صراحت تنظیم شود، به طور خودکار شامل نمی‌شود؛ در چنین مواردی باید آن را علاوه بر موارد دیگر اضافه کنید.
        - `GPUTextureUsage.TEXTURE_BINDING`: بافت می‌تواند برای استفاده به عنوان بافت نمونه‌برداری شده (sampled texture) در یک شیدر متصل شود، برای مثال در یک ورودی گروه اتصال در یک فراخوانی {{domxref("GPUDevice.createBindGroup()")}}.
        - `GPUTextureUsage.STORAGE_BINDING`: بافت می‌تواند برای استفاده به عنوان بافت ذخیره‌سازی (storage texture) در یک شیدر متصل شود، برای مثال در یک ورودی گروه اتصال در یک فراخوانی {{domxref("GPUDevice.createBindGroup()")}}.

        توجه داشته باشید که می‌توان چندین استفاده ممکن را با استفاده از [عملگر OR بیتی](/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR) مشخص کرد. برای مثال: `usage: GPUTextureUsage.COPY_SRC | GPUTextureUsage.RENDER_ATTACHMENT`.
    - `viewFormats` {{optional_inline}}
      - : آرایه‌ای از قالب‌هایی که نماهای ایجاد شده از بافت‌های بازگردانده شده توسط `getCurrentTexture()` ممکن است استفاده کنند. برای همه مقادیر ممکن به [فرمت‌های بافت](https://gpuweb.github.io/gpuweb/#texture-formats) مراجعه کنید.

### مقدار بازگشتی

هیچ‌کدام (`undefined`).

### استثناها

- `TypeError` {{domxref("DOMException")}}
  - : اگر `usage` شامل بیت `TRANSIENT_ATTACHMENT` باشد پرتاب می‌شود.

## مثال‌ها

### استفاده پایه

```js
const canvas = document.querySelector("#gpuCanvas");
const context = canvas.getContext("webgpu");

context.configure({
  device,
  format: navigator.gpu.getPreferredCanvasFormat(),
  alphaMode: "premultiplied",
});
```

### نمایش‌های `toneMapping` HDR

نمونه [Particles (HDR)](https://webgpu.github.io/webgpu-samples/?sample=particles) و آزمایش [پشتیبانی HDR](https://ccameron-chromium.github.io/webgpu-hdr/example.html) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API WebGPU](/en-US/docs/Web/API/WebGPU_API)