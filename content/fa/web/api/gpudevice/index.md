---
title: "GPUDevice"
---

---
title: GPUDevice
slug: Web/API/GPUDevice
page-type: web-api-interface
browser-compat: api.GPUDevice
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUDevice`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک دستگاه GPU منطقی را نمایش می‌دهد. این رابط اصلی است که از طریق آن بیشتر قابلیت‌های WebGPU در دسترس قرار می‌گیرند.

یک شیء `GPUDevice` با استفاده از متد {{domxref("GPUAdapter.requestDevice()")}} درخواست می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

ویژگی‌های والد خود، {{DOMxRef("EventTarget")}} را به ارث می‌برد.

- {{domxref("GPUDevice.adapterInfo", "adapterInfo")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GPUAdapterInfo")}} حاوی اطلاعات شناسایی دربارهٔ آداپتور مبدأ دستگاه.

- {{domxref("GPUDevice.features", "features")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GPUSupportedFeatures")}} که قابلیت‌های اضافی پشتیبانی‌شده توسط دستگاه را توصیف می‌کند.

- {{domxref("GPUDevice.label", "label")}}
  - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

- {{domxref("GPUDevice.limits", "limits")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GPUSupportedLimits")}} که محدودیت‌های پشتیبانی‌شده توسط دستگاه را توصیف می‌کند.

- {{domxref("GPUDevice.lost", "lost")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} را نگه می‌دارد که در تمام طول عمر دستگاه در حالت pending باقی می‌ماند و هنگام از دست رفتن دستگاه، با یک شیء {{domxref("GPUDeviceLostInfo")}} حل می‌شود.

- {{domxref("GPUDevice.queue", "queue")}} {{ReadOnlyInline}}
  - : صف اصلی {{domxref("GPUQueue")}} دستگاه را بازمی‌گرداند.

## روش‌های نمونه

روش‌های والد خود، {{DOMxRef("EventTarget")}} را به ارث می‌برد.

- {{domxref("GPUDevice.createBindGroup", "createBindGroup()")}}
  - : یک {{domxref("GPUBindGroup")}} بر اساس یک {{domxref("GPUBindGroupLayout")}} ایجاد می‌کند که مجموعه‌ای از منابع را که باید با هم در یک گروه پیوند داده شوند و نحوه استفاده از آن منابع در مراحل شیدر را تعریف می‌کند.

- {{domxref("GPUDevice.createBindGroupLayout", "createBindGroupLayout()")}}
  - : یک {{domxref("GPUBindGroupLayout")}} ایجاد می‌کند که ساختار و هدف منابع GPU مرتبط، مانند بافرهایی که در پایپلاین استفاده می‌شوند را تعریف می‌کند و هنگام ایجاد {{domxref("GPUBindGroup")}}ها به‌عنوان الگو به کار می‌رود.

- {{domxref("GPUDevice.createBuffer", "createBuffer()")}}
  - : یک {{domxref("GPUBuffer")}} برای ذخیره داده‌های خام جهت استفاده در عملیات GPU ایجاد می‌کند.

- {{domxref("GPUDevice.createCommandEncoder", "createCommandEncoder()")}}
  - : یک {{domxref("GPUCommandEncoder")}} ایجاد می‌کند که برای رمزگذاری دستوراتی که به GPU ارسال می‌شوند استفاده می‌شود.

- {{domxref("GPUDevice.createComputePipeline", "createComputePipeline()")}}
  - : یک {{domxref("GPUComputePipeline")}} ایجاد می‌کند که می‌تواند مرحله شیدر محاسباتی را کنترل کند و در یک {{domxref("GPUComputePassEncoder")}} استفاده شود.

- {{domxref("GPUDevice.createComputePipelineAsync", "createComputePipelineAsync()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با یک {{domxref("GPUComputePipeline")}} fulfilled می‌شود؛ این شیء می‌تواند مرحله شیدر محاسباتی را کنترل کند و در یک {{domxref("GPUComputePassEncoder")}} استفاده شود، به محض اینکه بتوان از پایپلاین بدون هیچ وقفه‌ای استفاده کرد.

- {{domxref("GPUDevice.createPipelineLayout", "createPipelineLayout()")}}
  - : یک {{domxref("GPUPipelineLayout")}} ایجاد می‌کند که {{domxref("GPUBindGroupLayout")}}های استفاده‌شده توسط یک پایپلاین را تعریف می‌کند. {{domxref("GPUBindGroup")}}هایی که در هنگام رمزگذاری دستورات با پایپلاین استفاده می‌شوند باید دارای {{domxref("GPUBindGroupLayout")}}های سازگار باشند.

- {{domxref("GPUDevice.createQuerySet", "createQuerySet()")}}
  - : یک {{domxref("GPUQuerySet")}} ایجاد می‌کند که می‌توان از آن برای ثبت نتایج پرس‌وجوها روی passها، مانند پرس‌وجوهای انسداد (occlusion) یا زمان‌سنج (timestamp)، استفاده کرد.

- {{domxref("GPUDevice.createRenderBundleEncoder", "createRenderBundleEncoder()")}}
  - : یک {{domxref("GPURenderBundleEncoder")}} ایجاد می‌کند که می‌توان از آن برای ضبط از پیشِ دسته‌هایی از دستورات استفاده کرد. این دسته‌ها را می‌توان از طریق متد {{domxref("GPURenderPassEncoder.executeBundles", "executeBundles()")}} در {{domxref("GPURenderPassEncoder")}}ها، هر چند بار که لازم باشد، مجدداً استفاده کرد.

- {{domxref("GPUDevice.createRenderPipeline", "createRenderPipeline()")}}
  - : یک {{domxref("GPURenderPipeline")}} ایجاد می‌کند که می‌تواند مراحل شیدر رأس (vertex) و قطعه (fragment) را کنترل کند و در یک {{domxref("GPURenderPassEncoder")}} یا {{domxref("GPURenderBundleEncoder")}} استفاده شود.

- {{domxref("GPUDevice.createRenderPipelineAsync", "createRenderPipelineAsync()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با یک {{domxref("GPURenderPipeline")}} fulfilled می‌شود؛ این شیء می‌تواند مراحل شیدر رأس و قطعه را کنترل کند و در یک {{domxref("GPURenderPassEncoder")}} یا {{domxref("GPURenderBundleEncoder")}} استفاده شود، به محض اینکه بتوان از پایپلاین بدون هیچ وقفه‌ای استفاده کرد.

- {{domxref("GPUDevice.createSampler", "createSampler()")}}
  - : یک {{domxref("GPUSampler")}} ایجاد می‌کند که نحوه تبدیل و فیلتر کردن داده‌های منبع بافت توسط شیدرها را کنترل می‌کند.

- {{domxref("GPUDevice.createShaderModule", "createShaderModule()")}}
  - : یک {{domxref("GPUShaderModule")}} از رشته‌ای از کد منبع WGSL ایجاد می‌کند.

- {{domxref("GPUDevice.createTexture", "createTexture()")}}
  - : یک {{domxref("GPUTexture")}} برای ذخیره داده‌های بافت جهت استفاده در عملیات رندر GPU ایجاد می‌کند.

- {{domxref("GPUDevice.destroy", "destroy()")}}
  - : دستگاه را از بین می‌برد و از انجام عملیات بیشتر روی آن جلوگیری می‌کند.

- {{domxref("GPUDevice.importExternalTexture", "importExternalTexture()")}}
  - : یک {{domxref("HTMLVideoElement")}} را به‌عنوان ورودی می‌گیرد و یک شیء پوششی {{domxref("GPUExternalTexture")}} بازمی‌گرداند که شامل یک عکس فوری (snapshot) از ویدیو است و می‌توان از آن در عملیات رندر GPU استفاده کرد.

- {{domxref("GPUDevice.popErrorScope", "popErrorScope()")}}
  - : یک محدوده خطای GPU موجود را از پشته محدوده خطا خارج می‌کند و یک {{jsxref("Promise")}} بازمی‌گرداند که به یک شیء ({{domxref("GPUInternalError")}}، {{domxref("GPUOutOfMemoryError")}} یا {{domxref("GPUValidationError")}}) که اولین خطای ضبط‌شده در آن محدوده را توصیف می‌کند، حل می‌شود؛ یا اگر خطایی رخ نداده باشد، به `null` حل می‌شود.

- {{domxref("GPUDevice.pushErrorScope", "pushErrorScope()")}}
  - : یک محدوده خطای GPU جدید به پشته محدوده خطای دستگاه اضافه می‌کند و به شما امکان می‌دهد خطاهای یک نوع خاص را ضبط کنید.

## رویدادها

- {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}}
  - : هنگامی که خطایی رخ می‌دهد که توسط محدوده خطای GPU مشاهده نشده است، برای فراهم کردن راهی برای گزارش خطاهای غیرمنتظره، شلیک می‌شود. موارد خطای شناخته‌شده باید با استفاده از {{domxref("GPUDevice.pushErrorScope", "pushErrorScope()")}} و {{domxref("GPUDevice.popErrorScope", "popErrorScope()")}} مدیریت شوند.

## مثال‌ها

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  const device = await adapter.requestDevice();

  const shaderModule = device.createShaderModule({
    code: shaders,
  });

  // …
}
```

برای نمونه‌های بسیار بیشتری از استفاده از `GPUDevice`، به صفحات اعضای جداگانهٔ فهرست‌شده در بالا و وب‌سایت‌های نمایشی زیر مراجعه کنید:

- [نمایش ساده محاسباتی](https://mdn.github.io/dom-examples/webgpu-compute-demo/)
- [نمایش ساده رندر](https://mdn.github.io/dom-examples/webgpu-render-demo/)
- [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/)

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)