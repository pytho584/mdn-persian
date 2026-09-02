---
title: "MediaStreamAudioSourceNode: mediaStream property"
short-title: mediaStream
slug: Web/API/MediaStreamAudioSourceNode/mediaStream
page-type: web-api-instance-property
browser-compat: api.MediaStreamAudioSourceNode.mediaStream
---

{{APIRef("Web Audio API")}}

ویژگی فقط‌خواندنی **`mediaStream`** از رابط {{domxref("MediaStreamAudioSourceNode")}}، {{domxref("MediaStream")}}ی را نشان می‌دهد که شامل ترک صوتی مورد استفاده این گره برای دریافت صدا است.

این جریان هنگام ایجاد گره مشخص شده است؛ یا با استفاده از سازندهٔ {{domxref("MediaStreamAudioSourceNode.MediaStreamAudioSourceNode", "MediaStreamAudioSourceNode()")}} یا با متد {{domxref("AudioContext.createMediaStreamSource()")}}.

## مقدار

یک {{domxref("MediaStream")}} که نشان‌دهندهٔ جریانی است که شامل {{domxref("MediaStreamTrack")}} به‌عنوان منبع صوتی گره است.

{{Glossary("user agent")}} (عامل کاربر) از اولین ترک صوتی که در جریان مشخص‌شده پیدا می‌کند به‌عنوان منبع صوتی این گره استفاده می‌کند. با این حال، هیچ راهی برای اطمینان از اینکه در جریان‌های چند‌ترکه کدام ترک استفاده خواهد شد وجود ندارد. اگر ترک خاصی برایتان مهم است یا به دسترسی به خود ترک نیاز دارید، بهتر است به‌جای آن از {{domxref("MediaStreamTrackAudioSourceNode")}} استفاده کنید.

## مثال‌ها

```js
const audioCtx = new window.AudioContext();
let options = {
  mediaStream: stream,
};

let source = new MediaStreamAudioSourceNode(audioCtx, options);
console.log(source.mediaStream);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}