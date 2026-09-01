---
title: "HTMLMediaElement: textTracks property"
short-title: textTracks
slug: Web/API/HTMLMediaElement/textTracks
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.textTracks
---

{{APIRef("HTML DOM")}}

خاصیت فقط-خواندنی **`textTracks`** در اشیاء {{DOMxRef("HTMLMediaElement")}} یک شئ {{DOMxRef("TextTrackList")}} را برمی‌گرداند که تمام اشیاء {{DOMxRef("TextTrack")}} مربوط به رَک‌های متنی عنصر رسانه را به همان ترتیبی که در لیست رَک‌های متنی هستند، فهرست می‌کند.

می‌توانید با استفاده از رویدادهای `addtrack` و `removetrack` تشخیص دهید که چه زمانی رَک‌هایی به یک عنصر [`<audio>`](/en-US/docs/Web/HTML/Reference/Elements/audio) یا [`<video>`](/en-US/docs/Web/HTML/Reference/Elements/video) اضافه یا از آن حذف می‌شوند. با این حال، این رویدادها مستقیماً به خود عنصر رسانه ارسال نمی‌شوند. در عوض، آنها به شئ لیست رَک‌های [`HTMLMediaElement`](/en-US/docs/Web/API/HTMLMediaElement) که مربوط به نوع رَک اضافه‌شده به عنصر است، ارسال می‌شوند.

لیست برگشتی _زنده_ است؛ یعنی با اضافه و حذف شدن رَک‌ها به عنصر رسانه، محتویات لیست به صورت پویا تغییر می‌کند. هنگامی که یک مرجع به لیست دارید، می‌توانید آن را برای تغییرات زیر نظر بگیرید تا زمانی که رَک‌های متنی جدید اضافه می‌شوند یا رَک‌های موجود حذف می‌شوند، تشخیص دهید.

برای آشنایی بیشتر با نحوه نظارت بر تغییرات لیست رَک‌های یک عنصر رسانه، به [رویدادهای TextTrackList](/en-US/docs/Web/API/TextTrackList#events) مراجعه کنید.

## مقدار

یک شئ {{DOMxRef("TextTrackList")}} که لیست رَک‌های متنی موجود در عنصر رسانه را نشان می‌دهد. می‌توان از طریق `textTracks[n]` به n-امین رَک متنی از لیست رَک‌های شئ دسترسی داشت، یا با استفاده از متد [`textTracks.getTrackById()`](/en-US/docs/Web/API/TextTrackList/getTrackById).

هر رَک توسط یک شئ {{DOMxRef("TextTrack")}} نمایش داده می‌شود که اطلاعاتی درباره آن رَک ارائه می‌دهد.

## مثال‌ها

ما با یک [`<video>`](/en-US/docs/Web/HTML/Reference/Elements/video) که چند فرزند [`<track>`](/en-US/docs/Web/HTML/Reference/Elements/track) دارد شروع می‌کنیم.

```html
<video controls>
  <source src="/shared-assets/videos/sintel-short.webm" type="video/webm" />
  <source src="/shared-assets/videos/sintel-short.mp4" type="video/mp4" />
  <track
    kind="subtitles"
    src="/shared-assets/misc/sintel-en.vtt"
    srclang="en"
    label="English" />
  <track
    kind="subtitles"
    src="/shared-assets/misc/sintel-de.vtt"
    srclang="de"
    label="Deutsch" />
  <track
    kind="subtitles"
    src="/shared-assets/misc/sintel-es.vtt"
    srclang="es"
    label="Español" />
</video>
```

`HTMLMediaElement.textTracks` یک `TextTrackList` برمی‌گرداند که می‌توانیم در آن پیمایش کنیم. در اینجا هر سه رَک را به طور همزمان نمایش می‌دهیم.

```js
const tracks = document.querySelector("video").textTracks;

for (const track of tracks) {
  track.mode = "showing";
}
```

{{EmbedLiveSample("Examples", "100%", 350)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: واسطی که برای تعریف خاصیت `HTMLMediaElement.textTracks` استفاده شده است
- {{HTMLElement("audio")}}, {{HTMLElement("video")}}
- {{DOMxRef("AudioTrack")}}, {{DOMxRef("AudioTrackList")}}
- {{DOMxRef("VideoTrack")}}, {{DOMxRef("VideoTrackList")}}
- [`addtrack`](/en-US/docs/Web/API/VideoTrackList/addtrack_event),
  [`change`](/en-US/docs/Web/API/VideoTrackList/change_event),
  [`removetrack`](/en-US/docs/Web/API/VideoTrackList/removetrack_event): رویدادهای AudioTrackList
- [`addtrack`](/en-US/docs/Web/API/VideoTrackList/addtrack_event),
  [`change`](/en-US/docs/Web/API/VideoTrackList/change_event),
  [`removetrack`](/en-US/docs/Web/API/VideoTrackList/removetrack_event): رویدادهای VideoTrackList