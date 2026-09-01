---
title: "GPUDevice: createComputePipelineAsync() method"
short-title: createComputePipelineAsync()
slug: Web/API/GPUDevice/createComputePipelineAsync
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createComputePipelineAsync
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`createComputePipelineAsync()`** 方法是 {{domxref("GPUDevice")}} 接口的一个方法，返回一个 {{jsxref("Promise")}}，该 Promise 在计算管线可以被使用且不会导致任何阻塞时，兑现为一个 {{domxref("GPUComputePipeline")}}，该管线可以控制计算着色器阶段，并可在 {{domxref("GPUComputePassEncoder")}} 中使用。

> [!NOTE]
> 在可行的情况下，通常优先使用此方法而不是 {{domxref("GPUDevice.createComputePipeline()")}}，因为它可以防止 GPU 操作的执行在管线编译期间被阻塞。

## 语法

```js-nolint
createComputePipelineAsync(descriptor)
```

### 参数

- `descriptor`
  - : 请参阅 [`GPUDevice.createComputePipeline()`](/en-US/docs/Web/API/GPUDevice/createComputePipeline#syntax) 方法的描述符定义。

### 返回值

一个 {{jsxref("Promise")}}，当创建的管线可以立即使用而无需额外延迟时，兑现为一个 {{domxref("GPUComputePipeline")}} 对象实例。

### 验证

如果管线创建失败并导致生成的管线无效，返回的 Promise 会以一个 {{domxref("GPUPipelineError")}} 拒绝：

- 如果失败是由于内部错误，{{domxref("GPUPipelineError")}} 的 `reason` 将为 `"internal"`。
- 如果失败是由于验证错误，{{domxref("GPUPipelineError")}} 的 `reason` 将为 `"validation"`。

以下任一条件为假时，可能发生验证错误：

- `compute` 属性内引用的 `module` 使用的工作组存储大小小于或等于 {{domxref("GPUDevice")}} 的 `maxComputeWorkgroupStorageSize` {{domxref("GPUSupportedLimits", "限制", "", "nocode")}}。
- `module` 使用的每个工作组的计算调用次数小于或等于 {{domxref("GPUDevice")}} 的 `maxComputeInvocationsPerWorkgroup` {{domxref("GPUSupportedLimits", "限制", "", "nocode")}}。
- `module` 的工作组大小小于或等于 {{domxref("GPUDevice")}} 对应的 `maxComputeWorkgroupSizeX`、`maxComputeWorkgroupSizeY` 或 `maxComputeWorkgroupSizeZ` {{domxref("GPUSupportedLimits", "限制", "", "nocode")}}。
- 如果省略 `entryPoint` 属性，着色器代码中包含且仅包含一个计算着色器入口点函数，浏览器将以此作为默认入口点。

## 示例

> [!NOTE]
> [WebGPU 示例](https://webgpu.github.io/webgpu-samples/) 提供了更多示例。

### 基本示例

下面的示例演示了以下过程：

- 使用 {{domxref("GPUDevice.createBindGroupLayout()")}} 创建绑定组布局。
- 将 `bindGroupLayout` 传给 {{domxref("GPUDevice.createPipelineLayout()")}} 以创建 {{domxref("GPUPipelineLayout")}}。
- 立即将该值用于 `createComputePipelineAsync()` 调用，以创建 {{domxref("GPUComputePipeline")}}。

```js
async function init() {
  // …

  const bindGroupLayout = device.createBindGroupLayout({
    entries: [
      {
        binding: 0,
        visibility: GPUShaderStage.COMPUTE,
        buffer: {
          type: "storage",
        },
      },
    ],
  });

  const computePipeline = await device.createComputePipelineAsync({
    layout: device.createPipelineLayout({
      bindGroupLayouts: [bindGroupLayout],
    }),
    compute: {
      module: shaderModule,
      entryPoint: "main",
    },
  });

  // …
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)