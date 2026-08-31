---
title: "AudioNode: channelCountMode property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/channelCountMode"
translated_by: "n8n + AI"
---

---
title: "AudioNode: channelCountMode property"
short-title: channelCountMode
slug: Web/API/AudioNode/channelCountMode
page-type: web-api-instance-property
browser-compat: api.AudioNode.channelCountMode
---

{{ APIRef("Web Audio API") }}

`AudioNode` 接口的 `channelCountMode` 属性是一个枚举值，用于描述节点输入与输出之间声道必须如何匹配。

## 值

`channelCountMode` 枚举值可能的值及其含义如下：

- `max`
  - : 声道数等于所有连接中的最大声道数。
    在这种情况下，`channelCount` 被忽略，只进行上混音。

    以下 `AudioNode` 子节点默认使用此值：{{domxref("GainNode")}}、{{domxref("DelayNode")}}、{{domxref("ScriptProcessorNode")}}、{{domxref("BiquadFilterNode")}}、{{domxref("WaveShaperNode")}}。

- `clamped-max`
  - : 声道数等于所有连接中的最大声道数，但会被限制为 `channelCount` 的值。

    以下 `AudioNode` 子节点默认使用此值：{{domxref("PannerNode")}}、{{domxref("ConvolverNode")}}、{{domxref("DynamicsCompressorNode")}}。

- `explicit`
  - : 声道数由 `channelCount` 的值定义。

    以下 `AudioNode` 子节点默认使用此值：{{domxref("AudioDestinationNode")}}、{{domxref("AnalyserNode")}}、{{domxref("ChannelSplitterNode")}}、{{domxref("ChannelMergerNode")}}。

> [!NOTE]
> 在旧版规范中，{{domxref("ChannelSplitterNode")}} 的默认值为 `max`。

## 示例

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillator.connect(gainNode);
gainNode.connect(audioCtx.destination);

oscillator.channelCountMode = "explicit";
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)