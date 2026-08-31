---
title: "BaseAudioContext: createOscillator() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createOscillator"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createOscillator() method"
short-title: createOscillator()
slug: Web/API/BaseAudioContext/createOscillator
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createOscillator
---

{{APIRef("Web Audio API")}}

`createOscillator()` 方法属于 {{domxref("BaseAudioContext")}} 接口，用于创建一个 {{domxref("OscillatorNode")}}，这是一种表示周期性波形的音频源。它基本上可以生成一个恒定音调。

> [!NOTE]
> 推荐使用 {{domxref("OscillatorNode.OscillatorNode", "OscillatorNode()")}} 构造函数来创建 {{domxref("OscillatorNode")}}；参见 [创建 AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode)。

## 语法

```js-nolint
createOscillator()
```

### 参数

无。

### 返回值

一个 {{domxref("OscillatorNode")}}。

## 示例

以下示例展示了使用 AudioContext 创建振荡器节点的基本用法。有关应用实例/信息，请查看我们的 [Violent Theremin 演示](https://mdn.github.io/webaudio-examples/violent-theremin/)（相关代码见 [app.js](https://github.com/mdn/webaudio-examples/blob/main/violent-theremin/scripts/app.js)）；更多信息也可参见我们的 {{domxref("OscillatorNode")}} 页面。

```js
// create web audio api context
const audioCtx = new AudioContext();

// create Oscillator node
const oscillator = audioCtx.createOscillator();

oscillator.type = "square";
oscillator.frequency.setValueAtTime(3000, audioCtx.currentTime); // value in hertz
oscillator.connect(audioCtx.destination);
oscillator.start();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)