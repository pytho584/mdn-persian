---
title: "GPUDevice: createPipelineLayout() method"
short-title: createPipelineLayout()
slug: Web/API/GPUDevice/createPipelineLayout
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createPipelineLayout
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createPipelineLayout()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPUPipelineLayout")}} (طرح خط لوله) ایجاد می‌کند که {{domxref("GPUBindGroupLayout")}}های (طرح‌های گروه اتصال) مورد استفاده توسط یک خط لوله (pipeline) را تعریف می‌کند. {{domxref("GPUBindGroup")}}هایی (گروه‌های اتصال) که در هنگام رمزگذاری دستورات با خط لوله استفاده می‌شوند باید دارای {{domxref("GPUBindGroupLayout")}}های سازگار باشند.

## Syntax

```js-nolint
createPipelineLayout(descriptor)
```

### پارامترها

- `descriptor`
  - : یک شیء حاوی ویژگی‌های زیر:
    - `bindGroupLayouts`
      - : آرایه‌ای از مقادیر که نشان‌دهنده طرح‌های گروه اتصال برای یک خط لوله هستند. هر مقدار می‌تواند:
        - یک شیء {{domxref("GPUBindGroupLayout")}} (طرح گروه اتصال) که با فراخوانی {{domxref("GPUDevice.createBindGroupLayout()")}} ایجاد شده است. هر شیء معادل یک ویژگی [`@group`](https://gpuweb.github.io/gpuweb/wgsl/#attribute-binding) در کد شیدر موجود در {{domxref("GPUShaderModule")}} مورد استفاده در یک خط لوله مرتبط است.
        - `null`، که نشان‌دهنده یک طرح گروه اتصال خالی است. مقادیر `null` هنگام ایجاد یک طرح خط لوله نادیده گرفته می‌شوند.
    - `label` {{optional_inline}}
      - : یک رشته که یک برچسب برای شناسایی شیء فراهم می‌کند، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("GPUPipelineLayout")}} (طرح خط لوله).

### اعتبارسنجی

معیارهای زیر باید هنگام فراخوانی **`createPipelineLayout()`** برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و یک شیء {{domxref("GPUPipelineLayout")}} نامعتبر بازگردانده می‌شود:

- اشیاء {{domxref("GPUBindGroupLayout")}} (طرح گروه اتصال) در `bindGroupLayouts` معتبر هستند.
- تعداد اشیاء {{domxref("GPUBindGroupLayout")}} در `bindGroupLayouts` کمتر از `maxBindGroups` {{domxref("GPUDevice")}} (محدودیت {{domxref("GPUSupportedLimits", "limit", "", "nocode")}}) است.

## مثال‌ها

> [!NOTE]
> [نمونه‌های WebGPU](https://webgpu.github.io/webgpu-samples/) شامل مثال‌های بیشتری هستند.

### چندین طرح گروه اتصال، گروه اتصال و طرح خط لوله

قطعه کد زیر:

- یک {{domxref("GPUBindGroupLayout")}} (طرح گروه اتصال) ایجاد می‌کند که یک اتصال با یک بافر، یک بافت و یک نمونه‌بردار را توصیف می‌کند.
- یک {{domxref("GPUPipelineLayout")}} (طرح خط لوله) بر اساس {{domxref("GPUBindGroupLayout")}} ایجاد می‌کند.

```js
// …

const bindGroupLayout = device.createBindGroupLayout({
  entries: [
    {
      binding: 0,
      visibility: GPUShaderStage.VERTEX | GPUShaderStage.FRAGMENT,
      buffer: {},
    },
    {
      binding: 1,
      visibility: GPUShaderStage.FRAGMENT,
      texture: {},
    },
    {
      binding: 2,
      visibility: GPUShaderStage.FRAGMENT,
      sampler: {},
    },
  ],
});

const pipelineLayout = device.createPipelineLayout({
  bindGroupLayouts: [bindGroupLayout],
});

// …
```

### مشخص کردن یک طرح گروه اتصال خالی

در این قطعه، سه طرح گروه اتصال ایجاد می‌کنیم، که طرح گروه اتصال ۱ نشان‌دهنده داده‌های قطعه و طرح گروه اتصال ۲ نشان‌دهنده داده‌های رأس است. اگر بخواهیم یک خط لوله ایجاد کنیم که فقط از طرح‌های گروه اتصال ۰ و ۲ استفاده کند، می‌توانیم برای طرح گروه اتصال ۱ مقدار `null` را ارسال کرده و سپس بدون شیدر قطعه رندر کنیم.

```js
const bgl0 = device.createBindGroupLayout({ entries: myGlobalEntries });
const bgl1 = device.createBindGroupLayout({ entries: myFragmentEntries });
const bgl2 = device.createBindGroupLayout({ entries: myVertexEntries });

// pipeline layout can be used to render without a fragment shader
const pipelineLayout = device.createPipelineLayout({
  bindGroupLayouts: [bgl0, null, bgl2],
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)