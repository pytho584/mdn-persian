---
title: "HTMLMediaElement: audioTracks property"
---

---
title: "HTMLMediaElement: audioTracks property"
short-title: audioTracks
slug: Web/API/HTMLMediaElement/audioTracks
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.audioTracks
---

{{APIRef("HTML DOM")}}

ویژگی فقط خواندنی **`audioTracks`** در اشیاء {{domxref("HTMLMediaElement")}} یک شیء {{domxref("AudioTrackList")}} را برمی‌گرداند که تمام اشیاء {{domxref("AudioTrack")}} نمایانگر آهنگ‌های صوتی عنصر رسانه را فهرست می‌کند.

عنصر رسانه می‌تواند یک عنصر {{HTMLElement("audio")}} یا یک عنصر {{HTMLElement("video")}} باشد.

لیست بازگشتی _زنده_ است؛ یعنی با افزوده شدن یا حذف شدن آهنگ‌ها به عنصر رسانه، محتویات لیست به صورت پویا تغییر می‌کند. هنگامی که یک مرجع به لیست دارید، می‌توانید آن را برای تغییرات زیر نظر بگیرید تا زمانی که آهنگ‌های صوتی جدید اضافه می‌شوند یا آهنگ‌های موجود حذف می‌شوند، تشخیص دهید. برای آشنایی بیشتر با نظارت بر تغییرات لیست آهنگ یک عنصر رسانه، به [رویدادهای AudioTrackList](/en-US/docs/Web/API/AudioTrackList#events) مراجعه کنید.

## مقدار

یک شیء {{domxref("AudioTrackList")}} که نمایانگر لیست آهنگ‌های صوتی موجود در عنصر رسانه است. می‌توان به لیست آهنگ‌ها با استفاده از نماد آرایه‌ای یا با استفاده از روش {{domxref("AudioTrackList.getTrackById", "getTrackById()")}} شیء دسترسی پیدا کرد.

هر آهنگ توسط یک شیء {{domxref("AudioTrack")}} نمایش داده می‌شود که اطلاعاتی درباره آهنگ ارائه می‌دهد.

## مثال‌ها

در این مثال، تمام آهنگ‌های صوتی روی یک عنصر مشخص خاموش می‌شوند.

### HTML

HTML خود عنصر را ایجاد می‌کند.

```html
<video id="video" src="somevideo.mp4"></video>
```

### JavaScript

کد JavaScript خاموش کردن آهنگ‌های صوتی عنصر ویدیو را انجام می‌دهد.

```js
const video = document.getElementById("video");

for (const track of video.audioTracks) {
  track.enabled = false;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف ویژگی `HTMLMediaElement.audioTracks` استفاده می‌شود.
- {{HTMLElement("audio")}}, {{HTMLElement("video")}}
- {{domxref("AudioTrack")}}, {{domxref("AudioTrackList")}}