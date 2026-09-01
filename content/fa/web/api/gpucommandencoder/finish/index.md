---
title: "GPUCommandEncoder: finish() method"
short-title: finish()
slug: Web/API/GPUCommandEncoder/finish
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.finish
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`finish()`** 方法属于 {{domxref("GPUCommandEncoder")}} 接口，用于完成在此 `GPUCommandEncoder` 上编码的命令序列的记录，并返回对应的 {{domxref("GPUCommandBuffer")}}。

## 语法

```js-nolint
finish()
finish(descriptor)
```

### 参数

- `descriptor` {{optional_inline}}
  - : 一个对象，可以包含以下属性：
    - `label` {{optional_inline}}
      - : 一个字符串，为返回的 {{domxref("GPUCommandBuffer")}} 提供标签，可用于标识它，例如在 {{domxref("GPUError")}} 消息或控制台警告中。

### 返回值

一个 {{domxref("GPUCommandBuffer")}} 对象实例。

### 验证

调用 **`finish()`** 时必须满足以下条件，否则会生成 {{domxref("GPUValidationError")}}，并且该 {{domxref("GPUCommandEncoder")}} 将变为无效：

- 没有活动的调试组（即通过 {{domxref("GPUCommandEncoder.pushDebugGroup", "pushDebugGroup()")}} 启动的调试组）。
- {{domxref("GPUCommandEncoder")}} 处于打开状态——这意味着：
  - 没有尚未结束（通过调用 `end()`）的子级 {{domxref("GPUComputePassEncoder")}} 或 {{domxref("GPURenderPassEncoder")}} 处于活动状态。
  - 尚未在该 {{domxref("GPUCommandEncoder")}} 上调用过 `finish()`（如果已经调用过，则不能再用于编码任何命令）。

## 示例

```js
// …

const commandBuffer = commandEncoder.finish();
device.queue.submit([commandBuffer]);

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)