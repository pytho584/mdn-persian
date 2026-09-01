---
title: "GPURenderBundleEncoder: popDebugGroup() method"
short-title: popDebugGroup()
slug: Web/API/GPURenderBundleEncoder/popDebugGroup
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.popDebugGroup
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`popDebugGroup()`** 方法用于结束一个渲染捆绑包调试组，该调试组通过调用 {{domxref("GPURenderBundleEncoder.pushDebugGroup", "pushDebugGroup()")}} 开始。

此方法可用于遥测，也可能在未来被用于 {{domxref("GPUError")}} 消息、浏览器开发者工具或其他服务中，以辅助调试。

> [!NOTE]
> 此方法与 {{domxref("GPURenderPassEncoder")}} 上对应的 {{domxref("GPURenderPassEncoder.popDebugGroup", "popDebugGroup()")}} 在功能上完全相同。

## 语法

```js-nolint
popDebugGroup()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

### 验证

调用 **`popDebugGroup()`** 时必须满足以下条件，否则会生成一个 {{domxref("GPUValidationError")}}，并且该 {{domxref("GPURenderBundleEncoder")}} 将变为无效：

- 渲染捆绑包编码器的调试堆栈不为空（即至少有一个渲染捆绑包调试组先前通过 {{domxref("GPURenderBundleEncoder.pushDebugGroup", "pushDebugGroup()")}} 启动）。

## 示例

```js
// …

const bundleEncoder = device.createRenderBundleEncoder(renderBundleDescriptor);

bundleEncoder.pushDebugGroup("my_group_marker"); // 开始带标签的调试组

bundleEncoder.setPipeline(renderPipeline);
bundleEncoder.setVertexBuffer(0, vertexBuffer);
bundleEncoder.draw(3);

bundleEncoder.popDebugGroup();

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)