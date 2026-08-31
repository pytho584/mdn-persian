---
title: "AudioPlaybackStats"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioPlaybackStats"
translated_by: "n8n + AI"
---

---
title: AudioPlaybackStats
slug: Web/API/AudioPlaybackStats
page-type: web-api-interface
status:
  - experimental
browser-compat: api.AudioPlaybackStats
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

**`AudioPlaybackStats`** 接口属于 [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)，提供与关联 {{domxref("AudioContext")}} 相关的时长、欠载和延迟统计信息。这些统计信息可帮助你测量音频延迟和故障。

可以通过 {{domxref("AudioContext.playbackStats")}} 属性访问音频上下文的 `AudioPlaybackStats` 对象。返回的 `AudioPlaybackStats` 对象是实时的——其包含的属性值每秒更新一次。

## 描述

在播放音频的应用中，测量音频 {{glossary("latency")}} 和欠载是很有益的，因为两者都可能导致音频体验不佳：

- **音频延迟**
  - : 指用户激活控件（如播放按钮）与实际听到音频之间的延迟量度。显著的延迟会让应用感觉反应迟钝。
- **欠载**
  - : 当音频应用在缓冲的音频数据播放完之前没有新数据补充时，会出现播放间隙——也就是说，它无法足够快地向输出设备提供音频帧。这可能是由于音频图复杂度、CPU 过载或其他音频程序故障导致的。结果是听到“卡顿”——咔嗒声、砰声或音频丢失——因为应用没有可播放的内容，只能用静音或噪声填充这段间隙。

如果检测到欠载，应采取行动避免未来再次发生——例如提供更大的缓冲区或释放系统资源。谨慎使用更大的缓冲区，因为这会增加延迟；实现平衡很重要。可以通过简化所需的处理或减小播放缓冲区大小来降低延迟。

Web 音频性能因设备而异，从高端现代桌面计算机到低端廉价手机。`AudioPlaybackStats` 对象允许你收集用户的遥测数据，以了解你的应用在“现实世界”中的表现。使用这些数据来识别并响应延迟和欠载问题。

例如，你可以创建一个“自适应”音频系统，当检测到欠载或延迟超过某个阈值（音频开始卡顿时）时，采取以下措施：

- 通过减少同时播放的最大声部数或移除复杂滤镜来降低计算负载。
- 提示用户关闭其他标签页或应用，或切换音频输出设备。

### 接口提供的欠载统计

欠载的定义基于**欠载帧**和**欠载事件**：

- 欠载帧
  - : 当音频上下文没有实际音频数据时，由输出设备播放的音频帧，在 Web 应用中通常是静音。
- 欠载事件
  - : 一段连续的欠载帧的播放。欠载事件的持续时间是这段欠载帧序列的总时长。

自音频上下文初始化以来发生的欠载事件数量由 {{domxref("AudioPlaybackStats.underrunEvents")}} 属性报告，这些欠载事件的持续时间由 {{domxref("AudioPlaybackStats.underrunDuration")}} 属性报告。这样你可以了解音频因欠载而中断的频率和时长。

### 接口提供的延迟统计

音频上下文的延迟可以通过 {{domxref("AudioPlaybackStats.averageLatency")}}、{{domxref("AudioPlaybackStats.minimumLatency")}} 和 {{domxref("AudioPlaybackStats.maximumLatency")}} 属性进行测量。

可以通过 {{domxref("AudioContext.outputLatency")}} 属性获取音频上下文的即时播放延迟；但这是一个瞬时值，波动很快。`AudioPlaybackStats` 提供了一段时间内的平均、最小和最大延迟，这对于识别持续存在的性能问题更有用。

## 实例属性

