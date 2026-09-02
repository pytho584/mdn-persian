---
title: "MIDIMessageEvent: data property"
short-title: data
slug: Web/API/MIDIMessageEvent/data
page-type: web-api-instance-property
browser-compat: api.MIDIMessageEvent.data
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

**`data`**只读属性属于{{domxref("MIDIMessageEvent")}}接口，返回单条 MIDI 消息的 MIDI 数据字节。

## 值

一个 {{jsxref("Uint8Array")}}。

## 示例

在以下示例中，我们对所有输入端口监听 {{domxref("MIDIInput.midimessage_event", "midimessage")}} 事件。收到消息时，`data` 的值会被打印到控制台。

```js
inputs.forEach((input) => {
  input.onmidimessage = (message) => {
    console.log(message.data);
  };
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
