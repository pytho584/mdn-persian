---
title: "HTMLMediaElement: seekable property"
short-title: seekable
slug: Web/API/HTMLMediaElement/seekable
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.seekable
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`seekable`** در اشیاء {{domxref("HTMLMediaElement")}}، یک [شیء `TimeRanges` نرمال‌شده](/en-US/docs/Web/API/TimeRanges#normalized_timeranges_objects) ایستای جدید برمی‌گرداند که بازه‌هایی از منبع رسانه را (در صورت وجود) نشان می‌دهد که عامل کاربر در زمان دسترسی به ویژگی `seekable` توانایی جست‌وجو در آن‌ها را دارد.

## مقدار

یک شیء [TimeRanges نرمال‌شده](/en-US/docs/Web/API/TimeRanges#normalized_timeranges_objects) ایستای جدید که بازه‌هایی از منبع رسانه را (در صورت وجود) نشان می‌دهد که عامل کاربر در زمان دسترسی به ویژگی `seekable` توانایی جست‌وجو در آن‌ها را دارد.

## مثال‌ها

```js
const video = document.querySelector("video");
const timeRangesObject = video.seekable;
const timeRanges = [];
// Go through the object and output an array
for (let count = 0; count < timeRangesObject.length; count++) {
  timeRanges.push([timeRangesObject.start(count), timeRangesObject.end(count)]);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: واسطی که برای تعریف ویژگی `HTMLMediaElement.seekable` استفاده می‌شود
- [Media Source API](/en-US/docs/Web/API/Media_Source_Extensions_API)
- [Media buffering, seeking, and time ranges](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/buffering_seeking_time_ranges)