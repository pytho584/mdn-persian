---
title: "GPURenderBundleEncoder: drawIndirect() method"
short-title: drawIndirect()
slug: Web/API/GPURenderBundleEncoder/drawIndirect
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.drawIndirect
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`drawIndirect()`** 方法属于 {{domxref("GPURenderBundleEncoder")}} 接口，它使用从 {{domxref("GPUBuffer")}} 读取的参数来绘制图元。

> [!NOTE]
> 此方法与其在 {{domxref("GPURenderPassEncoder")}} 上的对应方法——{{domxref("GPURenderPassEncoder.drawIndirect", "drawIndirect()")}} 功能完全相同。

## 语法

```js-nolint
drawIndirect(indirectBuffer, indirectOffset)
```

### 参数

- `indirectBuffer`
  - : 一个 {{domxref("GPUBuffer")}}，其中包含执行绘制操作所需的 `vertexCount`、`instanceCount`、`firstVertex` 和 `firstInstance` 值。该缓冲区必须包含一个紧密排列的、由四个 32 位无符号整数值组成的数据块（共 16 字节），这些值的顺序与 {{domxref("GPURenderBundleEncoder.draw()")}} 的参数顺序相同。例如：

    ```js
    const uint32 = new Uint32Array(4);
    uint32[0] = 3; // vertexCount 值
    uint32[1] = 1; // instanceCount 值
    uint32[2] = 0; // firstVertex 值
    uint32[3] = 0; // firstInstance 值

    // 将值写入 GPUBuffer
    device.queue.writeBuffer(buffer, 0, uint32, 0, uint32.length);
    ```

    > [!NOTE]
    > 要使用非零的 `firstInstance` 值，需要启用 `indirect-first-instance` [特性](/en-US/docs/Web/API/GPUSupportedFeatures)。如果未启用 `indirect-first-instance` 特性且 `firstInstance` 不为零，则 `drawIndirect()` 调用将被视为无操作（no-op）。

- `indirectOffset`
  - : 一个以字节为单位的偏移量，表示 `indirectBuffer` 中值数据开始的位置。

### 返回值

无（{{jsxref("undefined")}}）。

### 验证

调用 **`drawIndirect()`** 时必须满足以下条件，否则将生成 {{domxref("GPUValidationError")}}，并且 {{domxref("GPURenderBundleEncoder")}} 变为无效：

- `indirectBuffer` 的 {{domxref("GPUBuffer.usage")}} 包含 `GPUBufferUsage.INDIRECT` 标志。
- `indirectOffset` 加上 `indirectBuffer` 中值参数所指定的总大小，小于或等于 `indirectBuffer` 的 {{domxref("GPUBuffer.size")}}。
- `indirectOffset` 是 4 的倍数。

## 示例

```js
// …

// 创建 GPURenderBundleEncoder
const bundleEncoder = device.createRenderBundleEncoder(descriptor);

// 设置管线和顶点缓冲区
bundleEncoder.setPipeline(renderPipeline);
bundleEncoder.setVertexBuffer(0, vertexBuffer);

// 创建 drawIndirect 值
const uint32 = new Uint32Array(4);
uint32[0] = 3;
uint32[1] = 1;
uint32[2] = 0;
uint32[3] = 0;

// 创建 GPUBuffer 并将绘制值写入其中
const drawValues = device.createBuffer({
  size: 16,
  usage: GPUBufferUsage.COPY_DST | GPUBufferUsage.INDIRECT,
});
device.queue.writeBuffer(drawValues, 0, uint32, 0, uint32.length);

// 绘制顶点
bundleEncoder.drawIndirect(drawValues, 0);

// 结束 bundle 录制
const renderBundle = bundleEncoder.finish();

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)