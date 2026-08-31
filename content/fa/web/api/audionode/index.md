---
title: "AudioNode"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode"
translated_by: "n8n + AI"
---

---
title: AudioNode
slug: Web/API/AudioNode
page-type: web-api-interface
browser-compat: api.AudioNode
---

{{APIRef("Web Audio API")}}

**`AudioNode`** 接口是一个用于表示音频处理模块的通用接口。

示例包括：

- 音频源（如 HTML {{HTMLElement("audio")}} 或 {{HTMLElement("video")}} 元素、{{domxref("OscillatorNode")}} 等），
- 音频目的地，
- 中间处理模块（如 {{domxref("BiquadFilterNode")}} 或 {{domxref("ConvolverNode")}} 等滤波器），或
- 音量控制（如 {{domxref("GainNode")}}）

{{InheritanceDiagram}}

> [!NOTE]
> `AudioNode` 可以成为事件的目标，因此它实现了 {{domxref("EventTarget")}} 接口。

## 实例属性

- {{domxref("AudioNode.context")}} {{ReadOnlyInline}}
  - : 返回关联的 {{domxref("BaseAudioContext")}}，即表示该节点参与的处理图的对象。
- {{domxref("AudioNode.numberOfInputs")}} {{ReadOnlyInline}}
  - : 返回输入到节点的输入数量。源节点被定义为 `numberOfInputs` 属性值为 `0` 的节点。
- {{domxref("AudioNode.numberOfOutputs")}} {{ReadOnlyInline}}
  - : 返回从节点输出的数量。目的地节点——如 {{ domxref("AudioDestinationNode") }}——此属性值为 `0`。
- {{domxref("AudioNode.channelCount")}}
  - : 表示一个整数，用于确定在[向上混音和向下混音](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing)连接到节点的任何输入时使用多少个通道。其用法和精确定义取决于 {{domxref("AudioNode.channelCountMode")}} 的值。
- {{domxref("AudioNode.channelCountMode")}}
  - : 表示一个枚举值，描述节点输入和输出之间通道匹配的方式。
- {{domxref("AudioNode.channelInterpretation")}}
  - : 表示一个枚举值，描述通道的含义。这种解释将定义音频[向上混音和向下混音](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing)的方式。
    可能的值为 `"speakers"` 或 `"discrete"`。

## 实例方法

_还实现了 {{domxref("EventTarget")}} 接口的方法。_

- {{domxref("AudioNode.connect()")}}
  - : 允许我们将此节点的输出连接到另一个节点的输入，无论是作为音频数据还是作为 {{domxref("AudioParam")}} 的值。
- {{domxref("AudioNode.disconnect()")}}
  - : 允许我们将当前节点与已连接的另一节点断开。

## 描述

### 音频路由图

![参与 AudioContext 的 AudioNode 创建音频路由图。](webaudiobasics.png)

每个 `AudioNode` 都有输入和输出，多个音频节点连接在一起构建一个 _处理图_。该图包含在一个 {{domxref("AudioContext")}} 中，且每个音频节点只能属于一个音频上下文。

_源节点_ 有零个输入但有一个或多个输出，可用于生成声音。另一方面，_目的地节点_ 没有输出；相反，其所有输入直接通过扬声器（或音频上下文使用的任何音频输出设备）播放。此外，还有具有输入和输出的 _处理节点_。具体的处理因 `AudioNode` 而异，但通常节点读取其输入，进行一些与音频相关的处理，并为其输出生成新值，或让音频通过（例如在 {{domxref("AnalyserNode")}} 中，处理结果被单独访问）。

图中的节点越多，延迟就越高。例如，如果图有 500ms 的延迟，当源节点播放声音时，需要半秒钟才能在扬声器上听到（或者由于底层音频设备的延迟甚至更长）。因此，如果需要交互式音频，请尽可能保持图较小，并将用户控制的音频节点放在图的末尾。例如，音量控制（`GainNode`）应该是最后一个节点，以便音量变化立即生效。

每个输入和输出都有一定数量的 _通道_。例如，单声道音频有一个通道，而立体声音频有两个通道。Web Audio API 将根据需要向上混音或向下混音通道数量；详细信息请参阅 Web Audio 规范。

有关所有音频节点的列表，请参阅 [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) 主页。

### 创建 `AudioNode`

有两种创建 `AudioNode` 的方法：通过 _构造函数_ 和通过 _工厂方法_。

```js
// constructor
const analyserNode = new AnalyserNode(audioCtx, {
  fftSize: 2048,
  maxDecibels: -25,
  minDecibels: -60,
  smoothingTimeConstant: 0.5,
});
```

```js
// factory method
const analyserNode = audioCtx.createAnalyser();
analyserNode.fftSize = 2048;
analyserNode.maxDecibels = -25;
analyserNode.minDecibels = -60;
analyserNode.smoothingTimeConstant = 0.5;
```

您可以自由使用构造函数或工厂方法，或混合使用，但使用构造函数有一些优势：

- 所有参数都可以在构造时设置，无需单独设置。
- 您可以[对音频节点进行子类化](https://github.com/WebAudio/web-audio-api/issues/251)。虽然实际处理由浏览器在内部完成且无法更改，但您可以围绕音频节点编写包装器以提供自定义属性和方法。
- 性能略好：在 Chrome 和 Firefox 中，工厂方法在内部调用构造函数。

_简要历史：_ Web Audio 规范的第一版只定义了工厂方法。在 [2013 年 10 月的设计审查](https://github.com/WebAudio/web-audio-api/issues/250) 之后，决定添加构造函数，因为它们比工厂方法有很多好处。构造函数于 2016 年 8 月至 10 月被添加到规范中。工厂方法继续保留在规范中，并且没有被弃用。

## 示例

这个简单的代码片段展示了如何创建一些音频节点，以及如何使用 `AudioNode` 的属性和方法。您可以在 [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) 着陆页上链接的任何示例中找到此类用法（例如 [Violent Theremin](https://github.com/mdn/webaudio-examples/tree/main/violent-theremin)）。

```js
const audioCtx = new AudioContext();

const oscillator = new OscillatorNode(audioCtx);
const gainNode = new GainNode(audioCtx);

oscillator.connect(gainNode).connect(audioCtx.destination);

oscillator.context;
oscillator.numberOfInputs;
oscillator.numberOfOutputs;
oscillator.channelCount;
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)