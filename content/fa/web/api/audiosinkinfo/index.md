---
title: "AudioSinkInfo"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioSinkInfo"
translated_by: "n8n + AI"
---

---
title: AudioSinkInfo
slug: Web/API/AudioSinkInfo
page-type: web-api-interface
status:
  - experimental
browser-compat: api.AudioSinkInfo
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

**`AudioSinkInfo`** 是 {{domxref("Web Audio API", "Web Audio API", "", "nocode")}} 的一个接口，表示描述 {{domxref("AudioContext")}} 的 sink ID 的信息，可通过 {{domxref("AudioContext.sinkId")}} 获取。

{{InheritanceDiagram}}

## 实例属性

- {{domxref("AudioSinkInfo.type", "type")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 返回音频输出设备的类型。

## 示例

如果使用 `sinkId` 值 `{ type: 'none' }` 创建新的 {{domxref("AudioContext")}}，则在代码后面调用 {{domxref("AudioContext.sinkId")}} 将返回包含 `type: 'none'` 的 `AudioSinkInfo` 对象。这是目前唯一可用的值。

```js
audioCtx = new window.AudioContext({
  sinkId: { type: "none" },
});

// …

audioCtx.sinkId;
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [SetSinkId 测试示例](https://mdn.github.io/dom-examples/audiocontext-setsinkid/)（查看[源代码](https://github.com/mdn/dom-examples/tree/main/audiocontext-setsinkid)）
- {{domxref("AudioContext.setSinkId()")}}
- {{domxref("AudioContext.sinkId")}}
- {{domxref("AudioContext/sinkchange_event", "sinkchange")}}