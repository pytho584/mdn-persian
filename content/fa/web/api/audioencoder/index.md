---
title: "AudioEncoder"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder"
translated_by: "n8n + AI"
---

---
title: AudioEncoder
slug: Web/API/AudioEncoder
page-type: web-api-interface
browser-compat: api.AudioEncoder
---

{{APIRef("WebCodecs API")}}{{SecureContext_Header}}{{AvailableInWorkers("window_and_dedicated")}}

[WebCodecs API](/en-US/docs/Web/API/WebCodecs_API) 的 **`AudioEncoder`** 接口对 {{domxref("AudioData")}} 对象进行编码。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("AudioEncoder.AudioEncoder", "AudioEncoder()")}}
  - : 创建一个新的 `AudioEncoder` 对象。

## 实例属性

_从父接口 {{DOMxRef("EventTarget")}} 继承属性。_

- {{domxref("AudioEncoder.encodeQueueSize")}} {{ReadOnlyInline}}
  - : 一个整数，表示编码队列请求的数量。
- {{domxref("AudioEncoder.state")}} {{ReadOnlyInline}}
  - : 表示底层编解码器的状态，以及是否已配置为进行编码。

### 事件

- {{domxref("AudioEncoder.dequeue_event", "dequeue")}}
  - : 触发以表示 {{domxref("AudioEncoder.encodeQueueSize")}} 的减少。

## 静态方法

- {{domxref("AudioEncoder.isConfigSupported_static", "AudioEncoder.isConfigSupported()")}}
  - : 返回一个 Promise，指示所提供的 `AudioEncoderConfig` 是否受支持。

## 实例方法

_从父接口 {{DOMxRef("EventTarget")}} 继承方法。_

- {{domxref("AudioEncoder.configure()")}}
  - : 将控制消息加入队列，以配置音频编码器用于编码块。
- {{domxref("AudioEncoder.encode()")}}
  - : 将控制消息加入队列，以对给定的 {{domxref("AudioData")}} 对象进行编码。
- {{domxref("AudioEncoder.flush()")}}
  - : 返回一个 Promise，一旦队列中的所有待处理消息完成，该 Promise 就会解决。
- {{domxref("AudioEncoder.reset()")}}
  - : 重置所有状态，包括配置、控制消息队列中的控制消息以及所有待处理的回调。
- {{domxref("AudioEncoder.close()")}}
  - : 结束所有待处理的工作并释放系统资源。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}