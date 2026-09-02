---
title: "MediaStreamTrackEvent: MediaStreamTrackEvent() constructor"
short-title: MediaStreamTrackEvent()
slug: Web/API/MediaStreamTrackEvent/MediaStreamTrackEvent
page-type: web-api-constructor
browser-compat: api.MediaStreamTrackEvent.MediaStreamTrackEvent
---

{{APIRef("Media Capture and Streams")}}

سازندهی **`MediaStreamTrackEvent()`** یک شیء جدید {{domxref("MediaStreamTrackEvent")}} برمی‌گرداند که نمایانگر رویدادی است که در آن یک {{domxref("MediaStreamTrack")}} به یک {{domxref("MediaStream")}} اضافه یا از آن حذف شده است.

## سینتکس

```js-nolint
new MediaStreamTrackEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای که نام رویداد را مشخص می‌کند. این مقدار به بزرگی و کوچکی حروف حساس است و مرورگرها آن را روی `addtrack` یا `removetrack` تنظیم می‌کنند.
- `options`
  - : یک شیء که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `track`
      - : یک شیء {{domxref("MediaStreamTrack")}} که نمایانگر ترک اضافه‌شده به جریان یا حذف‌شده از جریان است.

### مقدار بازگشتی

یک شیء جدید {{domxref("MediaStreamTrackEvent")}} که بر اساس گزینه‌های ارائه‌شده ساخته شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای {{domxref("MediaStream/addtrack_event", "addtrack")}} و {{domxref("MediaStream/removetrack_event", "removetrack")}}
- {{domxref("MediaStreamTrack")}}
- {{domxref("MediaStream")}}
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)