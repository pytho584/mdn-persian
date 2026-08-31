---
title: "CloseEvent: CloseEvent() constructor"
short-title: CloseEvent()
slug: Web/API/CloseEvent/CloseEvent
page-type: web-api-constructor
browser-compat: api.CloseEvent.CloseEvent
---

{{APIRef("Websockets API")}}{{AvailableInWorkers}}

سازندهٔ **`CloseEvent()`** یک شیء جدید از نوع {{domxref("CloseEvent")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new CloseEvent(type)
new CloseEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای است با نام رویداد.
    این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را روی `close` قرار می‌دهند.
- `options` {{optional_inline}}
  - : شیءایی است که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، ویژگی‌های زیر را دارد:
    - `wasClean` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد آیا اتصال به‌طور تمیز بسته شده است یا نه. مقدار پیش‌فرض آن `false` است.
    - `code` {{optional_inline}}
      - : یک عدد صحیح که _کد بستن اتصال_ ارسال‌شده توسط سرور را نمایش می‌دهد. مقدار پیش‌فرض آن `0` است.
    - `reason` {{optional_inline}}
      - : رشته‌ای شامل دلیلی قابل‌فهم برای انسان که توصیف می‌کند چرا سرور اتصال را بسته است. مقدار پیش‌فرض آن `''` است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("CloseEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CloseEvent")}}، رابط (interface) شیءهایی که این سازنده می‌سازد.