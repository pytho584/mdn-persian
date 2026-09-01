---
title: "GPUAdapterInfo"
---

---
title: GPUAdapterInfo
slug: Web/API/GPUAdapterInfo
page-type: web-api-interface
browser-compat: api.GPUAdapterInfo
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

`GPUAdapterInfo` 接口属于 {{domxref("WebGPU API", "WebGPU API", "", "nocode")}}，包含关于 {{domxref("GPUAdapter")}} 的标识信息。

可以通过适配器自身的 {{domxref("GPUAdapter.info")}} 属性来获取适配器的 `GPUAdapterInfo`，也可以通过由该适配器创建的设备的 {{domxref("GPUDevice.adapterInfo")}} 属性来获取。

该对象允许开发者访问用户 GPU 的具体细节，以便他们能够预先针对 GPU 特有的错误采取规避措施，或提供不同的代码路径以更好地适应不同的 GPU 架构。提供此类信息确实存在安全风险——它可能被用于指纹识别——因此共享的信息被限制在最低限度，且不同的浏览器供应商可能会共享不同种类和粒度的信息。

{{InheritanceDiagram}}

## 实例属性

- {{domxref("GPUAdapterInfo.architecture", "architecture")}} {{ReadOnlyInline}}
  - : 适配器所属 GPU 家族或类别的名称。如果不可用，则返回空字符串。
- {{domxref("GPUAdapterInfo.description", "description")}} {{ReadOnlyInline}}
  - : 描述适配器的人类可读字符串。如果不可用，则返回空字符串。
- {{domxref("GPUAdapterInfo.device", "device")}} {{ReadOnlyInline}}
  - : 适配器的供应商特定标识符。如果不可用，则返回空字符串。
- {{domxref("GPUAdapterInfo.isFallbackAdapter", "isFallbackAdapter")}} {{ReadOnlyInline}}
  - : 一个布尔值。如果适配器是[آداپتور جایگزین (fallback adapter)](/en-US/docs/Web/API/GPU/requestAdapter#fallback_adapters)，则返回 `true`，否则返回 `false`。
- {{domxref("GPUAdapterInfo.subgroupMaxSize", "subgroupMaxSize")}} {{ReadOnlyInline}}
  - : 该 {{domxref("GPUAdapter")}} 支持的最大[اندازه زیرگروه (subgroup size)](https://gpuweb.github.io/gpuweb/wgsl/#subgroup-size)。
- {{domxref("GPUAdapterInfo.subgroupMinSize", "subgroupMinSize")}} {{ReadOnlyInline}}
  - : 该 {{domxref("GPUAdapter")}} 支持的最小[اندازه زیرگروه (subgroup size)](https://gpuweb.github.io/gpuweb/wgsl/#subgroup-size)。
- {{domxref("GPUAdapterInfo.vendor", "vendor")}} {{ReadOnlyInline}}
  - : 适配器供应商的名称。如果不可用，则返回空字符串。

## 示例

### 通过 GPUAdapter.info 访问 GPUAdapterInfo

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const adapterInfo = adapter.info;
console.log(adapterInfo.vendor);
console.log(adapterInfo.architecture);
```

### 通过 GPUDevice.adapterInfo 访问 GPUAdapterInfo

```js
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
  throw Error("Couldn't request WebGPU adapter.");
}

const myDevice = await adapter.requestDevice();

function optimizeForGpuDevice(device) {
  if (device.adapterInfo.vendor === "amd") {
    // Use AMD-specific optimizations
  } else if (device.adapterInfo.architecture.includes("turing")) {
    // Optimize for NVIDIA Turing architecture
  }
}

optimizeForGpuDevice(myDevice);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("GPUAdapter.info")}}
- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)