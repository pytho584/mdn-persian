---
title: "MediaStreamTrack: contentHint property"
short-title: contentHint
slug: Web/API/MediaStreamTrack/contentHint
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.contentHint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`contentHint`** در رابط {{domxref("MediaStreamTrack")}} یک رشته است که نوع محتوای موجود در track را مشخص می‌کند. مقادیر مجاز به مقدار ویژگی {{domxref("MediaStreamTrack.kind")}} بستگی دارند.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `""`
  - : هیچ `contentHint` تنظیم نشده است.
- `"speech"`
  - : این track باید به‌گونه‌ای پردازش شود که گویی حاوی داده‌های گفتاری است. هنگام تنظیم این مقدار، مقدار {{domxref("MediaStreamTrack.kind")}} باید `"audio"` باشد.
- `"speech-recognition"`
  - : این track باید به‌گونه‌ای پردازش شود که گویی حاوی داده‌هایی برای تشخیص گفتار توسط ماشین است. هنگام تنظیم این مقدار، مقدار {{domxref("MediaStreamTrack.kind")}} باید `"audio"` باشد.
- `"music"`
  - : این track باید به‌گونه‌ای پردازش شود که گویی حاوی موسیقی است. هنگام تنظیم این مقدار، مقدار {{domxref("MediaStreamTrack.kind")}} باید `"audio"` باشد.
- `"motion"`
  - : این track باید به‌گونه‌ای پردازش شود که گویی ویدئویی است که حرکت در آن اهمیت دارد. برای مثال، ویدئوی وب‌کم، فیلم‌ها یا بازی‌های ویدئویی. هنگام تنظیم این مقدار، مقدار {{domxref("MediaStreamTrack.kind")}} باید `"video"` باشد.
- `"detail"`
  - : این track باید به‌گونه‌ای پردازش شود که گویی جزئیات ویدئو اهمیت فوق‌العاده‌ای دارند. برای مثال، ارائه‌ها یا صفحات وب با محتوای متنی، نقاشی یا طراحی خطی. هنگام تنظیم این مقدار، مقدار {{domxref("MediaStreamTrack.kind")}} باید `"video"` باشد.
- `"text"`
  - : این track باید به‌گونه‌ای پردازش شود که گویی جزئیات ویدئو اهمیت فوق‌العاده‌ای دارند و لبه‌های تیز و نواحی با رنگ یکنواخت ممکن است به‌طور مکرر رخ دهند. برای مثال، ارائه‌ها یا صفحات وب با محتوای متنی. هنگام تنظیم این مقدار، مقدار {{domxref("MediaStreamTrack.kind")}} باید `"video"` باشد.

## مثال‌ها

### تابعی که contentHint را تنظیم می‌کند

این تابع یک stream و یک مقدار `contentHint` دریافت می‌کند و hint را روی هر track اعمال می‌کند. [مثال کامل را اینجا ببینید](https://webrtc.github.io/samples/src/content/capture/video-contenthint/) که نشان می‌دهد مقادیر مختلف `contentHint` چگونه نحوه نمایش trackها را تغییر می‌دهند.

```js
function setVideoTrackContentHints(stream, hint) {
  const tracks = stream.getVideoTracks();
  tracks.forEach((track) => {
    if ("contentHint" in track) {
      track.contentHint = hint;
      if (track.contentHint !== hint) {
        console.error(`Invalid video track contentHint: "${hint}"`);
      }
    } else {
      console.error("MediaStreamTrack contentHint attribute not supported");
    }
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
