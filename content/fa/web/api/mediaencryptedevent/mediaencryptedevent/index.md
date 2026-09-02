---
title: "MediaEncryptedEvent: MediaEncryptedEvent() constructor"
short-title: MediaEncryptedEvent()
slug: Web/API/MediaEncryptedEvent/MediaEncryptedEvent
page-type: web-api-constructor
browser-compat: api.MediaEncryptedEvent.MediaEncryptedEvent
---

{{APIRef("Encrypted Media Extensions")}}

سازندهٔ **`MediaEncryptedEvent`** یک شیء جدید {{domxref("MediaEncryptedEvent")}} می‌سازد.

> [!NOTE]
> در موارد عادی نیازی به فراخوانی این سازنده در کد خود ندارید، زیرا چنین رویدادهایی معمولاً در صورت نیاز توسط مرورگر تولید می‌شوند.

## Syntax

```js-nolint
new MediaEncryptedEvent(type)
new MediaEncryptedEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته با نام رویداد. به حروف کوچک و بزرگ حساس است و مرورگرها همیشه آن را روی `encrypted` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `initDataType`
      - : یک رشته با نوع داده‌های اولیه (initialization data) موجود در این شیء.
    - `message`
      - : یک {{jsxref("ArrayBuffer")}} حاوی داده‌های اولیه، یا `null` اگر داده‌ای وجود نداشته باشد.

### مقدار بازگشتی

یک شیء جدید {{domxref("MediaEncryptedEvent")}}.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}