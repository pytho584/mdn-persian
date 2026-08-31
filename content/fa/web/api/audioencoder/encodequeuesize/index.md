---
title: "AudioEncoder: encodeQueueSize property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/encodeQueueSize"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: encodeQueueSize property"
short-title: encodeQueueSize
slug: Web/API/AudioEncoder/encodeQueueSize
page-type: web-api-instance-property
browser-compat: api.AudioEncoder.encodeQueueSize
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

{{domxref("AudioEncoder")}} 接口的 **`encodeQueueSize`** 只读属性返回队列中待处理的编码请求数。

## 值

一个整数，包含请求数。

## 示例

以下示例将队列大小打印到控制台。

```js
console.log(AudioEncoder.encodeQueueSize);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}