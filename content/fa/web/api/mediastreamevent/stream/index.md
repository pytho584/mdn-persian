---
title: "MediaStreamEvent: stream property"
short-title: stream
slug: Web/API/MediaStreamEvent/stream
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MediaStreamEvent.stream
---

{{APIRef("WebRTC")}}{{deprecated_header}}{{Non-standard_header}}

ویژگی فقط‌خواندنی **`MediaStreamEvent.stream`**، شیء {{domxref("MediaStream")}} مرتبط با رویداد را بازمی‌گرداند.

## مثال

```js
pc.onaddstream = (ev) => {
  alert(`A stream (id: '${ev.stream.id}') has been added to this connection.`);
};
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("RTCPeerConnection.addstream_event", "addstream")}}, {{domxref("RTCPeerConnection.removestream_event", "removestream")}}
- {{domxref("RTCPeerConnection")}}