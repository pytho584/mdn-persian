---
title: "DataCue: DataCue() constructor"
short-title: DataCue()
slug: Web/API/DataCue/DataCue
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.DataCue.DataCue
---

{{APIRef("WebVTT")}}{{SeeCompatTable}}

سازندهٔ **`DataCue()`** یک شیء {{domxref("DataCue")}} جدید می‌سازد و برمی‌گرداند که نشان‌دهندهٔ یک نشانه (cue) فراداده‌ای زمان‌بندی‌شده در یک بازهٔ زمانی معین است. نشانهٔ حاصل را می‌توان با استفاده از {{domxref("TextTrack.addCue()")}} به یک {{domxref("TextTrack")}} فراداده‌ای اضافه کرد و بدین ترتیب داده‌های دلخواه را با پخش صدا یا ویدیو همگام‌سازی نمود.

## Syntax

```js-nolint
new DataCue(startTime, endTime, value)
new DataCue(startTime, endTime, value, type)
```

### پارامترها

- `startTime`
  - : عددی که زمان شروع، بر حسب ثانیه، برای بازهٔ زمانی نشانه را مشخص می‌کند. این مقدار با نقطه‌ای از خط زمانی رسانه مطابقت دارد که نشانه در آن فعال می‌شود و رویداد {{domxref("TextTrackCue/enter_event", "enter")}} آن رخ می‌دهد.
- `endTime`
  - : عددی که زمان پایان، بر حسب ثانیه، برای بازهٔ زمانی نشانه را مشخص می‌کند. وقتی پخش رسانه به این زمان برسد، رویداد {{domxref("TextTrackCue/exit_event", "exit")}} نشانه رخ می‌دهد. برای نشانه‌ای که تا پایان رسانه فعال می‌ماند، از `Infinity` استفاده کنید.
- `value`
  - : بار داده‌ای (payload) مرتبط با نشانه. این مقدار می‌تواند از هر نوعی باشد؛ مانند یک رشته، یک شیء جاوااسکریپت یا یک {{jsxref("ArrayBuffer")}}. این مقدار در ویژگی {{domxref("DataCue.value", "value")}} نشانه ذخیره می‌شود.
- `type` {{optional_inline}}
  - : رشته‌ای که نوع یا طرحوارهٔ داده‌های موجود در `value` را مشخص می‌کند. این رشته معمولاً با نماد دامنهٔ معکوس نوشته می‌شود (مثلاً `"org.id3"` یا `"org.mp4ra"`). این مقدار در ویژگی {{domxref("DataCue.type", "type")}} نشانه ذخیره می‌شود و اگر ارائه نشود، به‌صورت پیش‌فرض یک رشتهٔ خالی خواهد بود.

### مقدار بازگشتی

یک شیء جدید {{domxref("DataCue")}}.

## مثال‌ها

### ساخت DataCue با داده‌های موقعیت جغرافیایی

این مثال یک `DataCue` می‌سازد که مختصات موقعیت جغرافیایی را حمل می‌کند و از یک رشتهٔ دامنهٔ معکوس به‌عنوان `type` برای شناسایی قالب داده استفاده می‌کند.

```html
<video controls src="video.mp4"></video>
```

```js
const video = document.querySelector("video");
const track = video.addTextTrack("metadata", "Geo Track");
track.mode = "hidden";

// ساخت یک نشانه از ثانیهٔ ۵ تا پایان رسانه
const data = { latitude: 51.5043, longitude: -0.0762 };
const cue = new DataCue(5.0, Infinity, data, "org.example.geo");

cue.addEventListener("enter", (e) => {
  const { latitude, longitude } = e.target.value;
  console.log(`Pan map to: ${latitude}, ${longitude}`);
});

track.addCue(cue);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("DataCue")}}
- {{domxref("TextTrack")}}
- {{domxref("TextTrack.addCue()")}}
- رویداد {{domxref("TextTrackCue/enter_event", "enter")}}
- رویداد {{domxref("TextTrackCue/exit_event", "exit")}}