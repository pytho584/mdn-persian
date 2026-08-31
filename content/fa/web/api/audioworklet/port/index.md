---
title: "AudioWorklet: port"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorklet/port"
translated_by: "n8n + AI"
---

---
title: "AudioWorklet: port"
short-title: port
slug: Web/API/AudioWorklet/port
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioWorklet.port
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

{{domxref("AudioWorklet")}} 接口的 **`port`** 只读属性返回一个 {{domxref("MessagePort")}} 对象，可用于在主线程和关联的 {{domxref("AudioWorkletGlobalScope")}} 之间发送和接收消息。

这允许在主线程中的代码与音频工作let的全局作用域之间进行自定义的异步通信，例如接收控制数据或全局设置。

## 值

连接 `AudioWorklet` 及其关联 `AudioWorkletGlobalScope` 的 {{domxref("MessagePort")}} 对象。

## 示例

有关更多示例，请参阅 [`AudioWorkletNode.port`](/en-US/docs/Web/API/AudioWorkletNode/port#examples)。

### 使用端口进行全局消息传递

在以下示例中，我们可以使用 `port.onmessage` 接收数据，并使用 `port.postMessage` 发送数据：

```js
const context = new AudioContext();
// Load the module that contains worklet code
await context.audioWorklet.addModule("processor.js");

// Listener for messages from AudioWorkletGlobalScope
context.audioWorklet.port.onmessage = (event) => {
  console.log("Message from global worklet:", event.data);
};

// Set a global config, for example:
context.audioWorklet.port.postMessage({
  volume: 0.8,
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("AudioWorkletGlobalScope")}} — `AudioWorklet` 的全局执行上下文
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [使用 AudioWorklet](/en-US/docs/Web/API/Web_Audio_API/Using_AudioWorklet)