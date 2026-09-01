---
title: "ErrorEvent: ErrorEvent() constructor"
short-title: ErrorEvent()
slug: Web/API/ErrorEvent/ErrorEvent
page-type: web-api-constructor
browser-compat: api.ErrorEvent.ErrorEvent
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

سازندهی **`ErrorEvent()`** یک شیء جدید {{domxref("ErrorEvent")}} می‌سازد.

## سینتکس

```js-nolint
new ErrorEvent(type)
new ErrorEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. این مقدار به بزرگی و کوچکی حروف حساس است.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `message` {{optional_inline}}
      - : رشته‌ای شامل پیام خطای قابل‌خواندن برای انسان که مشکل را توصیف می‌کند.
    - `filename` {{optional_inline}}
      - : رشته‌ای شامل نام فایل اسکریپتی که خطا در آن رخ داده است.
    - `lineno` {{optional_inline}}
      - : یک عدد صحیح شامل شماره خط فایل اسکریپتی که خطا در آن رخ داده است.
    - `colno` {{optional_inline}}
      - : یک عدد صحیح شامل شماره ستون فایل اسکریپتی که خطا در آن رخ داده است.
    - `error` {{optional_inline}}
      - : یک مقدار جاوااسکریپت، مانند {{jsxref("Error")}} یا {{domxref("DOMException")}}، که خطای مرتبط با این رویداد را نشان می‌دهد.

### مقدار بازگشتی

یک شیء جدید {{domxref("ErrorEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
