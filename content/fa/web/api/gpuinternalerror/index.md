---
title: "GPUInternalError"
---

---
title: GPUInternalError
slug: Web/API/GPUInternalError
page-type: web-api-interface
browser-compat: api.GPUInternalError
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`GPUInternalError`** 接口属于 {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}，用于描述一种应用错误，表示即使所有验证要求都已满足，操作仍因系统或实现特有的原因而失败。

它是 {{domxref("GPUDevice.popErrorScope")}} 和 {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} 事件所暴露的错误类型之一。

内部错误发生在 WebGPU 实现中出现了未被验证捕获、且无法明确归类为内存不足错误的情况。它通常意味着你代码执行的操作触及了系统限制，而这种限制难以用 WebGPU 的[支持的限制](/en-US/docs/Web/API/GPUSupportedLimits)来表达。相同的操作在另一台设备上可能会成功。此类错误通常只在管线创建时出现，尤其是当着色器对于设备来说过于复杂时。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("GPUInternalError.GPUInternalError", "GPUInternalError()")}}
  - : 创建一个新的 `GPUInternalError` 对象实例。

## 实例属性

`message` 属性继承自其父接口 {{domxref("GPUError")}}：

- {{domxref("GPUError.message", "message")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : 一个字符串，提供人类可读的消息，说明错误发生的原因。

## 示例

以下示例使用错误作用域来捕获可能存在的验证错误，并将其记录到控制台。

```js
device.pushErrorScope("internal");

let module = device.createShaderModule({
  code: shader, // REALLY complex shader
});

device.popErrorScope().then((error) => {
  if (error) {
    // error is a GPUInternalError object instance
    module = null;
    console.error(`An error occurred while creating shader: ${error.message}`);
  }
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [WebGPU 错误处理最佳实践](https://toji.dev/webgpu-best-practices/error-handling)