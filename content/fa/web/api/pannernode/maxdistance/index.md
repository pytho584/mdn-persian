---
title: "PannerNode: maxDistance property"
short-title: maxDistance
slug: Web/API/PannerNode/maxDistance
page-type: web-api-instance-property
browser-compat: api.PannerNode.maxDistance
---

{{ APIRef("Web Audio API") }}

ویژگی `maxDistance` از رابط {{ domxref("PannerNode") }} یک مقدار اعشاری (double) است که حداکثر فاصله بین منبع صوتی و شنونده را نشان می‌دهد. پس از این فاصله، حجم صدا دیگر کاهش نمی‌یابد. این مقدار تنها در مدل فاصله `linear` استفاده می‌شود.

مقدار پیش‌فرض ویژگی `maxDistance` برابر با `10000` است.

## مقدار

یک عدد اعشاری (double). مقدار پیش‌فرض `10000` است و مقادیر غیرمثبت مجاز نیستند.

### استثناها

- {{jsxref("RangeError")}}
  - : اگر به ویژگی مقداری خارج از محدوده مجاز داده شود، این خطا پرتاب می‌شود.

## مثال‌ها

برای مشاهده کد مثال، به [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)