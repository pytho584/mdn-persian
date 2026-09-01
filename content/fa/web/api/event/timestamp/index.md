---
title: "Event: timeStamp property"
short-title: timeStamp
slug: Web/API/Event/timeStamp
page-type: web-api-instance-property
browser-compat: api.Event.timeStamp
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`timeStamp`** از رابط {{domxref("Event")}} زمان ایجاد رویداد را بر حسب میلی‌ثانیه برمی‌گرداند.

## مقدار

این مقدار تعداد میلی‌ثانیه‌هایی است که از آغاز «مبدأ زمان» تا لحظه ایجاد رویداد سپری شده است.
اگر شیء سراسری {{domxref("Window")}} باشد، مبدأ زمان لحظه‌ای است که کاربر روی پیوند کلیک کرده، یا لحظه‌ای که اسکریپتِ آغازکننده بارگذاری سند فراخوانی شده است.
در یک worker، مبدأ زمان لحظه ایجاد آن worker است.

این مقدار یک {{domxref("DOMHighResTimeStamp")}} با دقت ۵ میکروثانیه (۰٫۰۰۵ میلی‌ثانیه) است، اما برای جلوگیری از [اثر انگشت](/en-US/docs/Glossary/Fingerprinting)، [دقت آن کاهش می‌یابد](#reduced_time_precision).

## مثال

### HTML

```html
<p>
  Focus this iframe and press any key to get the current timestamp for the
  keypress event.
</p>
<p>timeStamp: <span id="time">-</span></p>
```

### JavaScript

```js
function getTime(event) {
  const time = document.getElementById("time");
  time.firstChild.nodeValue = event.timeStamp;
}
document.body.addEventListener("keypress", getTime);
```

### نتیجه

{{EmbedLiveSample("Example", "100%", 100)}}

## کاهش دقت زمان

برای محافظت در برابر حملات زمان‌بندی و [اثر انگشت](/en-US/docs/Glossary/Fingerprinting)، ممکن است دقت `event.timeStamp` بسته به تنظیمات مرورگر گرد شود. در فایرفاکس، تنظیم `privacy.reduceTimerPrecision` به‌صورت پیش‌فرض فعال است و مقدار پیش‌فرض آن ۲ میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید؛ در این حالت، دقت، ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` خواهد بود، هر کدام بزرگ‌تر باشد.

برای مثال، با کاهش دقت زمان، نتیجه `event.timeStamp` همیشه مضربی از ۲ خواهد بود، یا با فعال بودن `privacy.resistFingerprinting`، مضربی از ۱۰۰ (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`) خواهد بود.

```js
// reduced time precision (2ms) in Firefox 60
event.timeStamp;
// Might be:
// 9934
// 10362
// 11670
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
event.timeStamp;
// Might be:
// 53500
// 58900
// 64400
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}