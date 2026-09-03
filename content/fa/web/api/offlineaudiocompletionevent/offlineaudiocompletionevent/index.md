---
title: "OfflineAudioCompletionEvent: OfflineAudioCompletionEvent() constructor"
short-title: OfflineAudioCompletionEvent()
slug: Web/API/OfflineAudioCompletionEvent/OfflineAudioCompletionEvent
page-type: web-api-constructor
browser-compat: api.OfflineAudioCompletionEvent.OfflineAudioCompletionEvent
---

{{APIRef("Web Audio API")}}

سازنده **`OfflineAudioCompletionEvent()`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک شیء جدید {{domxref("OfflineAudioCompletionEvent")}} ایجاد می‌کند.

> [!NOTE]
> معمولاً نیازی به استفاده دستی از این سازنده ندارید. رویدادهای `OfflineAudioCompletionEvent` به دلایل قدیمی به نمونه‌های {{domxref("OfflineAudioContext")}} ارسال می‌شوند.

## نحو

```js-nolint
new OfflineAudioCompletionEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نام رویداد است. این مقدار به بزرگی و کوچکی حروف حساس است و مرورگرها آن را `complete` تنظیم می‌کنند.
- `options`
  - : یک شیء که علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}} می‌تواند ویژگی‌های زیر را داشته باشد:
    - `renderedBuffer`
      - : {{domxref("AudioBuffer")}} رندر شده حاوی داده‌های صوتی.

### مقدار بازگشتی

یک شیء جدید {{domxref("OfflineAudioCompletionEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}