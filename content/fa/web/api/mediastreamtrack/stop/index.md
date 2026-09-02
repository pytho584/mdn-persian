---
title: "MediaStreamTrack: stop() method"
short-title: stop()
slug: Web/API/MediaStreamTrack/stop
page-type: web-api-instance-method
browser-compat: api.MediaStreamTrack.stop
---

{{APIRef("Media Capture and Streams")}}

متد **`stop()`** در رابط {{domxref("MediaStreamTrack")}}، track مربوطه را متوقف می‌کند.

## نحو

```js-nolint
stop()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## توضیحات

فراخوانی `stop()` به {{glossary("user agent")}} اعلام می‌کند که دیگر منبعِ این track — هر منبعی که باشد، از جمله فایل‌ها، جریان‌های شبکه یا دوربین/میکروفون محلی — توسط این {{domxref("MediaStreamTrack")}} مورد نیاز نیست. ازآنجاکه ممکن است چند track از منبع یکسانی استفاده کنند (مثلاً وقتی دو تب از میکروفون دستگاه استفاده می‌کنند)، منبع لزوماً بلافاصله متوقف نمی‌شود. در عوض، منبع از track جدا می‌شود و شیء track متوقف می‌گردد. تنها زمانی که هیچ track رسانه‌ای از آن منبع استفاده نکند، منبع می‌تواند واقعاً به‌طور کامل متوقف شود.

بلافاصله پس از فراخوانی `stop()`، خاصیت {{domxref("MediaStreamTrack.readyState", "readyState")}} روی `ended` تنظیم می‌شود. توجه داشته باشید که رویداد [`ended`](/en-US/docs/Web/API/MediaStreamTrack/ended_event) در این وضعیت صادر نخواهد شد.

## مثال‌ها

### توقف یک جریان ویدیویی

در این مثال، تابعی را می‌بینیم که با فراخوانی `stop()` روی هر track متعلق به یک {{HTMLElement("video")}} مشخص، پخش ویدیوی جریانیافته را متوقف می‌کند.

```js
function stopStreamedVideo(videoElem) {
  const stream = videoElem.srcObject;
  const tracks = stream.getTracks();

  tracks.forEach((track) => {
    track.stop();
  });

  videoElem.srcObject = null;
}
```

این کار با دریافت جریانِ عنصر ویدیو از خاصیت {{domxref("HTMLMediaElement.srcObject", "srcObject")}} آن انجام می‌شود. سپس فهرست trackهای جریان با فراخوانی متد {{domxref("MediaStream.getTracks", "getTracks()")}} به دست می‌آید. پس از آن، تنها کاری که باقی می‌ماند این است که با استفاده از {{jsxref("Array.forEach", "forEach()")}} روی فهرست trackها پیمایش کنیم و متد `stop()` هر track را فراخوانی کنیم.

در پایان، `srcObject` برابر با `null` قرار می‌گیرد تا پیوند با شیء {{domxref("MediaStream")}} قطع شود و بتوان آن را آزاد کرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaStreamTrack")}} — رابطی که این متد به آن تعلق دارد.
- {{domxref("MediaStreamTrack.readyState")}}
- {{domxref("MediaStreamTrack/ended_event", "ended")}}