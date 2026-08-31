---
title: "AudioProcessingEvent: inputBuffer property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioProcessingEvent/inputBuffer"
translated_by: "n8n + AI"
---

---
title: "AudioProcessingEvent: inputBuffer property"
short-title: inputBuffer
slug: Web/API/AudioProcessingEvent/inputBuffer
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.AudioProcessingEvent.inputBuffer
---

{{APIRef("Web Audio API")}}{{Deprecated_header}}

**`inputBuffer`** 只读属性，属于 {{domxref("AudioProcessingEvent")}} 接口，表示音频处理事件的输入缓冲区。

输入缓冲区由 {{domxref("AudioBuffer")}} 对象表示，该对象包含一组音频通道，每个通道都是一个浮点值数组，表示音频信号波形，这些波形编码为一系列振幅。通道数量和每个通道的长度由 `AudioBuffer` 的通道数和缓冲区大小属性决定。

## 值

一个 {{domxref("AudioBuffer")}} 对象。

## 示例

在此示例中，创建了一个 {{domxref("ScriptProcessorNode")}}，缓冲区大小为 256 个样本，2 个输入通道和 2 个输出通道。当触发 {{domxref("ScriptProcessorNode/audioprocess_event", "audioprocess")}} 事件时，将从事件对象中获取输入和输出缓冲区。输入缓冲区中的音频数据被处理，结果写入输出缓冲区。在此情况下，音频数据按 0.5 的因子缩放。

```js
const audioContext = new AudioContext();
const processor = audioContext.createScriptProcessor(256, 2, 2);

processor.addEventListener("audioprocess", (event) => {
  const inputBuffer = event.inputBuffer;
  const outputBuffer = event.outputBuffer;

  for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
    const inputData = inputBuffer.getChannelData(channel);
    const outputData = outputBuffer.getChannelData(channel);

    // Process the audio data here
    for (let i = 0; i < outputBuffer.length; i++) {
      outputData[i] = inputData[i] * 0.5;
    }
  }
});

processor.connect(audioContext.destination);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("AudioProcessingEvent.outputBuffer")}}
- {{domxref("ScriptProcessorNode")}}