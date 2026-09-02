---
title: "MediaStreamAudioDestinationNode: stream property"
short-title: stream
slug: Web/API/MediaStreamAudioDestinationNode/stream
page-type: web-api-instance-property
browser-compat: api.MediaStreamAudioDestinationNode.stream
---

{{ APIRef("Web Audio API") }}

ویژگی `stream` در interface {{ domxref("AudioContext") }} یک {{domxref("MediaStream")}} را نشان می‌دهد که شامل یک {{domxref("MediaStreamTrack")}} صوتی با همان تعداد کانال‌های خود گره است.

می‌توانید از این ویژگی برای گرفتن یک جریان (stream) از گراف صوتی و هدایت آن به یک ساختار دیگر، مانند [Media Recorder](/en-US/docs/Web/API/MediaStream_Recording_API)، استفاده کنید.

## مقدار

یک {{domxref("MediaStream")}} شامل یک ترک صوتی. این ترک صوتی یک {{domxref("MediaStreamTrack")}} است که ویژگی {{domxref("MediaStreamTrack.kind", "kind")}} آن `audio` است.

## مثال‌ها

برای کد مثال که یک `MediaStreamAudioDestinationNode` می‌سازد و از ویژگی `stream` آن به‌عنوان منبع صوتی برای ضبط استفاده می‌کند، به [`AudioContext.createMediaStreamDestination()`](/en-US/docs/Web/API/AudioContext/createMediaStreamDestination#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)