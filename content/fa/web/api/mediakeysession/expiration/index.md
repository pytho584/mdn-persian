---
title: "MediaKeySession: expiration property"
short-title: expiration
slug: Web/API/MediaKeySession/expiration
page-type: web-api-instance-property
browser-compat: api.MediaKeySession.expiration
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`expiration`** از رابط {{domxref('MediaKeySession')}}، زمانی را برمی‌گرداند که پس از آن دیگر نمی‌توان از کلیدهای موجود در نشست جاری برای رمزگشایی داده‌های رسانه‌ای استفاده کرد، یا اگر چنین زمانی وجود نداشته باشد، مقدار `NaN` را بازمی‌گرداند.

این مقدار توسط CDM (ماژول رمزگشایی محتوا) تعیین می‌شود و بر حسب میلی‌ثانیه از ۱ ژانویه ۱۹۷۰، UTC اندازه‌گیری می‌شود. این مقدار ممکن است در طول عمر نشست تغییر کند، مثلاً زمانی که یک عملیات باعث شروع یک پنجره زمانی شود.

## مقدار

یک عدد یا `NaN`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
