---
title: "PresentationRequest: getAvailability() method"
short-title: getAvailability()
slug: Web/API/PresentationRequest/getAvailability
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PresentationRequest.getAvailability
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

هنگامی که متد `getAvailability()` فراخوانی می‌شود، عامل کاربر (_user agent_) _باید_ مراحل زیر را اجرا کند:

- ورودی
  - : _presentationUrls_، فهرستی از [URLهای درخواست ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-request-urls)
- خروجی
  - : _P_، یک [Promise](https://www.w3.org/TR/presentation-api/#dfn-promise)

1. اگر یکی از شرایط زیر برقرار باشد:
   - نتیجه اجرای [الگوریع ممنوعیت بافت‌های امنیتی مختلط](https://www.w3.org/TR/presentation-api/#dfn-prohibits-mixed-security-contexts-algorithm) روی [شی تنظیمات](https://www.w3.org/TR/presentation-api/#dfn-settings-object) سند، «ممنوعیت بافت‌های امنیتی مختلط» باشد و _presentationUrl_ یک [URL از پیش تأییدنشده](https://www.w3.org/TR/presentation-api/#dfn-a-priori-unauthenticated-url) باشد.
   - [مجموعه پرچم‌های sandboxing فعال](https://www.w3.org/TR/presentation-api/#dfn-active-sandboxing-flag-set) شی سند، [پرچم بافت مرورگری ارائه sandbox شده](https://www.w3.org/TR/presentation-api/#sandboxed-presentation-browsing-context-flag) را تنظیم کرده باشد.

   مراحل فرعی زیر را اجرا کن:
   1. یک [Promise](https://www.w3.org/TR/presentation-api/#dfn-promise) برگردان که با یک `SecurityError` {{domxref("DOMException")}} رد شده باشد.
   2. این مراحل را خاتمه بده.

2. بگذارید _P_ یک [Promise](https://www.w3.org/TR/presentation-api/#dfn-promise) جدید باشد.
3. _P_ را برگردان، اما این مراحل را [به صورت موازی](https://www.w3.org/TR/presentation-api/#dfn-in-parallel) ادامه بده.
4. اگر عامل کاربر قادر به [نظارت بر فهرست نمایشگرهای ارائه موجود](https://www.w3.org/TR/presentation-api/#dfn-monitor-the-list-of-available-presentation-displays) برای کل مدت [بافت مرورگری کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-browsing-context) نباشد (مثلاً به دلیل غیرفعال کردن این ویژگی توسط کاربر)، آنگاه:
   1. _P_ را با یک شی `PresentationAvailability` جدید که ویژگی `value` آن روی `false` تنظیم شده است، [پذیرفته](https://www.w3.org/TR/presentation-api/#dfn-resolving-a-promise) کن.
   2. تمام مراحل باقی‌مانده را خاتمه بده.

5. اگر عامل کاربر قادر به [نظارت مداوم بر فهرست نمایشگرهای ارائه موجود](https://www.w3.org/TR/presentation-api/#dfn-monitor-the-list-of-available-presentation-displays) نباشد اما بتواند برای شروع یک اتصال، نمایشگرهای ارائه را پیدا کند، آنگاه:
   1. _P_ را با یک `NotSupportedError` {{domxref("DOMException")}} [رد](https://www.w3.org/TR/presentation-api/#dfn-rejecting-a-promise) کن.
   2. تمام مراحل باقی‌مانده را خاتمه بده.

6. اگر یک tuple (_A_, _presentationUrls_) در [مجموعه اشیاء در دسترس بودن](https://www.w3.org/TR/presentation-api/#dfn-set-of-availability-objects) وجود داشته باشد، آنگاه:
   1. _P_ را با _A_ [پذیرفته](https://www.w3.org/TR/presentation-api/#dfn-resolving-a-promise) کن.
   2. تمام مراحل باقی‌مانده را خاتمه بده.

7. بگذارید _A_ یک شی `PresentationAvailability` جدید باشد که ویژگی `value` آن به صورت زیر تنظیم شده است:
   1. اگر [فهرست نمایشگرهای ارائه موجود](https://www.w3.org/TR/presentation-api/#dfn-list-of-available-presentation-displays) خالی باشد، `false`.
   2. اگر حداقل یک [نمایشگر ارائه سازگار](https://www.w3.org/TR/presentation-api/#dfn-compatible-presentation-display) برای برخی از اعضای _presentationUrls_ وجود داشته باشد، `true`. یعنی یک ورودی _(presentationUrl, display)_ در [فهرست نمایشگرهای ارائه موجود](https://www.w3.org/TR/presentation-api/#dfn-list-of-available-presentation-displays) برای برخی _presentationUrl_ در _presentationUrls_ وجود داشته باشد.
   3. در غیر این صورت، `false`.

8. یک tuple (_A_, _presentationUrls_) ایجاد کن و آن را به [مجموعه اشیاء در دسترس بودن](https://www.w3.org/TR/presentation-api/#dfn-set-of-availability-objects) اضافه کن.
9. الگوریتم [نظارت بر فهرست نمایشگرهای ارائه موجود](https://www.w3.org/TR/presentation-api/#dfn-monitor-the-list-of-available-presentation-displays) را اجرا کن.
10. _P_ را با _A_ [پذیرفته](https://www.w3.org/TR/presentation-api/#dfn-resolving-a-promise) کن.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}