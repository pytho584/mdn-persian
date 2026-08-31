---
title: "CompositionEvent: locale property"
short-title: locale
slug: Web/API/CompositionEvent/locale
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.CompositionEvent.locale
---

{{deprecated_header}}{{APIRef("UI Events")}}{{Non-standard_header}}

ویژگی فقط‌خواندنی **`locale`** در رابط {{domxref("CompositionEvent")}}، locale (منطقه/زبان) روش ورودی فعلی را برمی‌گرداند (مثلاً locale چیدمان صفحه‌کلید، اگر ترکیب با یک {{glossary("Input method editor")}} مرتبط باشد).

> [!WARNING]
> حتی در مرورگرهایی که از این ویژگی پشتیبانی می‌کنند، به مقدار موجود در آن اعتماد نکنید.
> حتی اگر از نظر فنی در دسترس باشد، روش مقداردهی آن هنگام ایجاد یک {{domxref("CompositionEvent")}} تضمین‌شده و سازگار نیست.

## مقدار

یک رشته (string) که locale روش ورودی فعلی را نشان می‌دهد.

## مشخصات

این ویژگی در نسخه‌های اولیه مشخصات مختلف وجود داشت. اکنون فقط به دلایل سازگاری نگهداری می‌شود و روش مقداردهی آن هنگام ایجاد یک {{domxref("CompositionEvent")}} [به‌خوبی تعریف نشده است](https://github.com/w3c/uievents/issues/48).

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CompositionEvent")}}