---
title: "AudioSession"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioSession"
translated_by: "n8n + AI"
---

---
title: AudioSession
slug: Web/API/AudioSession
page-type: web-api-interface
status:
  - experimental
browser-compat: api.AudioSession
---

{{APIRef("Audio Session API")}}{{SeeCompatTable}}

رابط **`AudioSession`** از [API Audio Session](/en-US/docs/Web/API/Audio_Session_API) به یک صفحه وب اجازه می‌دهد نوع صدایی را که تولید می‌کند اعلام کند — برای مثال پخش موسیقی، تماس ویدیویی، یا یک اعلان کوتاه. پلتفرم از این اعلام برای تصمیم‌گیری درباره نحوه‌ی همزیستی صدای صفحه و صدای سایر برنامه‌ها و تب‌ها استفاده می‌کند — اینکه آیا صدا را مکث کند، کاهش دهد (duck) یا به صورت موازی پخش کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("AudioSession.type")}} {{Experimental_Inline}}
  - : رشته‌ای است که نوع جلسه صوتی را نشان می‌دهد. مقادیر احتمالی شامل `"auto"`, `"playback"`, `"transient"`, `"transient-solo"`, `"ambient"` و `"play-and-record"` هستند.

## مثال‌ها

### تنظیم نوع جلسه صوتی برای یک برنامه کنفرانس ویدیویی

مثال زیر نوع جلسه صوتی را برای یک برنامه کنفرانس ویدیویی روی `"play-and-record"` تنظیم می‌کند. در پلتفرم‌های پشتیبانی‌شده، این سیگنال می‌دهد که صفحه به پخش و ضبط همزمان نیاز دارد، که ممکن است باعث شود سیستم صدا را از طریق خروجی مناسب هدایت کند (مثلاً گوشی به جای بلندگو در دستگاه‌های تلفن همراه) و از قطع شدن صدای سایر برنامه‌ها در طول تماس جلوگیری کند.

```js
navigator.audioSession.type = "play-and-record";

// Start playing remote media
remoteVideo.srcObject = remoteMediaStream;
remoteVideo.play();

// Start capturing local media
const stream = await navigator.mediaDevices.getUserMedia({
  audio: true,
  video: true,
});
localVideo.srcObject = stream;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Navigator.audioSession")}}
- [Audio Session API](/en-US/docs/Web/API/Audio_Session_API)