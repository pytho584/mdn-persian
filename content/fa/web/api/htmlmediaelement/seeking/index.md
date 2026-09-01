---
title: "HTMLMediaElement: seeking property"
---

---
title: "HTMLMediaElement: seeking property"
short-title: seeking
slug: Web/API/HTMLMediaElement/seeking
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.seeking
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`seeking`** از رابط {{domxref("HTMLMediaElement")}} یک مقدار بولین است که نشان می‌دهد آیا منبع، یعنی {{htmlelement("audio")}} یا {{htmlelement("video")}}، در حال جست‌وجو (seeking) به موقعیتی جدید است.

## مقدار

یک مقدار بولین.

## مثال‌ها

```js
const el = document.querySelector("video");
console.log(el.seeking); // true or false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("HTMLMediaElement.seeking_event", "seeking")}}
- رویداد {{domxref("HTMLMediaElement.seeked_event", "seeked")}}
- {{domxref("HTMLVideoElement")}}
- {{domxref("HTMLAudioElement")}}