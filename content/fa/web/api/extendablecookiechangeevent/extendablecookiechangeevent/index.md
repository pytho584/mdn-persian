---
title: "ExtendableCookieChangeEvent: ExtendableCookieChangeEvent() constructor"
short-title: ExtendableCookieChangeEvent()
slug: Web/API/ExtendableCookieChangeEvent/ExtendableCookieChangeEvent
page-type: web-api-constructor
browser-compat: api.ExtendableCookieChangeEvent.ExtendableCookieChangeEvent
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("service")}}

سازندهٔ **`ExtendableCookieChangeEvent()`** یک شیء جدید از نوع {{domxref("ExtendableCookieChangeEvent")}} می‌سازد. این نوع رویداد، همان رویدادی است که به {{domxref("ServiceWorkerGlobalScope/cookiechange_event", "cookiechange")}} ارسال می‌شود؛ رویدادی که در {{domputed("ServiceWorkerGlobalScope")}} هنگام تغییر هر کوکی‌ای که با فهرست اشتراک تغییر کوکی سرویس‌کارگر مطابقت دارد، رخ می‌دهد. این سازنده توسط مرورگر هنگام وقوع یک تغییر فراخوانی می‌شود.

> [!NOTE]
> به‌طور کلی، این سازندهٔ رویداد برای وب‌سایت‌های تولیدی مورد نیاز نیست. کاربرد اصلی آن در تست‌هایی است که به یک نمونه از این رویداد نیاز دارند.

## نحو (Syntax)

```js-nolint
new ExtendableCookieChangeEvent(type)
new ExtendableCookieChangeEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته شامل نام رویداد. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را به `cookiechange` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}_، می‌تواند دارای ویژگی‌های زیر باشد:
    - `changed` {{optional_inline}}
      - : آرایه‌ای شامل یک کوکی تغییر یافته.
    - `deleted` {{optional_inline}}
      - : آرایه‌ای شامل یک کوکی حذف شده.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("ExtendableCookieChangeEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}