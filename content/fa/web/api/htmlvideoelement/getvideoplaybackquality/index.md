---
title: "HTMLVideoElement: getVideoPlaybackQuality() method"
---

---
title: "HTMLVideoElement: getVideoPlaybackQuality() method"
short-title: getVideoPlaybackQuality()
slug: Web/API/HTMLVideoElement/getVideoPlaybackQuality
page-type: web-api-instance-method
browser-compat: api.HTMLVideoElement.getVideoPlaybackQuality
---

{{ APIRef("HTML DOM") }}

متد **{{domxref("HTMLVideoElement")}}** با نام **`getVideoPlaybackQuality()`** یک شیء {{domxref("VideoPlaybackQuality")}} می‌سازد و برمی‌گرداند که شامل معیارهایی از جمله تعداد فریم‌های از دست رفته است.

از داده‌های بازگشتی می‌توان برای ارزیابی کیفیت جریان ویدیو استفاده کرد.

## سینتکس

```js-nolint
getVideoPlaybackQuality()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{domxref("VideoPlaybackQuality")}} که اطلاعاتی درباره کیفیت پخش فعلی عنصر ویدیو فراهم می‌کند.

## مثال‌ها

این مثال یک عنصر را به‌روزرسانی می‌کند تا تعداد کل فریم‌های ویدیویی را که تاکنون در فرایند پخش سپری شده‌اند نشان دهد. این مقدار شامل فریم‌های افتاده یا خراب نیز می‌شود، بنابراین با «تعداد کل فریم‌های پخش‌شده» یکسان نیست.

```js
const videoElem = document.getElementById("my_vid");
const counterElem = document.getElementById("counter");
const quality = videoElem.getVideoPlaybackQuality();

counterElem.innerText = quality.totalVideoFrames;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("video")}}
- رابط {{domxref("VideoPlaybackQuality")}}