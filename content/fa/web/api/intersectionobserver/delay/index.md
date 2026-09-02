---
title: "IntersectionObserver: delay property"
short-title: delay
slug: Web/API/IntersectionObserver/delay
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IntersectionObserver.delay
---

{{APIRef("Intersection Observer API")}}{{SeeCompatTable}}

ویژگی فقط-خواندنی **`delay`** در رابط {{domxref("IntersectionObserver")}} حداقل تأخیر بین اعلان‌های این ناظر را مشخص می‌کند.

تأخیر برای محدود کردن نرخ ارائه اعلان‌ها هنگام [ردیابی قابلیت مشاهده](/en-US/docs/Web/API/IntersectionObserver/trackVisibility) استفاده می‌شود، زیرا این یک عملیات از نظر محاسباتی سنگین است. توصیه این است که هنگام ردیابی قابلیت مشاهده، تأخیر را روی بزرگترین مقدار قابل تحمل تنظیم کنید.

## مقدار

یک عدد مثبت بر حسب میلی‌ثانیه.

مقدار با استفاده از آرگومان [`option.delay`](/en-US/docs/Web/API/IntersectionObserver/IntersectionObserver#delay) در سازنده `IntersectionObserver()` تنظیم می‌شود. اگر {{domxref("IntersectionObserver/trackVisibility","trackVisibility")}} برابر `true` باشد، مقدار به ۱۰۰ یا بیشتر محدود می‌شود، در غیر این صورت پیش‌فرض آن ۰ است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [زمان‌بندی قابلیت مشاهده عناصر با Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API/Timing_element_visibility)