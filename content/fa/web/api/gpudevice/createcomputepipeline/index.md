---
title: "GPUDevice: createComputePipeline() method"
short-title: createComputePipeline()
slug: Web/API/GPUDevice/createComputePipeline
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createComputePipeline
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createComputePipeline()`** از رابط {{domxref("GPUDevice")}} یک شیء {{domxref("GPUComputePipeline")}} می‌سازد که می‌تواند مرحله‌ی شیدر محاسباتی را کنترل کند و در یک {{domxref("GPUComputePassEncoder")}} استفاده شود.

## نحو (Syntax)

```js-nolint
createComputePipeline(descriptor)
```

### پارامترها

- `descriptor`
  - : یک شیء شامل ویژگی‌های زیر:
    - `compute`
      - : یک شیء که نقطه‌ی ورود شیدر محاسباتی خط لوله را توصیف می‌کند. این شیء می‌تواند ویژگی‌های زیر را داشته باشد:
        - `constants` {{optional_inline}}
          - : دنباله‌ای از انواع رکورد، با ساختار `(id, value)`، که مقادیر جایگزینی را برای [ثابت‌های WGSL که می‌توانند در خط لوله جایگزین شوند](https://gpuweb.github.io/gpuweb/#typedefdef-gpupipelineconstantvalue) نمایش می‌دهند. این مقادیر مانند [نقشه‌های مرتب](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) رفتار می‌کنند. در هر مورد، `id` کلیدی است که برای شناسایی یا انتخاب رکورد استفاده می‌شود و `constant` یک مقدار شمارشی است که یک WGSL را نمایش می‌دهد.

            بسته به اینکه کدام ثابت را می‌خواهید جایگزین کنید، `id` ممکن است به شکل شناسه‌ی عددی ثابت (در صورت مشخص بودن) یا در غیر این صورت نام شناسه‌ی ثابت باشد.

            یک قطعه کد که مقادیر جایگزینی را برای چند ثابت قابل جایگزینی فراهم می‌کند ممکن است به این شکل باشد:

            ```js
            ({
              // …
              constants: {
                0: false,
                1200: 3.0,
                1300: 2.0,
                width: 20,
                depth: -1,
                height: 15,
              },
            });
            ```

        - `entryPoint` {{optional_inline}}
          - : نام تابعی در `module` که این مرحله برای انجام کار خود از آن استفاده خواهد کرد. تابع شیدر مربوطه باید ویژگی `@compute` داشته باشد تا به عنوان این نقطه‌ی ورود شناسایی شود. برای اطلاعات بیشتر به [اعلام نقطه‌ی ورود](https://gpuweb.github.io/gpuweb/wgsl/#entry-point-decl) مراجعه کنید.

            اگر کد شیدر شما فقط یک تابع با ویژگی `@compute` داشته باشد، می‌توانید ویژگی `entryPoint` را حذف کنید — مرورگر از این تابع به عنوان نقطه‌ی ورود پیش‌فرض استفاده خواهد کرد. اگر `entryPoint` حذف شود و مرورگر نتواند نقطه‌ی ورود پیش‌فرضی را تعیین کند، یک {{domxref("GPUValidationError")}} ایجاد می‌شود و {{domxref("GPUComputePipeline")}} حاصل نامعتبر خواهد بود.

        - `module`
          - : یک شیء {{domxref("GPUShaderModule")}} شامل کد [WGSL](https://gpuweb.github.io/gpuweb/wgsl/) که این مرحله‌ی برنامه‌پذیر اجرا خواهد کرد.

    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `layout`
      - : چیدمان (ساختار، هدف و نوع) همه‌ی منابع GPU (بافرها، بافت‌ها و غیره) را که در طول اجرای خط لوله استفاده می‌شوند، تعریف می‌کند. مقادیر احتمالی عبارتند از:
        - یک شیء {{domxref("GPUPipelineLayout")}} که با {{domxref("GPUDevice.createPipelineLayout()")}} ساخته شده است، که به GPU اجازه می‌دهد از قبل بفهمد چگونه خط لوله را به کارآمدترین شکل اجرا کند.
        - رشته‌ی `"auto"` که باعث می‌شود خط لوله یک چیدمان گروه اتصال ضمنی بر اساس هر binding تعریف‌شده در کد شیدر ایجاد کند. اگر از `"auto"` استفاده شود، چیدمان‌های گروه اتصال تولیدشده فقط با خط لوله‌ی فعلی قابل استفاده هستند.

### مقدار بازگشتی

یک شیء {{domxref("GPUComputePipeline")}}.

### اعتبارسنجی

هنگام فراخوانی **`createComputePipeline()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} ایجاد شده و یک شیء {{domxref("GPUComputePipeline")}} نامعتبر بازگردانده می‌شود:

- اندازه‌ی فضای ذخیره‌سازی workgroup استفاده‌شده توسط `module` ارجاع‌شده در ویژگی `compute` کمتر یا برابر با {{domxref("GPUDevice")}}'s `maxComputeWorkgroupStorageSize` {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} باشد.
- `module` از تعداد فراخوانی محاسباتی در هر workgroup کمتر یا برابر با {{domxref("GPUDevice")}}'s `maxComputeInvocationsPerWorkgroup` {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} استفاده کند.
- اندازه‌ی workgroup در `module` کمتر یا برابر با {{domxref("GPUDevice")}}'s متناظر `maxComputeWorkgroupSizeX`، `maxComputeWorkgroupSizeY` یا `maxComputeWorkgroupSizeZ` {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} باشد.
- اگر ویژگی `entryPoint` حذف شود، کد شیدر فقط یک تابع نقطه‌ی ورود شیدر محاسباتی داشته باشد تا مرورگر از آن به عنوان نقطه‌ی ورود پیش‌فرض استفاده کند.

## مثال‌ها

> [!NOTE]
> [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) مثال‌های بسیار بیشتری دارند.

### مثال پایه

[نمونه‌ی محاسبات پایه‌ی ما](https://mdn.github.io/dom-examples/webgpu-compute-demo/) فرآیند زیر را نشان می‌دهد:

- ایجاد یک چیدمان گروه اتصال با {{domxref("GPUDevice.createBindGroupLayout()")}}.
- انتقال `bindGroupLayout` به {{domxref("GPUDevice.createPipelineLayout()")}} برای ایجاد یک {{domxref("GPUPipelineLayout")}}.
- استفاده از آن مقدار مستقیماً در فراخوانی `createComputePipeline()` برای ایجاد یک {{domxref("GPUComputePipeline")}}.

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

const computePipeline = device.createComputePipeline({
  layout: device.createPipelineLayout({
    bindGroupLayouts: [bindGroupLayout],
  }),
  compute: {
    module: shaderModule,
    entryPoint: "main",
  },
});

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)