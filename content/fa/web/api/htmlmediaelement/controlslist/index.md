---
title: "HTMLMediaElement: controlsList property"
short-title: controlsList
slug: Web/API/HTMLMediaElement/controlsList
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.controlsList
---

{{APIRef("HTML DOM")}}

ویژگی **`controlsList`** از رابط {{domxref("HTMLMediaElement")}} یک {{domxref("DOMTokenList")}} برمی‌گرداند که به عامل کاربر (user agent) کمک می‌کند تا انتخاب کند چه کنترل‌هایی را روی عنصر رسانه نشان دهد، هرگاه عامل کاربر مجموعه کنترل‌های خود را نمایش می‌دهد. این DOMTokenList می‌تواند یک یا چند مقدار از سه مقدار ممکن را بگیرد: `nodownload`، `nofullscreen` و `noremoteplayback`.

## مقدار

یک {{domxref("DOMTokenList")}}.

مقدار `controlsList` را می‌توان با ارسال یک رشته که نشان‌دهنده ویژگی {{domxref("DOMTokenList/value", "value")}} مربوط به `DOMTokenList` است، تنظیم کرد.

## مثال‌ها

### دریافت ویژگی controlsList

ویژگی `controlsList` یک شیء {{domxref("DOMTokenList")}} شامل مقدار فعلی تنظیم‌شده را برمی‌گرداند.

```js
const video = document.createElement("video");
console.log(video.controlsList.value); // ""

video.controlsList.add("noremoteplayback");
console.log(video.controlsList.value); // "noremoteplayback"
```

### تنظیم ویژگی controlsList

همچنین می‌توانید `controlsList` را با تنظیم مستقیم آن به یک رشته حاوی مقدار جدید، تغییر دهید.

```js
const audio = document.createElement("audio");
audio.controlsList = "nodownload";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Chrome HTMLMediaElement controlsList Sample](https://googlechrome.github.io/samples/media/controlslist.html)