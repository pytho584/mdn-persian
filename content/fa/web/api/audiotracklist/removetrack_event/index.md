---
title: "AudioTrackList: removetrack event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrackList/removetrack_event"
translated_by: "n8n + AI"
---

---
title: "AudioTrackList: removetrack event"
short-title: removetrack
slug: Web/API/AudioTrackList/removetrack_event
page-type: web-api-event
browser-compat: api.AudioTrackList.removetrack_event
---

{{APIRef("HTML DOM")}}

رویداد `removetrack` زمانی رخ می‌دهد که یک تراک از یک [`AudioTrackList`](/en-US/docs/Web/API/AudioTrackList) حذف شود.

## سینتکس

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک خاصیت مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("removetrack", (event) => { })

onremovetrack = (event) => { }
```

## نوع رویداد

یک {{domxref("TrackEvent")}}. از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("TrackEvent")}}

## توضیحات

### محرک

رویداد `removetrack` هر زمان که یک تراک از عنصر رسانه‌ای که تراک‌های صوتی آن توسط شیء `AudioTrackList` نمایش داده می‌شوند حذف شود، فراخوانی می‌شود.

این رویداد قابل لغو نیست و حباب نمی‌زند.

### موارد استفاده

می‌توانید از این رویداد برای واکنش به در دسترس نبودن یک تراک صوتی جدید استفاده کنید. به عنوان مثال، ممکن است بخواهید عناصر رابط کاربری خود را به‌روزرسانی کنید تا انتخاب تراک صوتی حذف‌شده توسط کاربر غیرمجاز شود.

## مثال‌ها

با استفاده از `addEventListener()`:

```js
const videoElement = document.querySelector("video");

videoElement.audioTracks.addEventListener("removetrack", (event) => {
  console.log(`Audio track: ${event.track.label} removed`);
});
```

با استفاده از خاصیت مدیریت رویداد `onremovetrack`:

```js
const videoElement = document.querySelector("video");

videoElement.audioTracks.onremovetrack = (event) => {
  console.log(`Audio track: ${event.track.label} removed`);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رویدادهای مرتبط: [`addtrack`](/en-US/docs/Web/API/AudioTrackList/addtrack_event)، [`change`](/en-US/docs/Web/API/AudioTrackList/change_event)
- رویداد معادل در [`VideoTrackList`](/en-US/docs/Web/API/VideoTrackList): [`removetrack`](/en-US/docs/Web/API/VideoTrackList/removetrack_event)
- رویداد معادل در [`MediaStream`](/en-US/docs/Web/API/MediaStream): [`removetrack`](/en-US/docs/Web/API/MediaStream/removetrack_event)
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [WebRTC](/en-US/docs/Web/API/WebRTC_API)