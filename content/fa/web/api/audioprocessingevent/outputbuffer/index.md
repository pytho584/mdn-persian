---
title: "AudioProcessingEvent: outputBuffer property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioProcessingEvent/outputBuffer"
translated_by: "n8n + AI"
---

---
title: "AudioProcessingEvent: outputBuffer property"
short-title: outputBuffer
slug: Web/API/AudioProcessingEvent/outputBuffer
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.AudioProcessingEvent.outputBuffer
---

{{APIRef("Web Audio API")}}{{Deprecated_header}}

{{domxref("AudioProcessingEvent")}} 接口的 **`outputBuffer`** 只读属性表示音频处理事件的输出缓冲区。

输出缓冲区由 {{domxref("AudioBuffer")}} 对象表示，该对象包含一组音频通道，每个通道都是一个浮点值数组，表示以一系列幅度编码的音频信号波形。通道数和每个通道的长度由 `AudioBuffer` 的通道数和缓冲区大小属性决定。

## 值

一个 {{domxref("AudioBuffer")}} 对象。

## 示例

在此示例中，创建了一个缓冲区大小为 256 个采样、2 个输入通道和 2 个输出通道的 {{domxref("ScriptProcessorNode")}}。当触发 {{domxref("ScriptProcessorNode/audioprocess_event", "audioprocess")}} 事件时，会从事件对象中获取输入和输出缓冲区。处理输入缓冲区中的音频数据，并将结果写入输出缓冲区。在本例中，音频数据按 0.5 的系数缩小。

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AudioProcessingEvent.inputBuffer")}}
- {{domxref("ScriptProcessorNode")}}