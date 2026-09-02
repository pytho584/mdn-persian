---
title: MediaStreamTrackEvent
slug: Web/API/MediaStreamTrackEvent
page-type: web-api-interface
browser-compat: api.MediaStreamTrackEvent
---

{{APIRef("Media Capture and Streams")}}

رابط **`MediaStreamTrackEvent`** از {{domxref("Media Capture and Streams API", "", "", "nocode")}} رویدادهایی را بازنمایی می‌کند که نشان می‌دهند با فراخوانی متدهای [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)، ترک‌هایی به یک {{domxref("MediaStream")}} اضافه شده یا از آن حذف شده‌اند. این رویدادها هنگام رخ دادن چنین تغییرهایی به همان جریان ارسال می‌شوند.

{{InheritanceDiagram}}

رویدادهای مبتنی بر این رابط عبارت‌اند از {{domxref("MediaStream/addtrack_event", "addtrack")}} و {{domxref("MediaStream/removetrack_event", "removetrack")}}.

## سازنده

- {{domxref("MediaStreamTrackEvent.MediaStreamTrackEvent", "MediaStreamTrackEvent()")}}
  - : یک `MediaStreamTrackEvent` جدید با پیکربندی مشخص‌شده می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، یعنی {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("MediaStreamTrackEvent.track")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("MediaStreamTrack")}} برمی‌گرداند که ترک مرتبط با رویداد را نشان می‌دهد.

## متدهای نمونه

_همچنین متدهای رابط والد خود، یعنی {{domxref("Event")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaStream")}}: رویدادهای {{domxref("MediaStream/addtrack_event", "addtrack")}} و {{domxref("MediaStream/removetrack_event", "removetrack")}}
- {{domxref("MediaStreamTrack")}}
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)