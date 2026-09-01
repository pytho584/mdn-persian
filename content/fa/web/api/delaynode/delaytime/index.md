---
title: "DelayNode: delayTime property"
short-title: delayTime
slug: Web/API/DelayNode/delayTime
page-type: web-api-instance-property
browser-compat: api.DelayNode.delayTime
---

{{ APIRef("Web Audio API") }}

خاصیت `delayTime` از رابط {{ domxref("DelayNode") }} یک [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) از نوع {{domxref("AudioParam")}} است که میزان تأخیری را که باید اعمال شود، مشخص می‌کند.

`delayTime` بر حسب ثانیه بیان می‌شود، کمینه‌ی آن `0` است و بیشینه‌ی آن توسط آرگومان `maxDelayTime` متد {{domxref("BaseAudioContext.createDelay")}} که آن را ایجاد کرده، تعیین می‌شود.

> [!NOTE]
> اگرچه {{domxref("AudioParam")}} برگشتی فقط‌خواندنی است، اما مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مقدار

یک {{domxref("AudioParam")}}.

## مثال‌ها

برای کد مثال، [`BaseAudioContext.createDelay()`](/en-US/docs/Web/API/BaseAudioContext/createDelay#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)