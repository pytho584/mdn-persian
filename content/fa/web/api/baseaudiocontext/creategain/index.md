---
title: "BaseAudioContext: createGain() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createGain"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createGain() method"
short-title: createGain()
slug: Web/API/BaseAudioContext/createGain
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createGain
---

{{ APIRef("Web Audio API") }}

{{ domxref("BaseAudioContext") }} 接口的 `createGain()` 方法用于创建一个 {{ domxref("GainNode") }}，该节点可用于控制音频图的整体增益（或音量）。

> [!NOTE]
> {{domxref("GainNode.GainNode", "GainNode()")}} 构造函数是创建 {{domxref("GainNode")}} 的推荐方式；参见
> [创建 AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode)。

## 语法

```js-nolint
createGain()
```

### 参数

无。

### 返回值

一个 {{domxref("GainNode")}}，它接收一个或多个音频源作为输入，并输出音量已按该节点的 {{domxref("GainNode.gain")}} [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) 参数所指定的增益（音量）调整后的音频。

## 示例

以下示例展示了 {{domxref("AudioContext")}} 的基本用法：创建一个 `GainNode`，然后在点击“静音”按钮时通过修改 `gain` 属性值来静音和取消静音音频。

下面的代码片段不能直接运行——有关完整可运行的示例，请参阅我们的
[Voice-change-O-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) 演示（[查看源代码](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js)）。

```html
<div>
  <button class="mute">Mute button</button>
</div>
```

```js
const audioCtx = new AudioContext();
const gainNode = audioCtx.createGain();
const mute = document.querySelector(".mute");
let source;

if (navigator.mediaDevices.getUserMedia) {
  navigator.mediaDevices.getUserMedia(
    // constraints - only audio needed for this app
    {
      audio: true,
    },

    // Success callback
    (stream) => {
      source = audioCtx.createMediaStreamSource(stream);
    },

    // Error callback
    (err) => {
      console.error(`The following gUM error occurred: ${err}`);
    },
  );
} else {
  console.error("getUserMedia not supported on your browser!");
}

source.connect(gainNode);
gainNode.connect(audioCtx.destination);

// …

mute.onclick = () => {
  if (mute.id === "") {
    // 0 means mute. If you still hear something, make sure you haven't
    // connected your source into the output in addition to using the GainNode.
    gainNode.gain.setValueAtTime(0, audioCtx.currentTime);
    mute.id = "activated";
    mute.textContent = "Unmute";
  } else {
    gainNode.gain.setValueAtTime(1, audioCtx.currentTime);
    mute.id = "";
    mute.textContent = "Mute";
  }
};
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)