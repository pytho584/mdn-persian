---
title: "GPUShaderModule: getCompilationInfo() method"
short-title: getCompilationInfo()
slug: Web/API/GPUShaderModule/getCompilationInfo
page-type: web-api-instance-method
browser-compat: api.GPUShaderModule.getCompilationInfo
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`getCompilationInfo()`** در رابط {{domxref("GPUShaderModule")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("GPUCompilationInfo")}} شامل پیام‌های تولیدشده در حین کامپایل `GPUShaderModule` تکمیل می‌شود.

## نحو (Syntax)

```js-nolint
getCompilationInfo()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء {{domxref("GPUCompilationInfo")}} تکمیل می‌شود.

{{domxref("GPUCompilationInfo")}} شامل یک ویژگی `messages` است که آرایه‌ای از اشیاء {{domxref("GPUCompilationMessage")}} می‌باشد و هر یک از آن‌ها جزئیات یک پیام کامپایل جداگانه را در بر دارد.

## مثال‌ها

در مثال زیر، ما عمداً یک پرانتز را از اعلان تابع در کد شیدر خود حذف کرده‌ایم:

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

هنگامی که ماژول شیدر را کامپایل می‌کنیم، از `getCompilationInfo()` برای دریافت اطلاعاتی درباره خطای حاصل استفاده می‌کنیم:

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)