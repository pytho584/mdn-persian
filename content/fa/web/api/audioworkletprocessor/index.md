---
title: "AudioWorkletProcessor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletProcessor"
translated_by: "n8n + AI"
---

---
title: AudioWorkletProcessor
slug: Web/API/AudioWorkletProcessor
page-type: web-api-interface
browser-compat: api.AudioWorkletProcessor
---

{{APIRef("Web Audio API")}}

**`AudioWorkletProcessor`** 接口（属于 [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)）表示自定义 {{domxref("AudioWorkletNode")}} 背后的音频处理代码。它位于 {{domxref("AudioWorkletGlobalScope")}} 中，并在 Web Audio 渲染线程上运行。相应地，基于它的 {{domxref("AudioWorkletNode")}} 在主线程上运行。

## 构造函数

> [!NOTE]
> `AudioWorkletProcessor` 及其派生类无法通过用户提供的代码直接实例化。相反，它们仅在创建关联的 {{domxref("AudioWorkletNode")}} 时由内部创建。派生类的构造函数会接收一个选项对象，因此你可以执行自定义的初始化过程 — 有关详细信息，请参阅构造函数页面。

- {{domxref("AudioWorkletProcessor.AudioWorkletProcessor", "AudioWorkletProcessor()")}}
  - : 创建一个新的 `AudioWorkletProcessor` 对象实例。

## 实例属性

- {{domxref("AudioWorkletProcessor.port", "port")}} {{ReadOnlyInline}}
  - : 返回一个 {{domxref("MessagePort")}}，用于处理器与其所属的 {{domxref("AudioWorkletNode")}} 之间的双向通信。另一端可通过该节点的 {{domxref("AudioWorkletNode.port", "port")}} 属性获得。

## 实例方法

_`AudioWorkletProcessor` 接口未定义自身的任何方法。但是，你必须提供一个 {{domxref("AudioWorkletProcessor.process", "process()")}} 方法，该方法会被调用来处理音频流。_

## 事件

_`AudioWorkletProcessor` 接口不响应任何事件。_

## 使用说明

### 派生类

要定义自定义音频处理代码，你必须从 `AudioWorkletProcessor` 接口派生一个类。虽然接口未定义该方法，但派生类必须具有 {{domxref("AudioWorkletProcessor.process", "process")}} 方法。该方法针对每个 128 采样帧的块调用，并将输入和输出数组以及自定义 {{domxref("AudioParam")}} 的计算值（如果已定义）作为参数。你可以使用输入和音频参数值来填充输出数组，输出数组默认包含静音。

可选地，如果你希望节点上具有自定义的 {{domxref("AudioParam")}}，你可以在处理器上提供一个 {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} 属性作为 _静态 getter_。返回的基于 {{domxref("AudioParamDescriptor")}} 的对象数组在 `AudioWorkletNode` 实例化期间被内部用于创建 {{domxref("AudioParam")}}。

生成的 `AudioParam` 位于节点的 {{domxref("AudioWorkletNode.parameters", "parameters")}} 属性中，并且可以使用标准方法（如 [`linearRampToValueAtTime`](/en-US/docs/Web/API/AudioParam/linearRampToValueAtTime)）进行自动化。它们的计算值将传递到处理器的 {{domxref("AudioWorkletProcessor.process", "process()")}} 方法中，以便你相应地塑造节点的输出。

### 处理音频

一个创建自定义音频处理机制的示例算法如下：

1. 创建一个单独的文件；
2. 在该文件中：
   1. 扩展 `AudioWorkletProcessor` 类（参见 ["派生类" 部分](#deriving_classes)）并在其中提供你自己的 {{domxref("AudioWorkletProcessor.process", "process()")}} 方法；
   2. 使用 {{domxref("AudioWorkletGlobalScope.registerProcessor()")}} 方法注册处理器；
3. 使用音频上下文的 {{domxref("BaseAudioContext.audioWorklet", "audioWorklet")}} 属性上的 {{domxref("Worklet.addModule", "addModule()")}} 方法加载该文件；
4. 基于该处理器创建一个 {{domxref("AudioWorkletNode")}}。处理器将由 `AudioWorkletNode` 构造函数在内部实例化。
5. 将该节点连接到其他节点。

## 示例

在下面的示例中，我们创建一个输出白噪声的自定义 {{domxref("AudioWorkletNode")}}。

首先，我们需要定义一个输出白噪声的自定义 `AudioWorkletProcessor`，并注册它。请注意，这应该在单独的文件中完成。

```js
// white-noise-processor.js
class WhiteNoiseProcessor extends AudioWorkletProcessor {
  process(inputs, outputs, parameters) {
    const output = outputs[0];
    output.forEach((channel) => {
      for (let i = 0; i < channel.length; i++) {
        channel[i] = Math.random() * 2 - 1;
      }
    });
    return true;
  }
}

registerProcessor("white-noise-processor", WhiteNoiseProcessor);
```

接下来，在我们的主脚本文件中，我们将加载处理器，创建 {{domxref("AudioWorkletNode")}} 的实例，并将处理器的名称传递给它，然后将节点连接到音频图。

```js
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule("white-noise-processor.js");
const whiteNoiseNode = new AudioWorkletNode(
  audioContext,
  "white-noise-processor",
);
whiteNoiseNode.connect(audioContext.destination);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [使用 AudioWorklet](/en-US/docs/Web/API/Web_Audio_API/Using_AudioWorklet)