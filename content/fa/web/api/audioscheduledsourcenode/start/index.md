---
title: "AudioScheduledSourceNode: start() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioScheduledSourceNode/start"
translated_by: "n8n + AI"
---

---
title: "AudioScheduledSourceNode: start() method"
short-title: start()
slug: Web/API/AudioScheduledSourceNode/start
page-type: web-api-instance-method
browser-compat: api.AudioScheduledSourceNode.start
---

{{APIRef("Web Audio API")}}

{{domxref("AudioScheduledSourceNode")}} 接口的 `start()` 方法会在指定时间安排声音开始播放。如果未指定时间，则声音会立即开始播放。

## 语法

```js-nolint
start()
start(when)
```

### 参数

- `when` {{optional_inline}}
  - : 声音开始播放的时间，以秒为单位。该值使用与 {{domxref("AudioContext")}} 在其 {{domxref("BaseAudioContext/currentTime", "currentTime")}} 属性中相同的时间坐标系。值为 0（或完全省略 `when` 参数）会导致声音立即开始播放。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

- `InvalidStateNode` {{domxref("DOMException")}}
  - : 如果节点已经启动，则抛出此异常。即使节点因先前调用 {{domxref("AudioScheduledSourceNode.stop", "stop()")}} 而不再运行，也会发生此错误。
- {{jsxref("RangeError")}}
  - : 如果为 `when` 指定的值为负数，则抛出此异常。

## 示例

此示例演示如何创建一个 {{domxref("OscillatorNode")}}，并安排其在 2 秒后开始播放，并在其之后 1 秒停止播放。时间是通过将所需的秒数添加到由 {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} 返回的上下文的当前时间戳来计算的。

```js
context = new AudioContext();
osc = context.createOscillator();
osc.connect(context.destination);

/* 安排振荡器的开始和停止时间 */

osc.start(context.currentTime + 2);
osc.stop(context.currentTime + 3);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("AudioScheduledSourceNode.stop", "stop()")}}
- {{domxref("AudioScheduledSourceNode")}}
- {{domxref("AudioBufferSourceNode")}}
- {{domxref("ConstantSourceNode")}}
- {{domxref("OscillatorNode")}}