---
title: Encrypted Media Extensions API
slug: Web/API/Encrypted_Media_Extensions_API
page-type: web-api-overview
browser-compat: api.Navigator.requestMediaKeySystemAccess
---

{{DefaultAPISidebar("Encrypted Media Extensions")}} {{securecontext_header}}

**API افزونه‌های رسانه رمزنگاری‌شده** (Encrypted Media Extensions) رابط‌هایی را برای کنترل پخش محتوایی که تحت یک طرح مدیریت محدودیت‌های دیجیتال (DRM) قرار دارد، فراهم می‌کند.

دسترسی به این API از طریق {{domxref("Navigator.requestMediaKeySystemAccess()")}} ارائه می‌شود.

## رابط‌ها

- {{domxref("MediaEncryptedEvent")}}
  - : رویداد خاص {{domxref("HTMLMediaElement/encrypted_event", "encrypted")}} را نشان می‌دهد که زمانی رخ می‌دهد که یک {{domxref('HTMLMediaElement')}} با داده‌های مقداردهی اولیه مواجه می‌شود.
- {{domxref("MediaKeyMessageEvent")}}
  - : محتوا و داده‌های مرتبط را در زمانی که ماژول رمزگشایی محتوا (CDM) یک پیام برای نشست (session) تولید می‌کند، شامل می‌شود.
- {{domxref("MediaKeys")}}
  - : مجموعه‌ای از کلیدها را نشان می‌دهد که یک {{domxref('HTMLMediaElement')}} مرتبط می‌تواند برای رمزگشایی داده‌های رسانه در حین پخش از آن‌ها استفاده کند.
- {{domxref("MediaKeySession")}}
  - : یک زمینه (context) برای تبادل پیام با ماژول رمزگشایی محتوا (CDM) را نشان می‌دهد.
- {{domxref("MediaKeyStatusMap")}}
  - : یک نگاشت فقط‌خواندنی از وضعیت‌های کلید رسانه بر اساس شناسه‌های کلید.
- {{domxref("MediaKeySystemAccess")}}
  - : دسترسی به یک سیستم کلید برای رمزگشایی و/یا یک ارائه‌دهنده حفاظت از محتوا را فراهم می‌کند.

### افزونه‌های سایر رابط‌ها

API افزونه‌های رسانه رمزنگاری‌شده رابط‌های زیر را گسترش می‌دهد و ویژگی‌های ذکر شده را به آن‌ها اضافه می‌کند.

#### HTMLMediaElement

- {{domxref("HTMLMediaElement.mediaKeys")}} {{readonlyinline}}
  - : یک شی {{domxref("MediaKeys")}} را ارائه می‌دهد که مجموعه کلیدهایی را نشان می‌دهد که عنصر می‌تواند برای رمزگشایی داده‌های رسانه در حین پخش استفاده کند.
- {{domxref("HTMLMediaElement.setMediaKeys()")}}
  - : {{domxref("MediaKeys")}} ای را تنظیم می‌کند که برای رمزگشایی رسانه در حین پخش استفاده خواهد شد.
- [`encrypted` event](/en-US/docs/Web/API/HTMLMediaElement/encrypted_event)
  - : رویدادی که روی یک {{domxref("HTMLMediaElement")}} هنگامی که داده‌های مقداردهی اولیه در رسانه یافت می‌شود و نشان می‌دهد که رسانه رمزنگاری شده است، رخ می‌دهد.

#### Navigator

- {{domxref("Navigator.requestMediaKeySystemAccess()")}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که به یک شی {{domxref('MediaKeySystemAccess')}} منجر می‌شود که می‌تواند برای دسترسی به یک سیستم کلید رسانه خاص استفاده شود، و این سیستم نیز به نوبه خود برای ایجاد کلیدهای رمزگشایی یک جریان رسانه به کار می‌رود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}