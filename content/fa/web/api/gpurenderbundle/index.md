---
title: GPURenderBundle
slug: Web/API/GPURenderBundle
page-type: web-api-interface
browser-compat: api.GPURenderBundle
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`GPURenderBundle`** 接口属于 {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}，表示一个用于存储预先录制的命令包（bundle）的容器。

这些命令包使用 {{domxref("GPURenderBundleEncoder")}} 进行编码；一旦所需命令编码完成，它们会通过 {{domxref("GPURenderBundleEncoder.finish()")}} 方法记录到 `GPURenderBundle` 对象实例中。

随后，这些命令包可以通过将 `GPURenderBundle` 对象传入 {{domxref("GPURenderPassEncoder.executeBundles()")}} 调用，在多个渲染通道中重复使用。在 JavaScript 绘制调用开销成为瓶颈的情况下，重用预先录制的命令可以显著提升应用性能。当一批对象在多个视图或帧中以相同方式绘制，且唯一的差异是所使用的缓冲内容（例如更新后的矩阵 uniform）时，渲染包最为有效。

一个典型示例是 VR 渲染。将渲染过程录制为渲染包，然后调整视图矩阵并为每只眼睛重放，是向场景的两次渲染发出绘制调用的更高效方式。

{{InheritanceDiagram}}

## 实例属性

- {{domxref("GPURenderBundle.label", "label")}}
  - : 一个字符串，提供可用于标识对象的标签，例如在 {{domxref("GPUError")}} 消息或控制台警告中。

## 示例

在 WebGPU 示例 [Animometer 示例](https://webgpu.github.io/webgpu-samples/samples/animometer/) 中，许多类似的操作会在多个不同对象上同时执行。渲染包通过以下函数进行编码：

```js
function recordRenderPass(
  passEncoder: GPURenderBundleEncoder | GPURenderPassEncoder
) {
  if (settings.dynamicOffsets) {
    passEncoder.setPipeline(dynamicPipeline);
  } else {
    passEncoder.setPipeline(pipeline);
  }
  passEncoder.setVertexBuffer(0, vertexBuffer);
  passEncoder.setBindGroup(0, timeBindGroup);
  const dynamicOffsets = [0];
  for (let i = 0; i < numTriangles; ++i) {
    if (settings.dynamicOffsets) {
      dynamicOffsets[0] = i * alignedUniformBytes;
      passEncoder.setBindGroup(1, dynamicBindGroup, dynamicOffsets);
    } else {
      passEncoder.setBindGroup(1, bindGroups[i]);
    }
    passEncoder.draw(3, 1, 0, 0);
  }
}
```

之后，创建一个 {{domxref("GPURenderBundleEncoder")}}，调用该函数，并使用 {{domxref("GPURenderBundleEncoder.finish()")}} 记录渲染包：

```js
const renderBundleEncoder = device.createRenderBundleEncoder({
  colorFormats: [presentationFormat],
});
recordRenderPass(renderBundleEncoder);
const renderBundle = renderBundleEncoder.finish();
```

然后使用 {{domxref("GPURenderPassEncoder.executeBundles()")}} 在多个渲染通道中重用这些工作以提升性能。请参阅示例代码列表以获取完整上下文。

```js
// …

return function doDraw(timestamp) {
  if (startTime === undefined) {
    startTime = timestamp;
  }
  uniformTime[0] = (timestamp - startTime) / 1000;
  device.queue.writeBuffer(uniformBuffer, timeOffset, uniformTime.buffer);

  renderPassDescriptor.colorAttachments[0].view = context
    .getCurrentTexture()
    .createView();

  const commandEncoder = device.createCommandEncoder();
  const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

  if (settings.renderBundles) {
    passEncoder.executeBundles([renderBundle]);
  } else {
    recordRenderPass(passEncoder);
  }

  passEncoder.end();
  device.queue.submit([commandEncoder.finish()]);
};

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)