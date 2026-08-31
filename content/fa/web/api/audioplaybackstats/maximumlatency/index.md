---
title: "AudioPlaybackStats: maximumLatency property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats/maximumLatency"
translated_by: "n8n + AI"
---

---
title: "AudioPlaybackStats: maximumLatency property"
short-title: maximumLatency
slug: Web/API/AudioPlaybackStats/maximumLatency
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioPlaybackStats.maximumLatency
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

**`maximumLatency`** 是 {{domxref("AudioPlaybackStats")}} 接口的只读属性，是一个数字，表示自音频上下文初始化以来或自上次调用 {{domxref("AudioPlaybackStats.resetLatency()")}} 以来的最大延迟。

## 值

一个双精度浮点数，表示最大延迟，单位为秒。初始值为 `0`。

## 示例

### 基本用法

```js
const audioCtx = new AudioContext();
const stats = audioCtx.playbackStats;

// ...

// Log maximum latency
console.log(stats.maximumLatency);
```

另请参阅主 {{domxref("AudioPlaybackStats")}} 参考页面，以获取更深入的示例。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)