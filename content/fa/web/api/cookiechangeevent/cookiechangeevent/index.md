---
title: "CookieChangeEvent: CookieChangeEvent() constructor"
short-title: CookieChangeEvent()
slug: Web/API/CookieChangeEvent/CookieChangeEvent
page-type: web-api-constructor
browser-compat: api.CookieChangeEvent.CookieChangeEvent
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}

سازندهٔ **`CookieChangeEvent()`** یک شیء جدید از نوع {{domxref("CookieChangeEvent")}} می‌سازد.
این شیء نوع رویداد {{domxref("CookieStore/change_event", "change")}} است که هنگام هر تغییری در کوکی‌ها، روی یک {{domxref("CookieStore")}} فراخوانی می‌شود.
این سازنده توسط مرورگر هنگام وقوع یک رویداد تغییر فراخوانی می‌شود.

> [!NOTE]
> این سازندهٔ رویداد معمولاً برای وب‌سایت‌های تولیدی لازم نیست. کاربرد اصلی آن در تست‌هایی است که به نمونه‌ای از این رویداد نیاز دارند.

## نحو (Syntax)

```js-nolint
new CookieChangeEvent(type)
new CookieChangeEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نام رویداد را مشخص می‌کند. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را روی `change` قرار می‌دهند.
- `options` {{Optional_Inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `changed` {{Optional_Inline}}
      - : آرایه‌ای شامل کوکی‌های تغییر یافته.
    - `deleted` {{Optional_Inline}}
      - : آرایه‌ای شامل کوکی‌های حذف‌شده.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("CookieChangeEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}