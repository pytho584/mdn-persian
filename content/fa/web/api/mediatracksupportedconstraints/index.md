---
title: MediaTrackSupportedConstraints
slug: Web/API/MediaTrackSupportedConstraints
page-type: web-api-interface
spec-urls: https://w3c.github.io/mediacapture-main/#media-track-supported-constraints
---

{{APIRef("Media Capture and Streams")}}

واژه‌نامه (dictionary) **`MediaTrackSupportedConstraints`** فهرست ویژگی‌های قابل محدودیت (constrainable properties) را که توسط {{Glossary("user agent")}} (نماینده کاربر) یا مرورگر در پیاده‌سازی شیء {{domxref("MediaStreamTrack")}} شناسایی می‌شوند، تعیین می‌کند. یک شیء منطبق بر `MediaTrackSupportedConstraints` توسط {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود.

به دلیل نحوه کار تعریف رابط‌ها (interface definitions) در WebIDL، اگر محدودیتی (constraint) درخواست شود اما پشتیبانی نشود، خطایی رخ نخواهد داد. در عوض، محدودیت‌های مشخص شده اعمال می‌شوند و هر محدودیت ناشناخته‌ای از درخواست حذف می‌گردد. این موضوع می‌تواند منجر به خطاهای گیج‌کننده و دشوار برای رفع اشکال شود. بنابراین، قبل از تلاش برای تنظیم محدودیت‌ها، حتماً از `getSupportedConstraints()` برای دریافت این اطلاعات استفاده کنید، اگر نیاز دارید تفاوت بین نادیده گرفتن بی‌صدا یک محدودیت و پذیرفته شدن یک محدودیت را بدانید.

یک مجموعه محدودیت (constraint set) واقعی با استفاده از یک شیء مبتنی بر واژه‌نامه {{domxref("MediaTrackConstraints")}} توصیف می‌شود.

برای یادگیری بیشتر در مورد نحوه کار محدودیت‌ها، به [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مراجعه کنید.

## ویژگی‌های نمونه (Instance properties)

ترکیبی از ویژگی‌های زیر (اما نه لزوماً همه) روی شیء وجود خواهند داشت.

- {{domxref("MediaTrackSupportedConstraints.aspectRatio", "aspectRatio")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`aspectRatio`](/en-US/docs/Web/API/MediaTrackConstraints/aspectRatio) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.autoGainControl", "autoGainControl")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`autoGainControl`](/en-US/docs/Web/API/MediaTrackConstraints/autoGainControl) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.channelCount", "channelCount")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`channelCount`](/en-US/docs/Web/API/MediaTrackConstraints/channelCount) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.deviceId", "deviceId")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`deviceId`](/en-US/docs/Web/API/MediaTrackConstraints/deviceId) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.echoCancellation", "echoCancellation")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`echoCancellation`](/en-US/docs/Web/API/MediaTrackConstraints/echoCancellation) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.facingMode", "facingMode")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`facingMode`](/en-US/docs/Web/API/MediaTrackConstraints/facingMode) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.frameRate", "frameRate")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`frameRate`](/en-US/docs/Web/API/MediaTrackConstraints/frameRate) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.groupId", "groupId")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`groupId`](/en-US/docs/Web/API/MediaTrackConstraints/groupId) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.height", "height")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`height`](/en-US/docs/Web/API/MediaTrackConstraints/height) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.latency", "latency")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`latency`](/en-US/docs/Web/API/MediaTrackConstraints/latency) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.noiseSuppression", "noiseSuppression")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`noiseSuppression`](/en-US/docs/Web/API/MediaTrackConstraints/noiseSuppression) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.restrictOwnAudio", "restrictOwnAudio")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت {{domxref("MediaTrackConstraints.restrictOwnAudio", "restrictOwnAudio")}} در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.resizeMode", "resizeMode")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`resizeMode`](/en-US/docs/Web/API/MediaTrackConstraints/resizeMode) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.sampleRate", "sampleRate")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`sampleRate`](/en-US/docs/Web/API/MediaTrackConstraints/sampleRate) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.sampleSize", "sampleSize")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`sampleSize`](/en-US/docs/Web/API/MediaTrackConstraints/sampleSize) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.suppressLocalAudioPlayback", "suppressLocalAudioPlayback")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`suppressLocalAudioPlayback`](/en-US/docs/Web/API/MediaTrackConstraints/suppressLocalAudioPlayback) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.volume", "volume")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`volume`](/en-US/docs/Web/API/MediaTrackConstraints/volume) در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.width", "width")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت [`width`](/en-US/docs/Web/API/MediaTrackConstraints/width) در محیط فعلی، `true` است.

### ویژگی‌های نمونه مخصوص ره‌گیری‌های صفحه اشتراکی (shared screen tracks)

برای ره‌گیری‌هایی (tracks) که شامل منابع ویدئویی از صفحه کاربر هستند، ویژگی‌های اضافی زیر ممکن است گنجانده شوند، علاوه بر ویژگی‌های موجود برای ره‌گیری‌های ویدئویی:

- {{domxref("MediaTrackSupportedConstraints.displaySurface", "displaySurface")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت {{domxref("MediaTrackConstraints.displaySurface", "displaySurface")}} در محیط فعلی، `true` است.
- {{domxref("MediaTrackSupportedConstraints.logicalSurface", "logicalSurface")}}
  - : یک مقدار بولین که در صورت پشتیبانی از محدودیت {{domxref("MediaTrackConstraints.logicalSurface", "logicalSurface")}} در محیط فعلی، `true` است.

## مشخصات (Specifications)

{{Specifications}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getUserMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}