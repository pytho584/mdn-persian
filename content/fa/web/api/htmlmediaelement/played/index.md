---
title: "HTMLMediaElement: played property"
short-title: played
slug: Web/API/HTMLMediaElement/played
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.played
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`played`** در رابط {{domxref("HTMLMediaElement")}} بازه‌های زمانی‌ای را نشان می‌دهد که منبع رسانه‌ای (یک فایل رسانه‌ای {{htmlelement("audio")}} یا {{htmlelement("video")}}) پخش شده است. این ویژگی یک شیء جدید {{domxref("TimeRanges")}} برمی‌گرداند که شامل بازه‌هایی از منبع رسانه است که مرورگر در لحظه ارزیابی این ویژگی پخش کرده است، در صورت وجود.

## مقدار

یک شیء {{domxref("TimeRanges")}} که بازه‌های زمانی پخش‌شده را نشان می‌دهد.

## نمونه‌ها

```js
const media = document.querySelector("audio");
const playedTimeRanges = media.played;
let timePlayed = 0;
// محاسبه کل مدت زمانی که رسانه پخش شده است
for (let i = 0; i < playedTimeRanges.length; i++) {
  timePlayed += playedTimeRanges.end(i) - playedTimeRanges.start(i);
}
console.log(`The media played for a total of ${timePlayed} seconds.`);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("HTMLMediaElement.seeked_event", "seeked")}}
- رویداد {{domxref("HTMLMediaElement.progress_event", "progress")}}
- {{domxref("HTMLMediaElement.seekable")}}
- {{domxref("HTMLMediaElement.buffered")}}
- {{domxref("HTMLVideoElement")}}
- {{domxref("HTMLAudioElement")}}