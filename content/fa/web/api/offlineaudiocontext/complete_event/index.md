---
title: "OfflineAudioContext: complete event"
short-title: complete
slug: Web/API/OfflineAudioContext/complete_event
page-type: web-api-event
browser-compat: api.OfflineAudioContext.complete_event
---

{{APIRef("Web Audio API")}}

رویداد `complete` در رابط {{domxref("OfflineAudioContext")}} زمانی رخ می‌دهد که رندرگیری یک زمینه صوتی آفلاین (offline audio context) کامل شود.

این رویداد قابل لغو نیست و حباب نمی‌زند.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("complete", (event) => { })

oncomplete = (event) => { }
```

## نوع رویداد

یک رویداد از نوع {{domxref("OfflineAudioCompletionEvent")}} که از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("OfflineAudioCompletionEvent")}}

## مثال‌ها

پس از اتمام پردازش، می‌توانید از مدیریت‌کننده رویداد `complete` استفاده کنید تا به کاربر اعلام کنید صدا آماده پخش است و دکمه پخش را فعال کنید:

```js
const offlineAudioCtx = new OfflineAudioContext();

offlineAudioCtx.addEventListener("complete", () => {
  console.log("Offline audio processing now complete");
  alert("Song processed and ready to play");
  playBtn.disabled = false;
});
```

همچنین می‌توانید مدیریت‌کننده رویداد را با استفاده از ویژگی `oncomplete` تنظیم کنید:

```js
const offlineAudioCtx = new OfflineAudioContext();

offlineAudioCtx.oncomplete = () => {
  console.log("Offline audio processing now complete");
  alert("Song processed and ready to play");
  playBtn.disabled = false;
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
