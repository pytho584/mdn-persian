---
title: "GPUDevice: createCommandEncoder() method"
short-title: createCommandEncoder()
slug: Web/API/GPUDevice/createCommandEncoder
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createCommandEncoder
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`createCommandEncoder()`** 方法屬於 {{domxref("GPUDevice")}} 介面，用於建立一個 {{domxref("GPUCommandEncoder")}}，用來編碼要發送給 GPU 的指令。

## 語法

```js-nolint
createCommandEncoder()
createCommandEncoder(descriptor)
```

### 參數

- `descriptor` {{optional_inline}}
  - : 一個物件，包含以下屬性：
    - `label` {{optional_inline}}
      - : 一個字串，提供可用於識別物件的標籤，例如在 {{domxref("GPUError")}} 訊息或主控台警告中。

### 回傳值

一個 {{domxref("GPUCommandEncoder")}} 物件實例。

## 範例

在我們的 [basic render demo](https://mdn.github.io/dom-examples/webgpu-render-demo/) 中，多個指令透過 `createCommandEncoder()` 建立的 {{domxref("GPUCommandEncoder")}} 來記錄：

```js
// …

// 建立 GPUCommandEncoder
const commandEncoder = device.createCommandEncoder();

// 建立 GPURenderPassDescriptor 告訴 WebGPU 要繪製到哪個紋理，然後開始渲染通道
const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: clearColor,
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
};

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// 繪製一個三角形
passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// 結束渲染通道
passEncoder.end();

// …
```

由 {{domxref("GPUCommandEncoder")}} 編碼的指令會透過 {{domxref("GPUCommandEncoder.finish()")}} 方法記錄到 {{domxref("GPUCommandBuffer")}} 中。接著，指令緩衝區會透過 {{domxref("GPUQueue.submit", "submit()")}} 呼叫傳入佇列，準備交由 GPU 處理。

```js
device.queue.submit([commandEncoder.finish()]);
```

> [!NOTE]
> 可以研究 [WebGPU samples](https://webgpu.github.io/webgpu-samples/) 以尋找更多指令編碼的範例。

## 規格

{{Specifications}}

## 瀏覽器相容性

{{Compat}}

## 參見

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)