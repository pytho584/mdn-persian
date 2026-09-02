---
title: "HTMLTrackElement: readyState property"
---

---
title: "HTMLTrackElement: readyState property"
short-title: readyState
slug: Web/API/HTMLTrackElement/readyState
page-type: web-api-instance-property
browser-compat: api.HTMLTrackElement.readyState
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنیِ **`readyState`** از رابط {{domxref("HTMLTrackElement")}} عددی را برمی‌گرداند که وضعیت آمادگیِ text track (ردیاب متنی) عنصر {{HTMLElement("track")}} را نشان می‌دهد:

0. NONE: حالت بارگذاری‌نشدهٔ text track.
1. LOADING: حالت در حال بارگذاریِ text track.
2. LOADED: حالت بارگذاری‌شدهٔ text track.
3. ERROR: حالت خطا در بارگذاری text track.

## مقدار

یک عدد؛ `0`، `1`، `2` یا `3`.

## مثال

```js
const trackElement = document.getElementById("exampleTrack");
console.log(trackElement.readyState); // 0, 1, 2, or 3
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLTrackElement")}}
- {{domxref("HTMLMediaElement.readyState")}}
- {{HTMLElement("track")}}