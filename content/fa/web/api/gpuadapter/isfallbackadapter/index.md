---
title: "GPUAdapter: isFallbackAdapter property"
short-title: isFallbackAdapter
slug: Web/API/GPUAdapter/isFallbackAdapter
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.GPUAdapter.isFallbackAdapter
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}{{deprecated_header}}{{non-standard_header}}

{{domxref("GPUAdapter")}} 接口的 **`isFallbackAdapter`** 只读属性，如果适配器是[备用适配器](/en-US/docs/Web/API/GPU/requestAdapter#fallback_adapters)，则返回 `true`，否则返回 `false`。

此属性已从 Web 平台中移除。请改用 {{domxref("GPUAdapterInfo.isFallbackAdapter")}}。

## 值

一个布尔值。

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

  const isFallback = adapter.isFallbackAdapter;
  console.log(isFallback);

  // …
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)