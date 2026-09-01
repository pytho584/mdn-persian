---
title: "GPUDevice: destroy() method"
short-title: destroy()
slug: Web/API/GPUDevice/destroy
page-type: web-api-instance-method
browser-compat: api.GPUDevice.destroy
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`destroy()`** 方法是 {{domxref("GPUDevice")}} 接口的一个方法，用于销毁设备，阻止在其上执行进一步的操作。

请注意：

- 当前已排入设备 {{domxref("GPUQueue")}} 队列的所有命令都将在设备销毁之前执行。
- 使用该设备创建的所有 WebGPU 资源（如缓冲区、纹理等）也将被销毁。
- 使用该设备创建的任何已映射缓冲区都将被取消映射。

## 语法

```js-nolint
destroy()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  let device = await adapter.requestDevice();

  // Some time later

  device.destroy();
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)