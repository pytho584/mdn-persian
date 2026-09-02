---
title: "MediaRecorderErrorEvent: MediaRecorderErrorEvent() constructor"
short-title: MediaRecorderErrorEvent()
slug: Web/API/MediaRecorderErrorEvent/MediaRecorderErrorEvent
page-type: web-api-constructor
status:
  - deprecated
  - non-standard
browser-compat: api.MediaRecorderErrorEvent.MediaRecorderErrorEvent
---

{{APIRef("MediaStream Recording")}}{{Deprecated_Header}}{{Non-standard_Header}}

سازنده‌ی **`MediaRecorderErrorEvent()`** یک شیء {{domxref("MediaRecorderErrorEvent")}} جدید ایجاد می‌کند که نشان‌دهنده‌ی خطایی است که در حین ضبط رسانه توسط [API ضبط جریان رسانه](/en-US/docs/Web/API/MediaStream_Recording_API) رخ داده است.

> [!NOTE]
> به طور کلی، شما خودتان این رویدادها را ایجاد نمی‌کنید؛ آن‌ها زمانی که در حین ضبط رسانه خطایی رخ می‌دهد، به پیاده‌سازی شما از {{domxref("MediaRecorder.error_event", "onerror")}} تحویل داده می‌شوند.

## نحو

```js-nolint
new MediaRecorderErrorEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته شامل نام رویداد. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را `error` قرار می‌دهند.
- `options`
  - : یک شیء که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `error`
      - : یک {{domxref("DOMException")}} که خطای رخ‌داده را توصیف می‌کند. ویژگی {{domxref("DOMException.name", "name")}} این شیء باید نام خطای رخ‌داده را نشان دهد. فیلدهای دیگر ممکن است وجود داشته باشند یا نداشته باشند.

> [!NOTE]
> برخی از {{Glossary("user agent", "عامل‌های کاربری")}} ویژگی‌های دیگری به شیء `error` اضافه می‌کنند که اطلاعاتی مانند dump پشته، نام فایل جاوااسکریپت و شماره خطی که خطا در آن رخ داده و سایر ابزارهای اشکال‌زدایی را فراهم می‌کند، اما شما نباید در محیط تولید به این اطلاعات اعتماد کنید.

### مقدار بازگشتی

یک شیء جدید {{domxref("MediaRecorderErrorEvent")}}.

## مشخصات

این ویژگی دیگر بخشی از هیچ مشخصاتی نیست و در مسیر تبدیل شدن به یک استاندارد نیست.

## سازگاری با مرورگر

{{Compat}}