---
title: "MediaKeySession: closed property"
short-title: closed
slug: Web/API/MediaKeySession/closed
page-type: web-api-instance-property
browser-compat: api.MediaKeySession.closed
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`closed`** از رابط {{domxref('MediaKeySession')}} یک {{jsxref('Promise')}} برمی‌گرداند که هنگام بسته‌شدن یک {{domxref('MediaKeySession')}} علامت می‌دهد.
این وعده (Promise) فقط می‌تواند با موفقیت انجام شود و هرگز رد نمی‌شود.
بستن یک نشست به این معنی است که مجوزها و کلیدهای مرتبط با آن دیگر برای رمزگشایی داده‌های رسانه‌ای معتبر نیستند.

## مقدار

یک {{jsxref("Promise")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}