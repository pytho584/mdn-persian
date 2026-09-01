```
---
title: "GPUComputePassEncoder: dispatchWorkgroups() method"
short-title: dispatchWorkgroups()
slug: Web/API/GPUComputePassEncoder/dispatchWorkgroups
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.dispatchWorkgroups
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`dispatchWorkgroups()`** 方法属于 {{domxref("GPUComputePassEncoder")}} 接口，用于调度一个特定的工作组网格，以执行当前 {{domxref("GPUComputePipeline")}}（即通过 {{domxref("GPUComputePassEncoder.setPipeline()")}} 设置）所定义的工作。

## 语法

```js-nolint
dispatchWorkgroups(workgroupCountX)
dispatchWorkgroups(workgroupCountX, workgroupCountY)
dispatchWorkgroups(workgroupCountX, workgroupCountY, workgroupCountZ)
```

### 参数

- `workgroupCountX`
  - ：要调度的工作组网格的 X 维度。
- `workgroupCountY` {{optional_inline}}
  - ：要调度的工作组网格的 Y 维度。如果省略，`workgroupCountY` 默认为 1。
- `workgroupCountZ` {{optional_inline}}
  - ：要调度的工作组网格的 Z 维度。如果省略，`workgroupCountZ` 默认为 1。

> [!NOTE]
> 传给 `dispatchWorkgroups()` 和 {{domxref("GPUComputePassEncoder.dispatchWorkgroupsIndirect()")}} 的 X、Y、Z 维度值，是每个维度上要调度的**工作组数量**，而不是每个维度上要执行的着色器调用次数。这与现代原生 GPU API 的行为一致，但与 OpenCL 的行为不同。这意味着，如果一个 {{domxref("GPUShaderModule")}} 定义了一个带有 `@workgroup_size(4, 4)` 的入口点，并通过 `passEncoder.dispatchWorkgroups(8, 8);` 调用进行调度，那么该入口点总共会被调用 1024 次——即在 X 和 Y 两个方向上各调度 8 次 4×4 的工作组。`4 * 4 * 8 * 8 = 1024`。

### 返回值

无（{{jsxref("undefined")}}）。

### 验证

调用 **`dispatchWorkgroups()`** 时必须满足以下条件，否则会生成一个 {{domxref("GPUValidationError")}}，并且该 {{domxref("GPUComputePassEncoder")}} 将变为无效：

- `workgroupCountX`、`workgroupCountY` 和 `workgroupCountZ` 都小于或等于 {{domxref("GPUDevice")}} 的 `maxComputeWorkgroupsPerDimension` {{domxref("GPUSupportedLimits", "限制", "", "nocode")}}。

## 示例

在 [basic compute demo](https://mdn.github.io/dom-examples/webgpu-compute-demo/) 中，通过 {{domxref("GPUCommandEncoder")}} 记录了几条命令。这些命令大部分来自通过 `beginComputePass()` 创建的 {{domxref("GPUComputePassEncoder")}}。

在代码开头，我们设置了一个全局缓冲区大小为 1000。另外请注意，着色器中的工作组大小设置为 64。

```js
const BUFFER_SIZE = 1000;

// Compute shader
const shader = `
@group(0) @binding(0)
var<storage, read_write> output: array<f32>;

@compute @workgroup_size(64)

...

`;
```

在后面的代码中，`dispatchWorkgroups()` 的 `workgroupCountX` 参数根据全局缓冲区大小和着色器工作组数量来设置。

```js
// …

// Create GPUCommandEncoder to encode commands to issue to the GPU
const commandEncoder = device.createCommandEncoder();

// Initiate compute pass
const passEncoder = commandEncoder.beginComputePass();

// Issue commands
passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);
passEncoder.dispatchWorkgroups(Math.ceil(BUFFER_SIZE / 64));

// End the render pass
passEncoder.end();

// Copy output buffer to staging buffer
commandEncoder.copyBufferToBuffer(
  output,
  0, // Source offset
  stagingBuffer,
  0, // Destination offset
  BUFFER_SIZE,
);

// End frame by passing array of command buffers to command queue for execution
device.queue.submit([commandEncoder.finish()]);

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```