---
title: "AudioBuffer: copyToChannel() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBuffer/copyToChannel"
translated_by: "n8n + AI"
---

---
title: "AudioBuffer: copyToChannel() method"
short-title: copyToChannel()
slug: Web/API/AudioBuffer/copyToChannel
page-type: web-api-instance-method
browser-compat: api.AudioBuffer.copyToChannel
---

{{ APIRef("Web Audio API") }}

متد `copyToChannel()` از رابط {{ domxref("AudioBuffer") }} نمونه‌ها را از آرایه مبدأ به کانال مشخص‌شده `AudioBuffer` کپی می‌کند.

## Syntax

```js-nolint
copyToChannel(source, channelNumber)
copyToChannel(source, channelNumber, startInChannel)
```

### Parameters

- `source`
  - : یک {{jsxref("Float32Array")}} که داده‌های کانال از آن کپی خواهد شد.
- `channelNumber`
  - : شماره کانال {{domxref("AudioBuffer")}} فعلی که داده‌های کانال به آن کپی می‌شود. اگر _channelNumber_ بزرگ‌تر یا مساوی {{domxref("AudioBuffer.numberOfChannels")}} باشد، یک خطای `INDEX_SIZE_ERR` پرتاب می‌شود.
- `startInChannel` {{optional_inline}}
  - : یک افست اختیاری برای کپی داده‌ها. اگر _startInChannel_ بزرگ‌تر از {{domxref("AudioBuffer.length")}} باشد، یک خطای `INDEX_SIZE_ERR` پرتاب می‌شود.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

```js
const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);
const anotherArray = new Float32Array();
// Copy channel data from second channel of myArrayBuffer.
myArrayBuffer.copyFromChannel(anotherArray, 1, 0);
// Copy data from anotherArray to first channel of myArrayBuffer. Both channels have the same data now.
myArrayBuffer.copyToChannel(anotherArray, 0, 0);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)