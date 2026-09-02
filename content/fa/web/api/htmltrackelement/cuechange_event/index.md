---
title: "HTMLTrackElement: cuechange event"
short-title: cuechange
slug: Web/API/HTMLTrackElement/cuechange_event
page-type: web-api-event
browser-compat: api.HTMLTrackElement.cuechange_event
---

{{APIRef("WebVTT")}}

رویداد **`cuechange`** زمانی رخ می‌دهد که یک {{domxref("TextTrack")}} کیوهای (cues) در حال نمایش خود را تغییر دهد. این رویداد هم روی `TextTrack` و هم روی {{domxref("HTMLTrackElement")}} (در صورت وجود) که در آن ارائه می‌شود، فراخوانی می‌شود.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم یک ویژگی کنترل‌کننده رویداد، از این نحو استفاده کنید:

```js-nolint
addEventListener("cuechange", (event) => { })

oncuechange = (event) => { }
```

## نوع رویداد

یک {{DOMxRef("Event")}} عمومی بدون هیچ ویژگی اضافه‌شده.

## مثال‌ها

{{domxref("TextTrack")}} زیرین، که با ویژگی {{domxref("HTMLTrackElement.track", "track")}} مشخص می‌شود، هر بار که کیوی (cue) در حال ارائه تغییر کند، یک رویداد `cuechange` دریافت می‌کند. این اتفاق حتی اگر track با یک عنصر رسانه‌ای مرتبط نباشد نیز رخ می‌دهد.

اگر track _با یک عنصر رسانه‌ای مرتبط باشد_، با استفاده از عنصر {{HTMLElement("track")}} به عنوان فرزند عنصر {{HTMLElement("audio")}} یا {{HTMLElement("video")}}، رویداد `cuechange` همچنین به {{domxref("HTMLTrackElement")}} ارسال می‌شود.

```js
let textTrackElem = document.getElementById("text-track");

textTrackElem.addEventListener("cuechange", (event) => {
  let cues = event.target.track.activeCues;
});
```

همچنین می‌توانید از کنترل‌کننده رویداد `oncuechange` استفاده کنید:

```js
let textTrackElem = document.getElementById("text-track");

textTrackElem.oncuechange = (event) => {
  let cues = event.target.track.activeCues;
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{glossary("WebVTT")}}
- همین رویداد روی {{domxref("TextTrack")}}: {{domxref("TextTrack.cuechange_event", "cuechange")}}