- {{domxref("AudioPlaybackStats.averageLatency")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : 一个数字，表示自音频上下文初始化以来或自上次调用 {{domxref("AudioPlaybackStats.resetLatency()")}} 以来的平均延迟。
- {{domxref("AudioPlaybackStats.minimumLatency")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : 一个数字，表示自音频上下文初始化以来或自上次调用 {{domxref("AudioPlaybackStats.resetLatency()")}} 以来的最小延迟。
- {{domxref("AudioPlaybackStats.maximumLatency")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : 一个数字，表示自音频上下文初始化以来或自上次调用 {{domxref("AudioPlaybackStats.resetLatency()")}} 以来的最大延迟。
- {{domxref("AudioPlaybackStats.totalDuration")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : 一个数字，表示自音频上下文初始化以来所有音频帧的总时长。
- {{domxref("AudioPlaybackStats.underrunDuration")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : 一个数字，表示自音频上下文初始化以来发生的欠载事件的总时长。
- {{domxref("AudioPlaybackStats.underrunEvents")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : 一个数字，表示自音频上下文初始化以来发生的欠载事件次数。

## 实例方法

- {{domxref("AudioPlaybackStats.resetLatency()")}} {{experimental_inline}}
  - : 将延迟统计测量区间的起始时间重置为当前时间。
- {{domxref("AudioPlaybackStats.toJSON()")}} {{experimental_inline}}
  - : 一个 {{Glossary("Serialization","序列化器")}}，返回 `AudioPlaybackStats` 对象的 JSON 表示。

## 示例

### 报告音频播放统计信息

此示例演示如何通过 `AudioPlaybackStats` 对象访问并报告音频统计信息。

#### HTML

我们包含三个 {{htmlelement("button")}} 元素——一个用于开始播放音频，一个用于获取并显示一组统计信息，另一个用于运行 {{domxref("AudioPlaybackStats.resetLatency()")}} 方法。我们还包含一个 {{htmlelement("ul")}} 元素，统计信息将显示在其中。

```html live-sample___playback-stats
<p>
  <button class="play">Play audio</button>
  <button class="stats">Display stats</button>
  <button class="reset">Reset latency</button>
</p>
<hr />
<ul class="output"></ul>
```

```css hidden live-sample___playback-stats
ul {
  width: 80%;
  margin: 0 auto;
}
li {
  margin-bottom: 10px;
}
```

#### JavaScript

在我们的 JavaScript 中，首先获取按钮和输出列表的引用。我们还会禁用统计信息和重置按钮，因为它们在初始状态下不会执行任何操作。一旦它们附加了事件监听器，我们会再次启用它们。

```js live-sample___playback-stats
const playBtn = document.querySelector(".play");
const statsBtn = document.querySelector(".stats");
const resetBtn = document.querySelector(".reset");
const output = document.querySelector(".output");

statsBtn.disabled = true;
resetBtn.disabled = true;
```

接下来，我们为播放按钮添加一个 `click` 事件监听器，以便在点击时：

- 创建一个新的 {{domxref("AudioContext")}}，并禁用播放按钮，防止再次点击。
- 运行一些特性检测代码，检查 {{domxref("AudioContext.playbackStats")}} 属性是否存在。如果不存在，我们会在输出列表的一个列表项中显示“你的浏览器不支持 `AudioPlaybackStats`。”消息，并 `return` 函数。
- 创建一个基本的音频图，包含一个 {{domxref("OscillatorNode")}} 和一个 {{domxref("GainNode")}}，并启动振荡器播放。
- 启用统计信息按钮，并为其添加 `click` 事件监听器，以便在点击时将音频上下文的 `AudioPlaybackStats` 对象中可用的不同统计信息写入一个文本字符串，并显示在输出列表的一个列表项中。
- 启用重置按钮，并为其添加 `click` 事件监听器，以便在点击时运行 {{domxref("AudioPlaybackStats.resetLatency()")}} 方法。

```js live-sample___playback-stats
playBtn.addEventListener("click", () => {
  const audioCtx = new AudioContext();
  playBtn.disabled = true;

  if (!audioCtx.playbackStats) {
    const listItem = document.createElement("li");
    listItem.textContent = "Your browser doesn't support AudioPlaybackStats.";
    output.appendChild(listItem);
    return;
  }

  const oscillator = audioCtx.createOscillator();
  oscillator.type = "square";
  oscillator.frequency.setValueAtTime(100, audioCtx.currentTime);
  const gain = audioCtx.createGain();
  gain.gain.value = 0.006;

  oscillator.connect(gain);
  gain.connect(audioCtx.destination);
  oscillator.start();

  const stats = audioCtx.playbackStats;

  statsBtn.disabled = false;
  statsBtn.addEventListener("click", () => {
    const listItem = document.createElement("li");
    const statsText = `Underrun duration: ${stats.underrunDuration}
                       Underrun events: ${stats.underrunEvents}
                       Total duration: ${stats.totalDuration}
                       Average latency: ${stats.averageLatency}
                       Min latency: ${stats.minimumLatency}
                       Max latency: ${stats.maximumLatency}`;
    listItem.textContent = statsText;
    output.appendChild(listItem);
  });

  resetBtn.disabled = false;
  resetBtn.addEventListener("click", () => {
    stats.resetLatency();
  });
});
```

#### 结果

渲染后的输出如下所示：

{{embedlivesample("playback-stats", "100%", "400")}}

点击“播放音频”按钮开始播放振荡器音调。现在，当点击“显示统计信息”按钮时，你会看到 `AudioPlaybackStats` 对象中可用的不同统计信息显示在一个列表项中。

如果点击“重置延迟”按钮，然后点击“显示统计信息”按钮，新的统计信息将出现，但最小延迟将不再为零。这是因为现在延迟是从点击“重置延迟”按钮时开始测量的，而不是从音频上下文初始化时开始测量的。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)