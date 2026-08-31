---
title: "AudioTrack"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrack"
translated_by: "n8n + AI"
---

---
title: AudioTrack
slug: Web/API/AudioTrack
page-type: web-api-interface
browser-compat: api.AudioTrack
---

{{APIRef("HTML DOM")}}

رابط **`AudioTrack`** یک مسیر صوتی واحد از یکی از عناصر رسانه‌ای HTML، یعنی {{HTMLElement("audio")}} یا {{HTMLElement("video")}} را نمایش می‌دهد.

رایج‌ترین کاربرد دسترسی به یک شیء `AudioTrack`، تغییر وضعیت ویژگی {{domxref("AudioTrack.enabled", "enabled")}} آن برای بی‌صدا کردن و بازگرداندن صدای مسیر است.

## ویژگی‌های نمونه

- {{domxref("AudioTrack.enabled", "enabled")}}
  - : یک مقدار بولی که کنترل می‌کند آیا صدای مسیر صوتی فعال است یا خیر. تنظیم این مقدار روی `false` صدای مسیر را بی‌صدا می‌کند.
- {{domxref("AudioTrack.id", "id")}} {{ReadOnlyInline}}
  - : یک رشته که مسیر را به‌طور یکتا درون رسانه شناسایی می‌کند. می‌توان از این شناسه برای یافتن یک مسیر خاص در فهرست مسیرهای صوتی با فراخوانی {{domxref("AudioTrackList.getTrackById()")}} استفاده کرد. همچنین اگر رسانه از جست‌وجو بر اساس قطعه رسانه مطابق [Media Fragments URI specification](https://www.w3.org/TR/media-frags/) پشتیبانی کند، می‌توان از این شناسه به‌عنوان بخش قطعه از URL استفاده کرد.
- {{domxref("AudioTrack.kind", "kind")}} {{ReadOnlyInline}}
  - : یک رشته که دسته‌ای را مشخص می‌کند که مسیر در آن قرار می‌گیرد. برای مثال، مسیر صوتی اصلی دارای `kind` با مقدار `"main"` خواهد بود.
- {{domxref("AudioTrack.label", "label")}} {{ReadOnlyInline}}
  - : یک رشته که برچسبی قابل‌خواندن برای انسان برای مسیر فراهم می‌کند. برای مثال، یک مسیر توضیحات صوتی برای یک فیلم ممکن است `label` با مقدار `"Commentary with director Christopher Nolan and actors Leonardo DiCaprio and Elliot Page."` داشته باشد. اگر برچسبی ارائه نشده باشد، این رشته خالی است.
- {{domxref("AudioTrack.language", "language")}} {{ReadOnlyInline}}
  - : یک رشته که زبان اصلی مسیر صوتی را مشخص می‌کند، یا اگر ناشناخته باشد یک رشته خالی است. زبان به‌صورت یک {{glossary("BCP 47 language tag")}} مانند `"en-US"` یا `"pt-BR"` مشخص می‌شود.
- {{domxref("AudioTrack.sourceBuffer", "sourceBuffer")}} {{ReadOnlyInline}}
  - : {{domxref("SourceBuffer")}} که مسیر را ایجاد کرده است. اگر مسیر توسط یک {{domxref("SourceBuffer")}} ایجاد نشده باشد یا {{domxref("SourceBuffer")}} از ویژگی {{domxref("MediaSource.sourceBuffers")}} منبع رسانه والد خود حذف شده باشد، `null` برمی‌گرداند.

## نکات استفاده

برای دریافت یک `AudioTrack` برای یک عنصر رسانه‌ای مشخص، از ویژگی {{domxref("HTMLMediaElement.audioTracks", "audioTracks")}} عنصر استفاده کنید که یک شیء {{domxref("AudioTrackList")}} برمی‌گرداند و می‌توانید از آن مسیرهای فردی موجود در رسانه را دریافت کنید:

```js
const el = document.querySelector("video");
const tracks = el.audioTracks;
```

سپس می‌توانید با استفاده از نحو آرایه یا توابعی مانند {{jsxref("Array.forEach", "forEach()")}} به مسیرهای فردی رسانه دسترسی پیدا کنید.

این مثال اول، اولین مسیر صوتی رسانه را دریافت می‌کند:

```js
const firstTrack = tracks[0];
```

مثال بعدی تمام مسیرهای صوتی رسانه را اسکن می‌کند و هر کدام را که به زبان ترجیحی کاربر هستند (که از متغیر `userLanguage` گرفته شده است) فعال می‌کند و بقیه را غیرفعال می‌کند.

```js
tracks.forEach((track) => {
  track.enabled = track.language === userLanguage;
});
```

{{domxref("AudioTrack.language", "language")}} به‌صورت یک {{glossary("BCP 47 language tag")}} معتبر مشخص می‌شود، برای مثال `"en-US"` برای انگلیسی آمریکایی.

## مثال

برای نمونه‌ای که نحوه دریافت آرایه‌ای از انواع و برچسب‌های مسیر برای یک عنصر رسانه‌ای مشخص، فیلترشده بر اساس نوع را نشان می‌دهد، به [`AudioTrack.label`](/en-US/docs/Web/API/AudioTrack/label#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}