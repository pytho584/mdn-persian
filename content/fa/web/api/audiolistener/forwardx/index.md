---
title: "AudioListener: forwardX property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/forwardX"
translated_by: "n8n + AI"
---

---
title: "AudioListener: forwardX property"
short-title: forwardX
slug: Web/API/AudioListener/forwardX
page-type: web-api-instance-property
browser-compat: api.AudioListener.forwardX
---

{{ APIRef("Web Audio API") }}

`forwardX` 只读属性是 {{ domxref("AudioListener") }} 接口的一个 {{domxref("AudioParam")}}，表示定义监听器所指向的前进方向的向量的 x 值。

> [!NOTE]
> 当与 {{domxref("PannerNode")}} 一起使用且其 {{domxref("PannerNode.panningModel", "panningModel")}} 设置为 equalpower 时，该参数为 _a-rate_，否则为 _k-rate_。

## 值

一个 {{domxref("AudioParam")}}。其默认值为 0，范围可以是正无穷到负无穷。

## 示例

示例代码参见 [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples)。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用 Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)