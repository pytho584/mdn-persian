---
title: "HTMLTrackElement: track property"
short-title: track
slug: Web/API/HTMLTrackElement/track
page-type: web-api-instance-property
browser-compat: api.HTMLTrackElement.track
---

{{APIRef("HTML DOM")}}

خاصیت فقط‑خواندنی **`track`** در رابط {{domxref("HTMLTrackElement")}} یک شیء {{DOMxRef("TextTrack")}} بازمی‌گرداند که متناظر با ره‌گیری متن (text track) عنصر {{HTMLElement("track")}} است.

## مقدار

یک شیء {{DOMxRef("TextTrack")}}.

## مثال

```js
const trackElement = document.getElementById("exampleTrack");
console.dir(trackElement.track);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTrackElement")}}
- {{domxref("textTrack")}}
- {{HTMLElement("track")}}