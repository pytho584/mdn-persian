---
title: "AudioContext: getOutputTimestamp() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/getOutputTimestamp"
translated_by: "n8n + AI"
---

---
title: "AudioContext: getOutputTimestamp() method"
short-title: getOutputTimestamp()
slug: Web/API/AudioContext/getOutputTimestamp
page-type: web-api-instance-method
browser-compat: api.AudioContext.getOutputTimestamp
---

{{APIRef("Web Audio API")}}

{{domxref("AudioContext")}} 接口的 **`getOutputTimestamp()`** 方法返回一个新的 `AudioTimestamp` 对象，其中包含与当前音频上下文相关的两个音频时间戳值。

这两个值如下：

- `AudioTimestamp.contextTime`：音频输出设备当前正在渲染的采样帧的时间（即输出音频流位置），其单位和原点与上下文的 {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} 相同。基本上，这是音频上下文首次创建之后的时间。
- `AudioTimestamp.performanceTime`：音频输出设备渲染与存储的 `contextTime` 值对应的采样帧的时刻的估计值，其单位和原点与 {{domxref("performance.now()")}} 相同。这是包含音频上下文的文档首次渲染之后的时间。

## Syntax

```js-nolint
getOutputTimestamp()
```

### Parameters

无。

### Return value

一个 `AudioTimestamp` 对象，具有以下属性。

- `contextTime`：`BaseAudioContext` 的 {{domxref("BaseAudioContext/currentTime","currentTime")}} 时间坐标系中的一个点；即音频上下文首次创建后的时间。
- `performanceTime`：`Performance` 接口的时间坐标系中的一个点；即包含音频上下文的文档首次渲染后的时间。

## Examples

在以下代码中，我们在点击播放按钮后开始播放音频文件，并启动一个 `requestAnimationFrame` 循环，持续输出 `contextTime` 和 `performanceTime`。

你可以查看此 [output-timestamp 示例](https://github.com/mdn/webaudio-examples/blob/main/output-timestamp/index.html) 的完整代码（[也可以在线查看](https://mdn.github.io/webaudio-examples/output-timestamp/)）。

```js
// Press the play button
playBtn.addEventListener("click", () => {
  // We can create the audioCtx as there has been some user action
  audioCtx ??= new AudioContext();
  source = new AudioBufferSourceNode(audioCtx);
  getData();
  source.start(0);
  playBtn.disabled = true;
  stopBtn.disabled = false;
  rAF = requestAnimationFrame(outputTimestamps);
});

// Press the stop button
stopBtn.addEventListener("click", () => {
  source.stop(0);
  playBtn.disabled = false;
  stopBtn.disabled = true;
  cancelAnimationFrame(rAF);
});

// Helper function to output timestamps
function outputTimestamps() {
  const ts = audioCtx.getOutputTimestamp();
  output.textContent = `Context time: ${ts.contextTime} | Performance time: ${ts.performanceTime}`;
  rAF = requestAnimationFrame(outputTimestamps); // Reregister itself
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}