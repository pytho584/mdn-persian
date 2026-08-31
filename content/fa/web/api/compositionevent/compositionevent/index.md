---
title: "CompositionEvent: CompositionEvent() constructor"
---

---
title: "CompositionEvent: CompositionEvent() constructor"
short-title: CompositionEvent()
slug: Web/API/CompositionEvent/CompositionEvent
page-type: web-api-constructor
browser-compat: api.CompositionEvent.CompositionEvent
---

{{APIRef("UI Events")}}

سازندهٔ **`CompositionEvent()`** یک شیء جدید از نوع {{domxref("CompositionEvent")}} ایجاد می‌کند.

## نحو

```js-nolint
new CompositionEvent(type)
new CompositionEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای (string) شامل نام رویداد.
    این مقدار به حروف بزرگ و کوچک حساس است (case-sensitive) و مرورگرها آن را روی `compositionstart`، `compositionupdate` یا `compositionend` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : شیئی که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("UIEvent/UIEvent", "UIEvent()")}}_، ویژگی‌های زیر را دارد:
    - `data` {{optional_inline}}
      - : رشته‌ای که برای مقداردهی اولیهٔ ویژگی {{domxref("CompositionEvent.data", "data")}} در {{domxref("CompositionEvent")}} جدید استفاده می‌شود. در رویدادهای تولیدشده توسط مرورگر، این مقدار روی نویسه‌هایی تنظیم می‌شود که از ترکیب IME حاصل شده‌اند.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("CompositionEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CompositionEvent")}}، واسط اشیائی که این سازنده می‌سازد.