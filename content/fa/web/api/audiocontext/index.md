---
title: "AudioContext"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext"
translated_by: "n8n + AI"
---

---
title: AudioContext
slug: Web/API/AudioContext
page-type: web-api-interface
browser-compat: api.AudioContext
---

{{APIRef("Web Audio API")}}

`AudioContext` 接口表示一个由音频模块链接在一起构建的音频处理图，每个模块由 {{domxref("AudioNode")}} 表示。

音频上下文既控制其所包含节点的创建，也控制音频处理或解码的执行。在做任何其他事情之前，你需要创建一个 `AudioContext`，因为一切都发生在上下文内部。建议创建一个 `AudioContext` 并重复使用它，而不是每次初始化一个新的；同时，也可以并发地对多个不同的音频源和管线使用单个 `AudioContext`。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("AudioContext.AudioContext", "AudioContext()")}}
  - : 创建并返回一个新的 `AudioContext` 对象。

## 实例属性

_同时继承其父接口 {{domxref("BaseAudioContext")}} 的属性。_

- {{domxref("AudioContext.baseLatency")}} {{ReadOnlyInline}}
  - : 返回 `AudioContext` 将音频从 {{domxref("AudioDestinationNode")}} 传递到音频子系统时所产生的处理延迟秒数。
- {{domxref("AudioContext.outputLatency")}} {{ReadOnlyInline}}
  - : 返回当前音频上下文输出延迟的估计值。
- {{domxref("AudioContext.playbackStats")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : 返回一个 {{domxref("AudioPlaybackStats")}} 对象，该对象提供对 `AudioContext` 的持续时间、欠载和延迟统计信息的访问。
- {{domxref("AudioContext.sinkId")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : 返回当前输出音频设备的接收器 ID（sink ID）。

## 实例方法

_同时继承其父接口 {{domxref("BaseAudioContext")}} 的方法。_

- {{domxref("AudioContext.close()")}}
  - : 关闭音频上下文，释放其使用的所有系统音频资源。
- {{domxref("AudioContext.createMediaElementSource()")}}
  - : 创建一个与 {{domxref("HTMLMediaElement")}} 关联的 {{domxref("MediaElementAudioSourceNode")}}。这可用于播放和处理来自 {{HTMLElement("video")}} 或 {{HTMLElement("audio")}} 元素的音频。
- {{domxref("AudioContext.createMediaStreamSource()")}}
  - : 创建一个与 {{domxref("MediaStream")}} 关联的 {{domxref("MediaStreamAudioSourceNode")}}，该 {{domxref("MediaStream")}} 表示可能来自本地计算机麦克风或其他来源的音频流。
- {{domxref("AudioContext.createMediaStreamDestination()")}}
  - : 创建一个与 {{domxref("MediaStream")}} 关联的 {{domxref("MediaStreamAudioDestinationNode")}}，该 {{domxref("MediaStream")}} 表示可能存储在本地文件中或发送到另一台计算机的音频流。
- {{domxref("AudioContext.createMediaStreamTrackSource()")}}
  - : 创建一个与表示媒体流轨道的 {{domxref("MediaStream")}} 关联的 {{domxref("MediaStreamTrackAudioSourceNode")}}。
- {{domxref("AudioContext.getOutputTimestamp()")}}
  - : 返回一个新的 `AudioTimestamp` 对象，其中包含与当前音频上下文相关的两个音频时间戳值。
- {{domxref("AudioContext.resume()")}}
  - : 恢复先前已暂停/挂起的音频上下文中时间的推进。
- {{domxref("AudioContext.setSinkId()")}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : 为 `AudioContext` 设置输出音频设备。
- {{domxref("AudioContext.suspend()")}}
  - : 暂停音频上下文中时间的推进，暂时停止音频硬件访问，并在此过程中减少 CPU/电池的使用。

## 事件

- {{domxref("AudioContext/sinkchange_event", "sinkchange")}} {{Experimental_Inline}}
  - : 当输出音频设备（因此也包括 {{domxref("AudioContext.sinkId")}}）发生变化时触发。

## 示例

基本音频上下文声明：

```js
const audioCtx = new AudioContext();

const oscillatorNode = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();
const finish = audioCtx.destination;
// etc.
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("OfflineAudioContext")}}