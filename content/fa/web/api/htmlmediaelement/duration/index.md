---
title: "HTMLMediaElement: duration property"
short-title: duration
slug: Web/API/HTMLMediaElement/duration
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.duration
---

{{APIRef("HTML DOM")}}

خاصیتِ **فقط‌خواندنیِ** {{domxref("HTMLMediaElement")}} با نام **`duration`** طول مدت رسانهٔ عنصر را بر حسب ثانیه نشان می‌دهد.

## مقدار

مقداری ممیز شناور با دقت دوبرابر که مدت‌زمان رسانه را بر حسب ثانیه نشان می‌دهد. اگر دادهٔ رسانه‌ای در دسترس نباشد، مقدار `NaN` بازگردانده می‌شود. اگر رسانهٔ عنصر مدت‌زمان مشخصی نداشته باشد — مانند جریان‌های زندهٔ رسانه‌ای — مقدار `duration` برابر با `Infinity` خواهد بود.

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.duration); // NaN
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [فناوری‌های رسانه‌ای وب](/en-US/docs/Web/Media)
- {{domxref("HTMLMediaElement.currentTime")}}: موقعیت پخش فعلی رسانه
- عناصر {{HTMLElement("audio")}} و {{HTMLElement("video")}}