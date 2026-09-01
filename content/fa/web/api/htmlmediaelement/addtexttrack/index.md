---
title: "HTMLMediaElement: addTextTrack() method"
short-title: addTextTrack()
slug: Web/API/HTMLMediaElement/addTextTrack
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.addTextTrack
---

{{APIRef("HTML DOM")}}

متد **`addTextTrack()`** از رابط {{domxref("HTMLMediaElement")}} یک شیء {{domxref("TextTrack")}} جدید ایجاد کرده و آن را به عنصر رسانه اضافه می‌کند. این متد یک رویداد {{domxref("TextTrackList/addtrack_event", "addtrack")}} در {{domxref("HTMLMediaElement/textTracks", "textTracks")}} این عنصر رسانه ایجاد می‌کند. این متد فقط روی یک {{domxref("HTMLMediaElement")}} قابل استفاده است و نه روی رابط {{domxref("TextTrackList")}}.

## نحو (Syntax)

```js-nolint
addTextTrack(kind)
addTextTrack(kind, label)
addTextTrack(kind, label, language)
```

### پارامترها

- `kind`
  - : یک رشته که نمایانگر خصوصیت {{domxref("TextTrack.kind")}} است (`subtitles`, `captions`, `descriptions`, `chapters` یا `metadata`).
- `label`
  - : یک رشته که نمایانگر خصوصیت {{domxref("TextTrack.label")}} است.
- `language`
  - : یک رشته که نمایانگر خصوصیت {{domxref("TextTrack.language")}} است.

### مقدار بازگشتی

شیء {{domxref("TextTrack")}} جدید ایجاد شده.

### استثناها (Exceptions)

هیچ‌کدام.

## مثال‌ها

این مثال یک {{domxref("TextTrack")}} جدید با `kind` تنظیم شده روی `"subtitles"` اضافه می‌کند و یک {{domxref("VTTCue")}} جدید به آن می‌افزاید.

```js
const video = document.querySelector("video");
const newTrack = video.addTextTrack("subtitles");
newTrack.addCue(new VTTCue(3, 6, "Hello world!"));
console.log(newTrack.cues[0].text);
// "Hello world!"
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگرها (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("TextTrack")}}
- [WebVTT API](/en-US/docs/Web/API/WebVTT_API)
- [فناوری‌های رسانه وب](/en-US/docs/Web/Media)
- آموزش: [محتوای ویدیویی و صوتی](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)