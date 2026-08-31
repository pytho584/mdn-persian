---
title: "AudioContext: sinkchange event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/sinkchange_event"
translated_by: "n8n + AI"
short-title: sinkchange
slug: Web/API/AudioContext/sinkchange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.AudioContext.sinkchange_event
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}

رویداد **`sinkchange`** از رابط {{domxref("AudioContext")}} زمانی پرتاب می‌شود که دستگاه خروجی صدا (و در نتیجه {{domxref("AudioContext.sinkId")}}) تغییر کرده است.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("sinkchange", (event) => { })

onsinkchange = (event) => { }
```

## نوع رویداد

{{domxref("Event")}}.

{{InheritanceDiagram("Event")}}

## مثال‌ها

یک شنونده رویداد `sinkchange` می‌تواند برای گزارش تغییر دستگاه خروجی صدا استفاده شود. توجه داشته باشید که اگر {{domxref("AudioContext.sinkId", "sinkId")}} شامل یک شیء {{domxref("AudioSinkInfo")}} باشد، نشان می‌دهد که صدا به گونه‌ای تغییر کرده است که روی هیچ دستگاه خروجی پخش نشود.

```js
audioCtx.addEventListener("sinkchange", () => {
  if (typeof audioCtx.sinkId === "object" && audioCtx.sinkId.type === "none") {
    console.log("Audio changed to not play on any device");
  } else {
    console.log(`Audio output device changed to ${audioCtx.sinkId}`);
  }
});
```

برای کد عملی، [مثال آزمایشی SetSinkId](https://mdn.github.io/dom-examples/audiocontext-setsinkid/) ما را ببینید (همچنین [کد منبع](https://github.com/mdn/dom-examples/tree/main/audiocontext-setsinkid) را بررسی کنید).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [تغییر دستگاه خروجی مقصد در Web Audio](https://developer.chrome.com/blog/audiocontext-setsinkid/)
- {{domxref("AudioContext.setSinkId()")}}
- {{domxref("AudioContext.sinkId")}}