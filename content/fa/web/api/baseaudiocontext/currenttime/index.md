---
title: "BaseAudioContext: currentTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/currentTime"
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

{{ domxref("BaseAudioContext") }} 接口的 `currentTime` 只读属性返回一个双精度浮点数，表示不断增加的硬件时间戳（以秒为单位），可用于调度音频播放、可视化时间线等。它从 0 开始。

## 值

一个浮点数。

## 示例

```js
const audioCtx = new AudioContext();
// Older webkit/blink browsers require a prefix

// …

console.log(audioCtx.currentTime);
```

## 降低的时间精度

为了防范时间攻击和[指纹识别](/en-US/docs/Glossary/Fingerprinting)，`audioCtx.currentTime` 的精度可能会根据浏览器设置被舍入。在 Firefox 中，`privacy.reduceTimerPrecision` 偏好默认启用，默认值为 2ms。你还可以启用 `privacy.resistFingerprinting`，在这种情况下，精度将为 100ms 或 `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` 的值，以较大者为准。

例如，在降低时间精度的情况下，`audioCtx.currentTime` 的结果将始终是 0.002 的倍数，或者在启用 `privacy.resistFingerprinting` 时是 0.1（或 `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`）的倍数。

```js
// reduced time precision (2ms) in Firefox 60
audioCtx.currentTime;
// Might be:
// 23.404
// 24.192
// 25.514
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
audioCtx.currentTime;
// Might be:
// 49.8
// 50.6
// 51.7
// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)