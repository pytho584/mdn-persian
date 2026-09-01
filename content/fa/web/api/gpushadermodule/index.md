```
---
title: "GPUShaderModule"
slug: Web/API/GPUShaderModule
page-type: web-api-interface
browser-compat: api.GPUShaderModule
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابطِ **`GPUShaderModule`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}، یک شیءِ ماژول سایه‌زن داخلی را نشان می‌دهد؛ محفظه‌ای برای کد سایه‌زن [WGSL](https://gpuweb.github.io/gpuweb/wgsl/) که می‌تواند برای اجرا توسط یک پایپ‌لاین به GPU ارسال شود.

یک نمونه از شیءِ `GPUShaderModule` با استفاده از {{domxref("GPUDevice.createShaderModule()")}} ساخته می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUShaderModule.label", "label")}}
  - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند؛ مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

## روش‌های نمونه

- {{domxref("GPUShaderModule.getCompilationInfo", "getCompilationInfo()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("GPUCompilationInfo")}} شامل پیام‌های تولیدشده در طول کامپایلِ `GPUShaderModule` تکمیل می‌شود.

## مثال‌ها

در [نمونه‌ی رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، ماژول سایه‌زن با استفاده از کد زیر ساخته می‌شود:

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
```