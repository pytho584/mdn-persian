---
title: "AudioProcessingEvent: playbackTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioProcessingEvent/playbackTime"
translated_by: "n8n + AI"
---

---
title: "AudioProcessingEvent: playbackTime property"
short-title: playbackTime
slug: Web/API/AudioProcessingEvent/playbackTime
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.AudioProcessingEvent.playbackTime
---

{{APIRef("Web Audio API")}}{{Deprecated_header}}

خاصیت فقط خواندنی **`playbackTime`** از رابط {{domxref("AudioProcessingEvent")}} نشان‌دهنده زمان پخش صدا است. این زمان در همان سیستم مختصات زمانی است که توسط {{domxref("AudioContext")}} استفاده می‌شود.

## مقدار

عددی که نیازی به عدد صحیح بودن ندارد.

## مثال‌ها

```js
const audioContext = new AudioContext();
const processor = audioContext.createScriptProcessor(256, 2, 2);

processor.addEventListener("audioprocess", (event) => {
  const inputBuffer = event.inputBuffer;
  const outputBuffer = event.outputBuffer;

  for (let channel = 0; channel < outputBuffer.numberOfChannels; channel++) {
    const inputData = inputBuffer.getChannelData(channel);
    const outputData = outputBuffer.getChannelData(channel);

    // Log the corresponding time for this audio buffer
    console.log(`Received audio data to be played at ${event.playbackTime}`);

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

- {{domxref("AudioProcessingEvent")}}
- {{domxref("ScriptProcessorNode")}}