---
title: "AudioData"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioData"
translated_by: "n8n + AI"
---

---
title: AudioData
slug: Web/API/AudioData
page-type: web-api-interface
browser-compat: api.AudioData
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

**`AudioData`** 接口属于 [WebCodecs API](/en-US/docs/Web/API/WebCodecs_API)，表示一个音频样本。

`AudioData` 是一个[可转移对象](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects)。

## 描述

音轨由一系列音频样本组成，每个样本表示一个捕获到的声音时刻。`AudioData` 对象就是这样一个样本的表示。与 [Insertable Streams API](/en-US/docs/Web/API/Insertable_Streams_for_MediaStreamTrack_API) 的接口一起使用时，你可以通过 {{domxref("MediaStreamTrackProcessor")}} 将流拆分为独立的 `AudioData` 对象，或者使用 {{domxref("MediaStreamTrackGenerator")}} 从帧流构建音轨。

> [!NOTE]
> 在 [数字音频概念](/en-US/docs/Web/Media/Guides/Formats/Audio_concepts) 中了解更多关于 Web 音频的信息。

### 媒体资源

`AudioData` 对象包含对附加的**媒体资源**的引用。该媒体资源包含对象所描述的实际音频样本数据。媒体资源由用户代理维护，直到不再被 `AudioData` 对象引用时才会被释放，例如调用 {{domxref("AudioData.close()")}} 时。

### 平面和音频格式

要获取 `AudioData` 的样本格式，请使用 {{domxref("AudioData.format")}} 属性。格式可以描述为**交错**或**平面**。在交错格式中，不同通道的音频样本被排列在一个单独的缓冲区中，该缓冲区称为**平面**。该平面的元素数量等于 {{domxref("AudioData.numberOfFrames")}} \* {{domxref("AudioData.numberOfChannels")}}。

在平面格式中，平面的数量等于 {{domxref("AudioData.numberOfChannels")}}，每个平面是一个缓冲区，其元素数量等于 {{domxref("AudioData.numberOfFrames")}}。

## 构造函数

- {{domxref("AudioData.AudioData", "AudioData()")}}
  - : 创建一个新的 `AudioData` 对象。

## 实例属性

- {{domxref("AudioData.format")}} {{ReadOnlyInline}}
  - : 返回音频的样本格式。
- {{domxref("AudioData.sampleRate")}} {{ReadOnlyInline}}
  - : 返回音频的采样率，单位 Hz。
- {{domxref("AudioData.numberOfFrames")}} {{ReadOnlyInline}}
  - : 返回帧数。
- {{domxref("AudioData.numberOfChannels")}} {{ReadOnlyInline}}
  - : 返回音频通道数。
- {{domxref("AudioData.duration")}} {{ReadOnlyInline}}
  - : 返回音频的时长，单位微秒。
- {{domxref("AudioData.timestamp")}} {{ReadOnlyInline}}
  - : 返回音频的时间戳，单位微秒。

## 实例方法

- {{domxref("AudioData.allocationSize()")}}
  - : 返回根据传递给方法的选项过滤后，存储样本所需的字节数。
- {{domxref("AudioData.copyTo()")}}
  - : 将 `AudioData` 对象指定平面中的样本复制到目标位置。
- {{domxref("AudioData.clone()")}}
  - : 创建一个新的 `AudioData` 对象，其引用的媒体资源与原始对象相同。
- {{domxref("AudioData.close()")}}
  - : 清除所有状态并释放对媒体资源的引用。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}