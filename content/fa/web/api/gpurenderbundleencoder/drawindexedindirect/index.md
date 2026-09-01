---
title: "GPURenderBundleEncoder: drawIndexedIndirect() method"
short-title: drawIndexedIndirect()
slug: Web/API/GPURenderBundleEncoder/drawIndexedIndirect
page-type: web-api-instance-method
browser-compat: api.GPURenderBundleEncoder.drawIndexedIndirect
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`drawIndexedIndirect()`** 方法属于 {{domxref("GPURenderBundleEncoder")}} 接口，使用从 {{domxref("GPUBuffer")}} 读取的参数来绘制索引化图元。

> [!NOTE]
> 此方法在功能上与其在 {{domxref("GPURenderPassEncoder")}} 上的对应方法 {{domxref("GPURenderPassEncoder.drawIndexedIndirect", "drawIndexedIndirect()")}} 完全相同。

## 语法

```js-nolint
drawIndexedIndirect(indirectBuffer, indirectOffset)
```

### 参数

- `indirectBuffer`
  - : 一个 {{domxref("GPUBuffer")}}，包含执行绘制操作所需的 `indexCount`、`instanceCount`、`firstIndex`、`baseVertex` 和 `firstInstance` 值。该缓冲区必须包含五个紧密排列的 32 位无符号整数值（共 20 字节），其顺序与 {{domxref("GPURenderBundleEncoder.drawIndexed()")}} 的参数顺序一致。例如：

    ```js
    const uint32 = new Uint32Array(5);
    uint32[0] = 3; // The indexCount value
    uint32[1] = 1; // The instanceCount value
    uint32[2] = 0; // The firstIndex value
    uint32[3] = 0; // The baseVertex value
    uint32[4] = 0; // The firstInstance value

    // Write values into a GPUBuffer
    device.queue.writeBuffer(buffer, 0, uint32, 0, uint32.length);
    ```

    > [!NOTE]
    > 要使用非零的 `firstInstance` 值，需要启用 `indirect-first-instance` [特性](/en-US/docs/Web/API/GPUSupportedFeatures)。如果未启用 `indirect-first-instance` 特性且 `firstInstance` 不为零，则 `drawIndexedIndirect()` 调用将被视为空操作（no-op）。

- `indirectOffset`
  - : `indirectBuffer` 中值数据开始处的偏移量，以字节为单位。

### 返回值

无（{{jsxref("undefined")}}）。

### 验证

调用 **`drawIndirect()`** 时必须满足以下条件，否则会生成 {{domxref("GPUValidationError")}} 并使 {{domxref("GPURenderBundleEncoder")}} 变为无效：

- `indirectBuffer` 的 {{domxref("GPUBuffer.usage")}} 包含 `GPUBufferUsage.INDIRECT` 标志。
- `indirectOffset` 加上 `indirectBuffer` 中由值参数指定的总大小小于或等于 `indirectBuffer` 的 {{domxref("GPUBuffer.size")}}。
- `indirectOffset` 是 4 的倍数。

## 示例

```js
// …

// Create GPURenderBundleEncoder
const bundleEncoder = device.createRenderBundleEncoder(descriptor);

// Set pipeline and vertex buffer
bundleEncoder.setPipeline(renderPipeline);
bundleEncoder.setVertexBuffer(0, vertexBuffer);
bundleEncoder.setIndexBuffer(indexBuffer, "uint16");

// Create drawIndexedIndirect values
const uint32 = new Uint32Array(5);
uint32[0] = 3;
uint32[1] = 1;
uint32[2] = 0;
uint32[3] = 0;
uint32[4] = 0;

// Create a GPUBuffer and write the draw values into it
const drawValues = device.createBuffer({
  size: 20,
  usage: GPUBufferUsage.COPY_DST | GPUBufferUsage.INDIRECT,
});
device.queue.writeBuffer(drawValues, 0, uint32, 0, uint32.length);

// Draw the vertices
bundleEncoder.drawIndexedIndirect(drawValues, 0);

// End the bundle recording
const renderBundle = bundleEncoder.finish();

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)