---
title: "BaseAudioContext: createPanner() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createPanner"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createPanner() method"
short-title: createPanner()
slug: Web/API/BaseAudioContext/createPanner
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createPanner
---

{{ APIRef("Web Audio API") }}

`createPanner()` 方法属于 {{ domxref("BaseAudioContext") }} 接口，用于创建一个新的 {{domxref("PannerNode")}}，该节点用于在三维空间中对传入的音频流进行空间化处理。

panner 节点相对于 AudioContext 的 {{domxref("AudioListener") }}（由 {{domxref("BaseAudioContext/listener", "AudioContext.listener")}} 属性定义）进行空间化处理，该监听器表示听音频的人的位置和朝向。

> [!NOTE]
> 推荐使用 {{domxref("PannerNode.PannerNode", "PannerNode()")}} 构造函数来创建 {{domxref("PannerNode")}}；参见 [创建 AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode)。

## 语法

```js-nolint
createPanner()
```

### 参数

无。

### 返回值

一个 {{domxref("PannerNode")}}。

## 示例

在以下示例中，你可以看到如何使用 `createPanner()` 方法、{{domxref("AudioListener")}} 和 {{domxref("PannerNode")}} 来控制音频的空间化。通常，你首先定义音频监听器和 panner（音源）在三维空间中的初始位置，然后在应用程序使用过程中更新其中一个或两个的位置。例如，你可能在游戏世界中移动一个角色，并且希望当角色靠近或远离音响等音乐播放器时，音频传递能够逼真地变化。在示例中，你可以看到通过 `moveRight()`、`moveLeft()` 等函数来控制这一过程，这些函数通过 `PositionPanner()` 函数为 panner 位置设置新值。

要查看完整的实现，请参阅我们的 [panner-node 示例](https://mdn.github.io/webaudio-examples/panner-node/)（[查看源代码](https://github.com/mdn/webaudio-examples/tree/main/panner-node)）——这个演示将你传送到 2.5D 的“金属房间”中，你可以在音箱上播放一首曲子，然后绕着音箱走动，观察声音如何变化！

请注意，我们使用了一些特性检测，以便在浏览器支持的情况下使用较新的属性值（如 {{domxref("AudioListener.forwardX")}}）来设置位置等，如果浏览器不支持这些新属性，则使用较旧的方法（如 {{domxref("AudioListener.setOrientation()")}}）。

```js
// 设置监听器和 panner 的位置信息
const WIDTH = window.innerWidth;
const HEIGHT = window.innerHeight;

const xPos = Math.floor(WIDTH / 2);
const yPos = Math.floor(HEIGHT / 2);
const zPos = 295;

// 定义其他变量

const audioCtx = new AudioContext();

const panner = audioCtx.createPanner();
panner.panningModel = "HRTF";
panner.distanceModel = "inverse";
panner.refDistance = 1;
panner.maxDistance = 10000;
panner.rolloffFactor = 1;
panner.coneInnerAngle = 360;
panner.coneOuterAngle = 0;
panner.coneOuterGain = 0;

if (panner.orientationX) {
  panner.orientationX.setValueAtTime(1, audioCtx.currentTime);
  panner.orientationY.setValueAtTime(0, audioCtx.currentTime);
  panner.orientationZ.setValueAtTime(0, audioCtx.currentTime);
} else {
  panner.setOrientation(1, 0, 0);
}

const listener = audioCtx.listener;

if (listener.forwardX) {
  listener.forwardX.setValueAtTime(0, audioCtx.currentTime);
  listener.forwardY.setValueAtTime(0, audioCtx.currentTime);
  listener.forwardZ.setValueAtTime(-1, audioCtx.currentTime);
  listener.upX.setValueAtTime(0, audioCtx.currentTime);
  listener.upY.setValueAtTime(1, audioCtx.currentTime);
  listener.upZ.setValueAtTime(0, audioCtx.currentTime);
} else {
  listener.setOrientation(0, 0, -1, 0, 1, 0);
}

let source;

const play = document.querySelector(".play");
const stop = document.querySelector(".stop");

const boomBox = document.querySelector(".boom-box");

const listenerData = document.querySelector(".listener-data");
const pannerData = document.querySelector(".panner-data");

leftBound = -xPos + 50;
rightBound = xPos - 50;

xIterator = WIDTH / 150;

// 在这个演示中，监听器始终保持在相同的位置

if (listener.positionX) {
  listener.positionX.setValueAtTime(xPos, audioCtx.currentTime);
  listener.positionY.setValueAtTime(yPos, audioCtx.currentTime);
  listener.positionZ.setValueAtTime(300, audioCtx.currentTime);
} else {
  listener.setPosition(xPos, yPos, 300);
}

listenerData.textContent = `Listener data: X ${xPos} Y ${yPos} Z 300`;

// panner 将随着音箱图形在屏幕上移动而移动
function positionPanner() {
  if (panner.positionX) {
    panner.positionX.setValueAtTime(xPos, audioCtx.currentTime);
    panner.positionY.setValueAtTime(yPos, audioCtx.currentTime);
    panner.positionZ.setValueAtTime(zPos, audioCtx.currentTime);
  } else {
    panner.setPosition(xPos, yPos, zPos);
  }
  pannerData.textContent = `Panner data: X ${xPos} Y ${yPos} Z ${zPos}`;
}
```

> [!NOTE]
> 要确定应用到监听器和 panner 的位置值，以使声音与屏幕上的视觉效果相匹配，需要进行相当多的数学计算，但只要稍加尝试，你很快就会熟悉它。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)