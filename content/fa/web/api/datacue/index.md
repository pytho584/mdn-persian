---
title: DataCue
slug: Web/API/DataCue
page-type: web-api-interface
status:
  - experimental
browser-compat: api.DataCue
---

{{APIRef("WebVTT")}}{{SeeCompatTable}}

رابط **`DataCue`** نماینگر یک نشانه (cue) است که داده‌های زمان‌بندی‌شدهٔ دلخواه را با یک منبع رسانه‌ای صوتی یا تصویری مرتبط می‌سازد، یا داده‌های زمان‌بندی‌شده را از یک منبع رسانه‌ای در اختیار صفحات وب قرار می‌دهد. این رابط، رابط {{domxref("TextTrackCue")}} را با یک ویژگی {{domxref("DataCue.value", "value")}} که می‌تواند هر نوع داده‌ای را در خود نگه دارد، و یک ویژگی {{domxref("DataCue.type", "type")}} که نوع داده را مشخص می‌کند، گسترش می‌دهد.

بر خلاف {{domxref("VTTCue")}} که برای نمایش متن زیرنویس و عنوان‌ها طراحی شده است، `DataCue` برای فراداده‌های زمان‌بندی‌شدهٔ غیرقابل نمایش در نظر گرفته شده است. موارد استفاده شامل جایگزینی پویای محتوا، درج تبلیغ، ارائهٔ محتوای تکمیلی در کنار صدا یا تصویر، یا به طور کلی، راه‌اندازی منطق برنامه در نقاط مشخصی از خط زمانی رسانه است.

برخی از عامل‌های کاربری ممکن است به طور خودکار اشیاء `DataCue` را برای فراداده‌های زمان‌بندی‌شدهٔ درون‌باند که در جریان‌های رسانه‌ای حمل می‌شوند، مانند برچسب‌های ID3 در [پخش زنده HTTP (HLS)](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/Setting_up_adaptive_streaming_media_sources#hls_encoding)، تولید کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("DataCue.DataCue", "DataCue()")}} {{experimental_inline}}
  - : یک شیء `DataCue` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("TextTrackCue")}} به ارث می‌برد._

- {{domxref("DataCue.type")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک رشته که نوع {{domxref("DataCue.value", "value")}} نشانه را مشخص می‌کند، معمولاً با استفاده از نماد دامنه معکوس (reverse-domain notation) (مثلاً `"org.mp4ra"`، `"org.id3"`).
- {{domxref("DataCue.value")}} {{experimental_inline}}
  - : بار داده‌ای (payload) مرتبط با نشانه. می‌تواند هر نوعی باشد.

## روش‌های نمونه

_این رابط هیچ متد خاص خود را ندارد اما متدهایی را از {{domxref("TextTrackCue")}} به ارث می‌برد._

## مثال‌ها

### ارتباط دادن فراداده‌های زمان‌بندی‌شده با یک ویدئو

مثال زیر یک {{domxref("TextTrack")}} فراداده‌ای روی یک عنصر ویدئو ایجاد می‌کند و اشیاء `DataCue` حاوی مختصات جغرافیایی را به آن اضافه می‌کند. هنگامی که هر نشانه در حین پخش فعال می‌شود، رویداد {{domxref("TextTrackCue/enter_event", "enter")}} آن فعال می‌شود و به صفحه اجازه می‌دهد واکنش نشان دهد — برای مثال، با به‌روزرسانی نمای نقشه.

```html
<video controls src="video.mp4"></video>
```

```js
const video = document.querySelector("video");
const track = video.addTextTrack("metadata", "Geo Track");
track.mode = "hidden";

const points = [
  { start: 0, end: 10, data: { latitude: 51.5043, longitude: -0.0762 } },
  { start: 10, end: 20, data: { latitude: 48.8566, longitude: 2.3522 } },
  { start: 20, end: 30, data: { latitude: 40.4168, longitude: -3.7038 } },
];

for (const point of points) {
  const cue = new DataCue(
    point.start,
    point.end,
    point.data,
    "org.example.geo",
  );
  cue.addEventListener("enter", (e) => {
    const { latitude, longitude } = e.target.value;
    console.log(`Map pan to: ${latitude}, ${longitude}`);
  });
  track.addCue(cue);
}

// At 0s: "Map pan to: 51.5043, -0.0762"
// At 10s: "Map pan to: 48.8566, 2.3522"
// At 20s: "Map pan to: 40.4168, -3.7038"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("TextTrackCue")}}
- {{domxref("VTTCue")}}
- {{domxref("TextTrack")}}
- رویداد {{domxref("TextTrackCue/enter_event", "enter")}}
- رویداد {{domxref("TextTrackCue/exit_event", "exit")}}