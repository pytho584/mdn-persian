---
title: "PannerNode: coneOuterGain property"
short-title: coneOuterGain
slug: Web/API/PannerNode/coneOuterGain
page-type: web-api-instance-property
browser-compat: api.PannerNode.coneOuterGain
---

{{ APIRef("Web Audio API") }}

ویژگی `coneOuterGain` در رابط {{ domxref("PannerNode") }} یک مقدار double است که میزان کاهش حجم صدا در خارج از مخروط تعریف‌شده توسط ویژگی {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} را توصیف می‌کند.

مقدار پیش‌فرض ویژگی `coneOuterGain` برابر با `0` است؛ یعنی هیچ صدایی در خارج از مخروط شنیده نمی‌شود.

## مقدار

یک مقدار double. پیش‌فرض آن `0` است و مقدار آن می‌تواند در بازه ۰ تا ۱ باشد.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر به ویژگی مقداری خارج از محدوده مجاز (۰ تا ۱) داده شود، این خطا پرتاب می‌شود.

## مثال‌ها

برای مشاهده کد مثالی که نشان می‌دهد تغییر پارامترهای جهت‌گیری {{domxref("PannerNode")}} به‌همراه {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}} و {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} چگونه بر حجم صدا تأثیر می‌گذارد، به [`PannerNode.orientationX`](/en-US/docs/Web/API/PannerNode/orientationX#example) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضاسازی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)