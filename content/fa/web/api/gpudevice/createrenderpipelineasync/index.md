---
title: "GPUDevice: createRenderPipelineAsync() method"
short-title: createRenderPipelineAsync()
slug: Web/API/GPUDevice/createRenderPipelineAsync
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createRenderPipelineAsync
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createRenderPipelineAsync()`** از رابط {{domxref("GPUDevice")}} یک {{jsxref("Promise}} برمی‌گرداند که با یک {{domxref("GPURenderPipeline")}} تحقق می‌یابد. این شیء می‌تواند مراحل سایه‌زن رأس و قطعه را کنترل کند و در یک {{domxref("GPURenderPassEncoder")}} یا {{domxref("GPURenderBundleEncoder")}} استفاده شود، به شرطی که پایپ‌لاین بدون هیچ تأخیری قابل استفاده باشد.

> [!NOTE]
> به طور کلی ترجیح داده می‌شود تا حد امکان از این متد به جای {{domxref("GPUDevice.createRenderPipeline()")}} استفاده شود، زیرا از مسدود شدن اجرای عملیات GPU در هنگام کامپایل پایپ‌لاین جلوگیری می‌کند.

## Syntax

```js-nolint
createRenderPipelineAsync(descriptor)
```

### Parameters

- `descriptor`
  - : تعریف توصیف‌کننده را برای متد [`GPUDevice.createRenderPipeline()`](/en-US/docs/Web/API/GPUDevice/createRenderPipeline#syntax) ببینید.

### Return value

یک {{jsxref("Promise")}} که با یک نمونه از شیء {{domxref("GPURenderPipeline")}} تحقق می‌یابد زمانی که پایپ‌لاین ایجاد شده آماده استفاده بدون تأخیر اضافی باشد.

### Validation

اگر ایجاد پایپ‌لاین ناموفق باشد و در نتیجه پایپ‌لاین حاصل نامعتبر شود، promise برگشتی با یک {{domxref("GPUPipelineError")}} رد می‌شود:

- اگر این به دلیل یک خطای داخلی باشد، {{domxref("GPUPipelineError")}} دارای `reason` برابر با `"internal"` خواهد بود.
- اگر این به دلیل یک خطای اعتبارسنجی باشد، {{domacro("GPUPipelineError")}} دارای `reason` برابر با `"validation"` خواهد بود.

یک خطای اعتبارسنجی می‌تواند در صورت نادرست بودن هر یک از موارد زیر رخ دهد:

- برای اشیاء `depthStencil`:
  - `format` یک فرمت [`depth-or-stencil`](https://gpuweb.github.io/gpuweb/#depth-or-stencil-format) است.
  - ویژگی‌های [`depthBias`](/en-US/docs/Web/API/GPUDevice/createRenderPipeline#depthbias)، [`depthBiasClamp`](/en-US/docs/Web/API/GPUDevice/createRenderPipeline#depthbiasclamp) و [`depthBiasSlopeScale`](/en-US/docs/Web/API/GPUDevice/createRenderPipeline#depthbiasslopescale) برای توپولوژی‌های خط و نقطه (یعنی اگر [`topology`](/en-US/docs/Web/API/GPUDevice/createRenderPipeline#topology) برابر با `"line-list"`، `"line-strip"` یا `"point-list"` باشد) روی <code>0</code> تنظیم شده‌اند.
  - اگر `depthWriteEnabled` `true` باشد یا `depthCompare` `"always"` نباشد، `format` یک مؤلفه عمق دارد.
  - اگر ویژگی‌های `stencilFront` یا `stencilBack` در مقادیر پیش‌فرض خود نباشند، `format` یک مؤلفه شابلون دارد.
- برای اشیاء `fragment`:
  - `targets.length` کمتر یا مساوی با {{domxref("GPUDevice")}}'s `maxColorAttachments` {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} است.
  - برای هر `target`، معادل عددی `WriteMask` کمتر از 16 است.
  - اگر هر یک از عملیات‌های عامل ترکیب استفاده شده از کانال آلفای منبع استفاده کنند (مثلاً `"src-alpha-saturated"`)، خروجی دارای یک کانال آلفا است (یعنی باید یک `vec4` باشد).
  - اگر ویژگی `entryPoint` حذف شود، کد سایه‌زن شامل یک تابع نقطه ورود سایه‌زن قطعه واحد برای استفاده مرورگر به عنوان نقطه ورود پیش‌فرض است.
- برای اشیاء `primitive`:
  - اگر ویژگی `unclippedDepth` استفاده شود، ویژگی `depth-clip-control` [feature](/en-US/docs/Web/API/GPUSupportedFeatures) فعال است.
- برای اشیاء `vertex`:
  - اگر ویژگی `entryPoint` حذف شود، کد سایه‌زن شامل یک تابع نقطه ورود سایه‌زن رأس واحد برای استفاده مرورگر به عنوان نقطه ورود پیش‌فرض است.

## Examples

> [!NOTE]
> نمونه‌های [WebGPU samples](https://webgpu.github.io/webgpu-samples/) شامل مثال‌های بسیار بیشتری هستند.

### Basic example

مثال زیر یک نمونه ساده از ساخت یک شیء توصیف‌کننده پایپ‌لاین رندر معتبر را نشان می‌دهد که سپس برای ایجاد یک {{domxref("GPURenderPipeline")}} از طریق فراخوانی `createRenderPipelineAsync()` استفاده می‌شود.

```js
async function init() {
  // …

  const vertexBuffers = [
    {
      attributes: [
        {
          shaderLocation: 0, // position
          offset: 0,
          format: "float32x4",
        },
        {
          shaderLocation: 1, // color
          offset: 16,
          format: "float32x4",
        },
      ],
      arrayStride: 32,
      stepMode: "vertex",
    },
  ];

  const pipelineDescriptor = {
    vertex: {
      module: shaderModule,
      entryPoint: "vertex_main",
      buffers: vertexBuffers,
    },
    fragment: {
      module: shaderModule,
      entryPoint: "fragment_main",
      targets: [
        {
          format: navigator.gpu.getPreferredCanvasFormat(),
        },
      ],
    },
    primitive: {
      topology: "triangle-list",
    },
    layout: "auto",
  };

  const renderPipeline =
    await device.createRenderPipelineAsync(pipelineDescriptor);

  // …
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [رابط WebGPU API](/en-US/docs/Web/API/WebGPU_API)