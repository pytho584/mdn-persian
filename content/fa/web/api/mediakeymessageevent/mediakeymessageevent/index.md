---
title: "MediaKeyMessageEvent: MediaKeyMessageEvent() constructor"
short-title: MediaKeyMessageEvent()
slug: Web/API/MediaKeyMessageEvent/MediaKeyMessageEvent
page-type: web-api-constructor
browser-compat: api.MediaKeyMessageEvent.MediaKeyMessageEvent
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

سازندهٔ **`MediaKeyMessageEvent`** یک شیء جدید از نوع {{domxref("MediaKeyMessageEvent")}} ایجاد می‌کند.

## نحو

```js-nolint
new MediaKeyMessageEvent(type)
new MediaKeyMessageEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد.
    به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را روی `message` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : شیءایی که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `messageType`
      - : نوع پیام که به برنامه‌ها اجازه می‌دهد بدون تجزیهٔ پیام‌ها بین آن‌ها تمایز قائل شوند.
        مقادیر مجاز عبارتند از: `license-request`، `license-renewal`، `license-renewal` یا `individualization-request`.
    - `message`
      - : آرایه‌ای شامل پیام تولیدشده توسط ماژول رمزگشایی محتوا.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("MediaKeyMessageEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}