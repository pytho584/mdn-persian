---
title: "HTMLTrackElement: kind property"
short-title: kind
slug: Web/API/HTMLTrackElement/kind
page-type: web-api-instance-property
browser-compat: api.HTMLTrackElement.kind
---

{{ApiRef("HTML DOM")}}

ویژگی **`kind`** از رابط {{domxref("HTMLTrackElement")}} نشان‌دهندهٔ نوع زیرنویس (track) یا نحوهٔ استفاده از آن است. این ویژگی منعکس‌کنندهٔ ویژگی [`kind`](/en-US/docs/Web/HTML/Reference/Elements/track#kind) (از نوع شمارشی) در عنصر {{htmlelement("track")}} می‌باشد.

اگر `kind` تنظیم نشده باشد، مقدار `subtitles` استفاده می‌شود. اگر ویژگی به یکی از مقادیر شمارشی معتبر تنظیم نشده باشد، نامعتبر تلقی شده و `metadata` به کار می‌رود. سایر مقادیر معتبر شامل `captions`، `descriptions` و `chapters` هستند.

## مقدار

یک رشته؛ به صورت حروف کوچک: `captions`، `descriptions`، `chapters`، `subtitles` یا `metadata`.

## مثال

با در نظر گرفتن کد زیر:

```html
<track src="track.vtt" id="exampleTrack" />
```

نتایج زیر را به دست می‌آوریم:

```js
const trackElement = document.getElementById("exampleTrack");
// missing value
console.log(trackElement.kind); // "subtitles"
trackElement.kind = "INVALID";
// invalid value
console.log(trackElement.kind); // "metadata"
trackElement.kind = "CAPTIONS";
// valid value
console.log(trackElement.kind); // "captions"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTrackElement.track")}}
- {{domxref("HTMLTrackElement.label")}}