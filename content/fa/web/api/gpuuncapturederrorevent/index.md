---
title: GPUUncapturedErrorEvent
slug: Web/API/GPUUncapturedErrorEvent
page-type: web-api-interface
browser-compat: api.GPUUncapturedErrorEvent
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`GPUUncapturedErrorEvent`** 接口属于 {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}，是 {{domxref("GPUDevice")}} 上 {{domxref("GPUDevice.uncapturederror_event", "uncapturederror")}} 事件的事件对象类型，用于遥测和报告意外错误。

已知的错误情况应使用 {{domxref("GPUDevice.pushErrorScope", "pushErrorScope()")}} 和 {{domxref("GPUDevice.popErrorScope", "popErrorScope()")}} 进行处理。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("GPUUncapturedErrorEvent.GPUUncapturedErrorEvent", "GPUUncapturedErrorEvent()")}}
  - : 创建一个新的 `GPUUncapturedErrorEvent` 对象实例。

## 实例属性

_继承其父类 {{domxref("Event")}} 的属性。_

- {{domxref("GPUUncapturedErrorEvent.error", "error")}} {{ReadOnlyInline}}
  - : 一个 {{domxref("GPUError")}} 对象实例，提供对错误详细信息的访问。

## 示例

你可以使用类似下面的代码作为全局机制，捕获所有未被错误作用域处理的错误。

```js
// …

device.addEventListener("uncapturederror", (event) => {
  // 重新抛出错误
  console.error("一个 WebGPU 错误未被捕获:", event.error.message);
  reportErrorToServer({
    type: event.error.constructor.name,
    message: event.error.message,
  });
});

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
- [WebGPU 错误处理最佳实践](https://toji.dev/webgpu-best-practices/error-handling)