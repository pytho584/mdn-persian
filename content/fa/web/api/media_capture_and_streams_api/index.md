---
title: "Media Capture and Streams API (Media Stream)"
slug: Web/API/Media_Capture_and_Streams_API
page-type: web-api-overview
browser-compat:
  - api.MediaStream
  - api.MediaStreamTrack
  - api.MediaDevices
  - api.MediaDeviceInfo
  - api.InputDeviceInfo
  - api.CanvasCaptureMediaStreamTrack
spec-urls:
  - https://w3c.github.io/mediacapture-main/
  - https://w3c.github.io/mediacapture-fromelement/
---

{{DefaultAPISidebar("Media Capture and Streams")}}

**رسانه‌برداری و جریان‌ها** (Media Capture and Streams) که اغلب **API جریان‌های رسانه‌ای** یا **MediaStream API** نامیده می‌شود، یک API مرتبط با [WebRTC](/en-US/docs/Web/API/WebRTC_API) است که پشتیبانی از پخش جریانی داده‌های صوتی و تصویری را فراهم می‌کند.

این API رابط‌ها و روش‌هایی را برای کار با جریان‌ها و trackهای تشکیل‌دهنده آن‌ها، محدودیت‌های مرتبط با قالب‌های داده، callbackهای موفقیت و خطا هنگام استفادهٔ ناهمگام از داده‌ها، و رویدادهایی که در این فرآیند رخ می‌دهند، ارائه می‌دهد.

## مفاهیم و کاربرد

این API بر پایهٔ دستکاری یک شیء {{domxref("MediaStream")}} است که یک جریان دادهٔ صوتی یا تصویری را نشان می‌دهد. نمونه‌ای را در [دریافت جریان رسانه‌ای](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Taking_still_photos#demo) ببینید.

یک `MediaStream` از صفر یا چند شیء {{domxref("MediaStreamTrack")}} تشکیل شده است که **track**های مختلف صوتی یا تصویری را نشان می‌دهند. هر `MediaStreamTrack` ممکن است یک یا چند **کانال** داشته باشد. کانال کوچک‌ترین واحد یک جریان رسانه‌ای است، مانند سیگنال صوتی مرتبط با یک بلندگوی خاص، مثل _چپ_ یا _راست_ در یک track صوتی استریو.

اشیاء `MediaStream` دارای یک **ورودی** و یک **خروجی** واحد هستند. یک شیء `MediaStream` که توسط {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} تولید می‌شود _محلی_ نامیده می‌شود و منبع ورودی آن یکی از دوربین‌ها یا میکروفون‌های کاربر است. یک `MediaStream` غیرمحلی ممکن است یک عنصر رسانه‌ای مانند {{HTMLElement("video")}} یا {{HTMLElement("audio")}} را نشان دهد، جریانی که از طریق شبکه آمده و از طریق API وب‌آرتی‌سی {{domxref("RTCPeerConnection")}} به دست آمده است، یا جریانی که با استفاده از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) و {{domxref("MediaStreamAudioDestinationNode")}} ایجاد شده است.

خروجی شیء `MediaStream` به یک **مصرف‌کننده** متصل می‌شود. مصرف‌کننده می‌تواند یک عنصر رسانه‌ای مانند {{HTMLElement("audio")}} یا {{HTMLElement("video")}}، API وب‌آرتی‌سی {{domxref("RTCPeerConnection")}} یا یک {{domxref("MediaStreamAudioSourceNode")}} از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) باشد.

## رابط‌ها

در این مقاله‌های مرجع، اطلاعات بنیادی موردنیاز دربارهٔ هر یک از رابط‌های تشکیل‌دهندهٔ API رسانه‌برداری و جریان‌ها را خواهید یافت.

- {{domxref("CanvasCaptureMediaStreamTrack")}}
- {{domxref("InputDeviceInfo")}}
- {{domxref("MediaDeviceInfo")}}
- {{domxref("MediaDevices")}}
- {{domxref("MediaStream")}}
- {{domxref("MediaStreamTrack")}}
- {{domxref("MediaStreamTrackEvent")}}
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaTrackSettings")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("OverconstrainedError")}}

## رویدادها

- {{domxref("MediaStream/addtrack_event", "addtrack")}}
- {{domxref("MediaStreamTrack/ended_event", "ended")}}
- {{domxref("MediaStreamTrack/mute_event", "mute")}}
- {{domxref("MediaStream/removetrack_event", "removetrack")}}
- {{domxref("MediaStreamTrack/unmute_event", "unmute")}}

## راهنماها و آموزش‌ها

مقالهٔ [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مفاهیم **محدودیت‌ها** و **قابلیت‌ها** و همچنین تنظیمات رسانه را بحث می‌کند و شامل یک [تمرین‌دهندهٔ محدودیت](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) است که به شما امکان می‌دهد نتایج اعمال مجموعه‌های مختلف محدودیت بر trackهای صوتی و تصویری ورودی از دستگاه‌های A/V رایانه (مانند وب‌کم و میکروفون) را آزمایش کنید.

مقالهٔ [گرفتن عکس‌های ثابت با getUserMedia()](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Taking_still_photos) نحوهٔ استفاده از [`getUserMedia()`](/en-US/docs/Web/API/MediaDevices/getUserMedia) را برای دسترسی به دوربین رایانه یا تلفن همراه با پشتیبانی از `getUserMedia()` و گرفتن عکس با آن نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebRTC](/en-US/docs/Web/API/WebRTC_API) - صفحهٔ معرفی این API
- [گرفتن عکس‌های ثابت با WebRTC](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Taking_still_photos): یک نمایش و آموزش دربارهٔ استفاده از `getUserMedia()`.