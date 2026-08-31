---
title: "AudioBufferSourceNode: buffer property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/buffer"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: buffer property"
short-title: buffer
slug: Web/API/AudioBufferSourceNode/buffer
page-type: web-api-instance-property
browser-compat: api.AudioBufferSourceNode.buffer
---

{{ APIRef("Web Audio API") }}

{{domxref("AudioBufferSourceNode")}} 接口的 **`buffer`** 属性提供使用 {{domxref("AudioBuffer")}} 作为声音数据源来播放音频的能力。

如果将 `buffer` 属性设置为 `null`，该节点将生成一个包含静音的单声道（即每个采样值都为 0）。

## 值

一个 {{domxref("AudioBuffer")}}，包含表示该节点将要播放的声音的数据。

## 异常

- `InvalidStateError` {{domxref("DOMException")}}
  - : 如果 `buffer` 属性已经被设置为非 `null` 值，然后又再次设置为非 `null` 值，则抛出该异常。

## 示例

> [!NOTE]
> 有关完整的工作示例，请参阅[在线运行的代码](https://mdn.github.io/webaudio-examples/audio-buffer/)，或[查看源代码](https://github.com/mdn/webaudio-examples/blob/main/audio-buffer/index.html)。

```js
const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);

button.onclick = () => {
  // Fill the buffer with white noise;
  // just random values between -1.0 and 1.0
  for (let channel = 0; channel < channels; channel++) {
    // This gives us the actual ArrayBuffer that contains the data
    const nowBuffering = myArrayBuffer.getChannelData(channel);
    for (let i = 0; i < frameCount; i++) {
      // Math.random() is in [0; 1.0]
      // audio needs to be in [-1.0; 1.0]
      nowBuffering[i] = Math.random() * 2 - 1;
    }
  }

  // Get an AudioBufferSourceNode.
  // This is the AudioNode to use when we want to play an AudioBuffer
  const source = audioCtx.createBufferSource();
  // set the buffer in the AudioBufferSourceNode
  source.buffer = myArrayBuffer;
};
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)