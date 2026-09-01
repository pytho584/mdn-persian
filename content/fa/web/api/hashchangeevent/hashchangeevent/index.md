---
title: "HashChangeEvent: HashChangeEvent() constructor"
---

---
title: "HashChangeEvent: HashChangeEvent() constructor"
short-title: HashChangeEvent()
slug: Web/API/HashChangeEvent/HashChangeEvent
page-type: web-api-constructor
browser-compat: api.HashChangeEvent.HashChangeEvent
---

{{APIRef("HTML DOM")}}

سازندهٔ **`HashChangeEvent()`** یک شیء جدید {{domxref("HashChangeEvent")}} می‌سازد که توسط رویداد {{domxref("Window/hashchange_event", "hashchange")}} استفاده می‌شود. این رویداد روی شیء {{domxref("window")}} زمانی که بخشِ fragment (قطعه) از URL تغییر می‌کند، شلیک می‌شود.

> [!NOTE]
> معمولاً توسعه‌دهندهٔ وب نیازی به فراخوانی این سازنده ندارد، زیرا مرورگر هنگام شلیک رویدادهای {{domxref("Window/hashchange_event", "hashchange")}} خودش این اشیاء را می‌سازد.

## دستور زبان

```js-nolint
new HashChangeEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. این مقدار به بزرگی/کوچکی حروف حساس است و مرورگرها آن را روی `hashchange` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، ویژگی‌های زیر را دارد:
    - `oldURL` {{optional_inline}}
      - : رشته‌ای شامل URL قبلی. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.
    - `newURL` {{optional_inline}}
      - : رشته‌ای شامل URL جدید. مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.

### مقدار بازگشتی

یک شیء جدید {{domxref("HashChangeEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Window/hashchange_event", "hashchange")}}