---
title: "PannerNode: panningModel property"
short-title: panningModel
slug: Web/API/PannerNode/panningModel
page-type: web-api-instance-property
browser-compat: api.PannerNode.panningModel
---

{{ APIRef("Web Audio API") }}

ویژگی `panningModel` از رابط {{ domxref("PannerNode") }} یک مقدار شمارشی است که تعیین می‌کند از کدام الگوریتم فضاسازی برای قرار دادن صدا در فضای سه‌بعدی استفاده شود.

مقدارهای ممکن عبارتند از:

- `equalpower`: الگوریتم پنینگ توان-مساوی را نشان می‌دهد که عموماً ساده و کارآمد در نظر گرفته می‌شود. `equalpower` مقدار پیش‌فرض است.
- `HRTF`: خروجی استریوی با کیفیت بالاتر از `equalpower` ارائه می‌دهد — آن از کانولوشن با پاسخ‌های ضربه‌ی اندازه‌گیری‌شده از افراد انسانی استفاده می‌کند.

## مقدار

یک enum — به [`PanningModelType`](https://webaudio.github.io/web-audio-api/#idl-def-PanningModelType) مراجعه کنید.

## مثال‌ها

برای کد نمونه، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)