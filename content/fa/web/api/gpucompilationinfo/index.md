---
title: GPUCompilationInfo
slug: Web/API/GPUCompilationInfo
page-type: web-api-interface
browser-compat: api.GPUCompilationInfo
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUCompilationInfo`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} یک آرایه از اشیاء {{domxref("GPUCompilationMessage")}} را نشان می‌دهد که توسط کامپایلر ماژول شیدر GPU برای کمک به تشخیص مشکلات کد شیدر تولید می‌شود.

`GPUCompilationInfo` از طریق {{domxref("GPUShaderModule.getCompilationInfo()")}} قابل دسترسی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUCompilationInfo.messages", "messages")}} {{ReadOnlyInline}}
  - : آرایه‌ای از اشیاء {{domxref("GPUCompilationMessage")}}، که هر کدام جزئیات یک پیام کامپایل شیدر جداگانه را شامل می‌شود. پیام‌ها می‌توانند اطلاعاتی، هشدار یا خطا باشند.

## مثال‌ها

در مثال زیر، ما عمداً یک پرانتز را از اعلان یک تابع در کد شیدر خود حذف کرده‌ایم:

```js
const shaders = `
struct VertexOut {
  @builtin(position) position : vec4f,
  @location(0) color : vec4f
}

@vertex
fn vertex_main(@location(0) position: vec4f,
               @location(1) color: vec4f -> VertexOut
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
```

هنگامی که ماژول شیدر را کامپایل می‌کنیم، از `getCompilationInfo()` برای دریافت اطلاعاتی در مورد خطای به‌وجودآمده استفاده می‌کنیم:

```js
async function init() {
  // …

  const shaderModule = device.createShaderModule({
    code: shaders,
  });

  const shaderInfo = await shaderModule.getCompilationInfo();
  const firstMessage = shaderInfo.messages[0];

  console.log(firstMessage.lineNum); // 9
  console.log(firstMessage.message); // "expected ')' for function declaration"
  console.log(firstMessage.type); // "error"
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)