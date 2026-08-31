---
title: "AudioTrackList: length property"
short-title: length
slug: Web/API/AudioTrackList/length
page-type: web-api-instance-property
browser-compat: api.AudioTrackList.length
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrackList/length"
translated_by: "n8n + AI"
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **{{domxref("AudioTrackList")}}** به نام **`length`** تعداد ورودی‌های موجود در `AudioTrackList` را برمی‌گرداند که هر کدام یک {{domxref("AudioTrack")}} است و نمایانگر یک آهنگ صوتی در عنصر رسانه‌ای است. مقدار ۰ نشان می‌دهد که هیچ آهنگ صوتی در رسانه وجود ندارد.

## مقدار

عددی که نشان می‌دهد چند آهنگ صوتی در `AudioTrackList` گنجانده شده است. هر آهنگ را می‌توان با در نظر گرفتن `AudioTrackList` به‌عنوان یک آرایه از اشیاء از نوع {{domxref("AudioTrack")}} دسترسی پیدا کرد.

## مثال‌ها

این قطعه کد تعداد آهنگ‌های صوتی اولین عنصر {{HTMLElement("video")}} یافت‌شده در {{Glossary("DOM")}} را توسط {{domxref("Document.querySelector", "querySelector()")}} دریافت می‌کند.

```js
const videoElem = document.querySelector("video");
let numAudioTracks = 0;

if (videoElem.audioTracks) {
  numAudioTracks = videoElem.audioTracks.length;
}
```

توجه داشته باشید که این نمونه مطمئن می‌شود که {{domxref("HTMLMediaElement.audioTracks")}} تعریف شده است تا در مرورگرهایی که از {{domxref("AudioTrack")}} پشتیبانی نمی‌کنند، خطایی رخ ندهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}