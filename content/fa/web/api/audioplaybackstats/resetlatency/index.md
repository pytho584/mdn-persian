---
title: "AudioPlaybackStats: resetLatency() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/resetLatency"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: resetLatency() method"
short-title: resetLatency()
slug: Web/API/AudioPlaybackStats/resetLatency
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.AudioPlaybackStats.resetLatency
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

**`resetLatency()`** 是 {{domxref("AudioPlaybackStats")}} 接口的方法，用于将延迟统计测量区间的起点重置为 {{domxref("BaseAudioContext.currentTime")}}。

## 语法

```js-nolint
resetLatency()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

### 基本用法

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Reset the latency measurement to the current time
stats.resetLatency();
```

另请参阅主 {{domxref("AudioPlaybackStats")}} 参考页面以获取更深入的示例。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)