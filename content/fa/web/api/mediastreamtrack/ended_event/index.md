---
title: "MediaStreamTrack: ended event"
short-title: ended
slug: Web/API/MediaStreamTrack/ended_event
page-type: web-api-event
browser-compat: api.MediaStreamTrack.ended_event
---

{{APIRef("Media Capture and Streams")}}

رویداد **`ended`** از رابط {{domxref("MediaStreamTrack")}} زمانی فعال می‌شود که پخش یا استریم به دلیل رسیدن به پایان رسانه یا در دسترس نبودن داده بیشتر متوقف شود.

این رویداد قابل لغو (cancelable) نیست و انتشار (bubble) نمی‌شود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("ended", (event) => { })

onended = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## نکات استفاده

رویدادهای `ended` زمانی فعال می‌شوند که منبع ردگیری (track) جریان رسانه به طور دائمی ارسال داده روی جریان را متوقف کند. راه‌های مختلفی برای این اتفاق وجود دارد، از جمله:

- داده دیگری برای ارسال باقی نمانده باشد.
- کاربر مجوزهای لازم برای ارسال داده را لغو کرده باشد.
- سخت‌افزاری که داده منبع را تولید می‌کند حذف یا خارج شده باشد.
- یک همتای راه دور (remote peer) به طور دائمی ارسال داده را متوقف کرده باشد.
- تنها حالتی که ردگیری به پایان می‌رسد اما رویداد `ended` فعال نمی‌شود، زمانی است که {{domxref("MediaStreamTrack.stop")}} فراخوانی شود.

مکث رسانه رویداد `ended` را ایجاد _نمی‌کند_.

## مثال‌ها

این مثال یک مدیریت‌کننده رویداد برای رویداد `ended` تنظیم می‌کند که با تغییر یک نماد روی صفحه، نشان می‌دهد که ردگیری دیگر فعال نیست.

```js
track.addEventListener("ended", () => {
  let statusElem = document.getElementById("status-icon");
  statusElem.src = "/images/stopped-icon.png";
});
```

همچنین می‌توانید مدیریت‌کننده رویداد را با استفاده از ویژگی `onended` تنظیم کنید:

```js
track.onended = () => {
  let statusElem = document.getElementById("status-icon");

  statusElem.src = "/images/stopped-icon.png";
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("HTMLMediaElement.playing_event", 'playing')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.waiting_event", 'waiting')}} در HTMLMediaElement
- رویداد {{domxref("HTMLMediaElement.seeking_event", 'seeking')}} در HTMLMediaElement
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}
- رویداد {{domxref("HTMLMediaElement.ended_event", 'ended')}} در HTMLMediaElement
- رویداد {{domxref("AudioScheduledSourceNode.ended_event", 'ended')}} در AudioScheduledSourceNode