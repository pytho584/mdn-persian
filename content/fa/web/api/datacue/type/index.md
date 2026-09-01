```markdown
---
title: "DataCue: type property"
short-title: type
slug: Web/API/DataCue/type
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.DataCue.type
---

{{APIRef("WebVTT")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`type`** در رابط {{domxref("DataCue")}} رشته‌ای را برمی‌گرداند که نوع یا ساختار داده‌های ذخیره‌شده در ویژگی {{domxref("DataCue.value", "value")}} نشانه را مشخص می‌کند. این مقدار معمولاً رشته‌ای با نماد دامنهٔ معکوس است (مانند `"org.id3"`، `"com.apple.itunes"`) که به برنامه‌ها امکان می‌دهد بار دادهٔ نشانه را به درستی تفسیر کنند.

وقتی عامل کاربر به‌صورت خودکار برای ابردادهٔ زمان‌دار درون‌باند (in-band) شیءهای `DataCue` می‌سازد (مثلاً از یک منبع HTTP Live Streaming)، این ویژگی را برای نشان دادن قالب ابرداده تنظیم می‌کند. وقتی کد برنامه با استفاده از سازندهٔ {{domxref("DataCue.DataCue", "DataCue()")}} یک `DataCue` ایجاد می‌کند، `type` از آرگومان اختیاری چهارم گرفته می‌شود و در صورت حذف شدن، به رشتهٔ خالی پیش‌فرض تنظیم می‌گردد.

## مقدار

یک رشته. مقادیر رایجی که عامل‌های کاربر برای ابردادهٔ درون‌باند تنظیم می‌کنند عبارت‌اند از:

- `"org.id3"` — ابردادهٔ ID3.
- `"org.mp4ra"` — ابردادهٔ MPEG-4.
- `"com.apple.quicktime.udta"` — دادهٔ کاربر QuickTime.
- `"com.apple.quicktime.mdta"` — ابردادهٔ QuickTime.
- `"com.apple.itunes"` — ابردادهٔ iTunes.

نشانه‌های تعریف‌شده توسط برنامه می‌توانند از هر رشته‌ای استفاده کنند، اما برای جلوگیری از تداخل، نماد دامنهٔ معکوس توصیه می‌شود.

## مثال‌ها

### خواندن type یک DataCue

```html
<video controls src="video.mp4"></video>
```

```js
const video = document.querySelector("video");
const track = video.addTextTrack("metadata", "Events");
track.mode = "hidden";

const cue = new DataCue(
  0,
  10,
  { latitude: 51.5043, longitude: -0.0762 },
  "org.example.geo",
);
track.addCue(cue);

console.log(cue.type);
// "org.example.geo"
```

### توزیع بر اساس type برای ابردادهٔ درون‌باند

وقتی عامل کاربر شیءهای `DataCue` را از ابردادهٔ زمان‌دار درون‌باند می‌سازد، می‌توان از ویژگی `type` برای تعیین نحوهٔ مدیریت هر نشانه استفاده کرد.

```js
track.addEventListener("cuechange", () => {
  for (const cue of track.activeCues) {
    switch (cue.type) {
      case "org.id3":
        handleID3Metadata(cue.value);
        break;
      case "org.mp4ra":
        handleMP4Metadata(cue.value);
        break;
      default:
        console.log(`Unknown cue type: ${cue.type}`);
    }
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DataCue")}}
- {{domxref("DataCue.value")}}
- سازندهٔ {{domxref("DataCue.DataCue", "DataCue()")}}
- {{domxref("TextTrackCue")}}
```