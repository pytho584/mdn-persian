---
title: "DataCue: value property"
short-title: value
slug: Web/API/DataCue/value
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.DataCue.value
---

{{APIRef("WebVTT")}}{{SeeCompatTable}}

ویژگی **`value`** از رابط {{domxref("DataCue")}} دادهٔ اصلی (payload) این نشانه (cue) را نشان می‌دهد. برخلاف {{domxref("VTTCue")}} که محتوای متنی را حمل می‌کند، `DataCue` می‌تواند هر نوع داده‌ای را نگه دارد — مانند یک شیء جاوااسکریپتی، یک رشته یا یک {{jsxref("ArrayBuffer")}} — و این آن را برای موارد استفادهٔ فرادادهٔ زمان‌بندی‌شده (timed metadata) مناسب می‌سازد، جایی که داده‌های ساختار یافته باید با پخش رسانه همگام‌سازی شوند.

این ویژگی برای نشانه‌هایی که توسط برنامه ساخته می‌شوند خواندنی-نوشتنی است و امکان به‌روزرسانی داده‌ها را پس از ساخت فراهم می‌کند. برای نشانه‌هایی که به‌طور خودکار توسط عامل کاربر (user agent) از فرادادهٔ زمان‌بندی‌شدهٔ درون‌باند (مثل برچسب‌های ID3 در منبع HTTP Live Streaming) تولید می‌شوند، مقدار توسط عامل کاربر تنظیم می‌شود و محتوای فراداده را بازتاب می‌دهد.

ویژگی {{domxref("DataCue.type", "type")}} می‌تواند در کنار `value` برای شناسایی قالب یا طرح‌واره (schema) داده استفاده شود.

## مقدار

هر نوعی. مقدار معمولاً یک رشته، یک شیء ساده یا یک {{jsxref("ArrayBuffer")}} است، بسته به منبع نشانه و نوع فرادادهٔ زمان‌بندی‌شده‌ای که آن را نمایش می‌دهد.

## مثال‌ها

### خواندن مقدار ویژگی value در یک DataCue

```html
<video controls src="video.mp4"></video>
```

```js
const video = document.querySelector("video");
const track = video.addTextTrack("metadata", "Geo Track");
track.mode = "hidden";

const cue = new DataCue(
  0,
  10,
  { latitude: 51.5043, longitude: -0.0762 },
  "org.example.geo",
);
track.addCue(cue);

console.log(cue.value);
// { latitude: 51.5043, longitude: -0.0762 }
```

### واکنش به داده‌های نشانه هنگام پخش

این مثال چند شیء `DataCue` را به یک تراک فراداده (metadata track) اضافه می‌کند و سپس مقدار `value` هر نشانه را زمانی که در حین پخش فعال می‌شود می‌خواند.

```html
<video controls src="video.mp4"></video>
```

```js
const video = document.querySelector("video");
const track = video.addTextTrack("metadata", "Events");
track.mode = "hidden";

const cue1 = new DataCue(5, 10, { action: "showBanner", text: "Welcome!" });
const cue2 = new DataCue(15, 20, { action: "highlight", playerId: 7 });

cue1.addEventListener("enter", (e) => {
  console.log(e.target.value.action);
  // "showBanner"
});

cue2.addEventListener("enter", (e) => {
  console.log(e.target.value.action);
  // "highlight"
});

track.addCue(cue1);
track.addCue(cue2);
```

### به‌روزرسانی مقدار یک DataCue

ویژگی `value` قابل نوشتن است، بنابراین می‌توان آن را پس از ایجاد نشانه تغییر داد.

```js
const cue = new DataCue(0, 5, "initial data");
cue.value = { updated: true, score: 42 };
console.log(cue.value);
// { updated: true, score: 42 }
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DataCue")}}
- {{domxref("DataCue.type")}}
- {{domxref("DataCue.DataCue", "DataCue()")}} constructor
- {{domxref("TextTrackCue")}}