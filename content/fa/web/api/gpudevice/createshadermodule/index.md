---
title: "GPUDevice: createShaderModule() method"
short-title: createShaderModule()
slug: Web/API/GPUDevice/createShaderModule
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createShaderModule
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createShaderModule()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPUShaderModule")}} را از رشتهای از کد منبع [WGSL](https://gpuweb.github.io/gpuweb/wgsl/) می‌سازد.

## سینتکس

```js-nolint
createShaderModule(descriptor)
```

### پارامترها

- `descriptor`
  - : یک شیء که شامل ویژگی‌های زیر است:
    - `code`
      - : یک رشته که کد منبع WGSL ماژول شیدر را نمایش می‌دهد.
    - `hints` {{optional_inline}}
      - : یک توالی از نوع‌های رکورد با ساختار `("string", compilationHint)`. این‌ها مانند [ordered maps](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) رفتار می‌کنند. در هر مورد، `"string"` کلیدی برای شناسایی یا انتخاب رکورد است و `compilationHint` یا یک نمونهٔ شیء {{domxref("GPUPipelineLayout")}} است یا یک مقدار شمارشی `"auto"`.

        هدف `hints` ارائهٔ اطلاعات دربارهٔ چیدمان پایپلاین در اولین فرصت ممکن برای بهبود عملکرد است. ایده این است که میزان کامپایلی که می‌توان توسط `createShaderModule()` یک‌بار انجام داد بیشینه شود، به‌جای اینکه این کار چندین بار در فراخوانی‌های متعدد {{domxref("GPUDevice.createComputePipeline()")}} و {{domxref("GPUDevice.createRenderPipeline()")}} تکرار شود.

        > [!NOTE]
        > پیاده‌سازی‌های مختلف ممکن است `hints` را به شکل‌های متفاوتی پردازش کنند، از جمله اینکه کلاً آن‌ها را نادیده بگیرند. ارائهٔ `hints` تضمین نمی‌کند که عملکرد کامپایل شیدر در همهٔ مرورگرها/سیستم‌ها بهبود یابد.

    - `label` {{optional_inline}}
      - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند؛ مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `sourceMap` {{optional_inline}}
      - : یک تعریف source map برای فراهم کردن یکپارچگی با ابزارهای توسعه‌دهنده مانند اشکال‌زدایی در زبان مبدأ. نام‌های WGSL (شناسه‌ها) در source mapها باید از قواعد تعریف‌شده در [WGSL identifier comparison](https://gpuweb.github.io/gpuweb/wgsl/#identifier-comparison) پیروی کنند. اگر تعریف شده باشد، source map ممکن است به‌صورت [source-map-v3 format](https://tc39.es/ecma426/) تفسیر شود.

        > [!NOTE]
        > پیاده‌سازی‌های مختلف ممکن است `sourceMap`ها را به شکل‌های متفاوتی پردازش کنند، از جمله اینکه کلاً آن‌ها را نادیده بگیرند.

### مقدار بازگشتی

یک نمونهٔ شیء {{domxref("GPUShaderModule")}}.

### اعتبارسنجی

معیارهای زیر باید هنگام فراخوانی **`createShaderModule()`** برآورده شوند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و یک شیء نامعتبر {{domxref("GPUShaderModule")}} بازگردانده می‌شود:

- اگر کد WGSL شیدر شما از نوع ممیز شناور نیمه‌دقیق [`f16`](https://gpuweb.github.io/gpuweb/wgsl/#extension-f16) استفاده می‌کند، باید شامل `enable f16;` در ابتدای کد باشد و {{domxref("GPUDevice")}} مرتبط با فعال بودن [feature](/en-US/docs/Web/API/GPUSupportedFeatures) به نام `shader-f16` ساخته شده باشد.

### مثال‌ها

در [basic render demo](https://mdn.github.io/dom-examples/webgpu-render-demo/) خود، ماژول شیدر با استفاده از کد زیر ایجاد می‌شود:

```js
const shaders = `
struct VertexOut {
  @builtin(position) position : vec4f,
  @location(0) color : vec4f
}

@vertex
fn vertex_main(@location(0) position: vec4f,
               @location(1) color: vec4f) -> VertexOut
{
  var output : VertexOut;
  output.position = position;
  output.color = color;
  return output;
}

@fragment
fn fragment_main(fragData: VertexOut) -> @location(0) vec4f
{
  return fragData.color;
}
`;

async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  const device = await adapter.requestDevice();

  // …
  // later on

  const shaderModule = device.createShaderModule({
    code: shaders,
  });

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [WebGPU Shading Language specification](https://gpuweb.github.io/gpuweb/wgsl/)