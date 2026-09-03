---
title: "PageTransitionEvent: PageTransitionEvent() سازنده"
slug: Web/API/PageTransitionEvent/PageTransitionEvent
page-type: web-api-constructor
browser-compat: api.PageTransitionEvent.PageTransitionEvent
---

{{APIRef("HTML DOM")}}

سازنده **`PageTransitionEvent()`** یک شیء جدید از نوع {{domxref("PageTransitionEvent")}} ایجاد می‌کند که توسط رویدادهای {{domxref("Window/pageshow_event", "pageshow")}} یا {{domxref("Window/pagehide_event", "pagehide")}} استفاده می‌شود. این رویدادها در شیء {{domxref("window")}} هنگام بارگذاری یا بارگیری‌نشدن یک صفحه رخ می‌دهند.

> [!NOTE]
> توسعه‌دهندگان وب معمولاً نیازی به فراخوانی این سازنده ندارند، زیرا مرورگر این اشیاء را هنگام فعال‌سازی رویدادهای {{domxref("Window/pageshow_event", "pageshow")}} یا {{domxref("Window/pagehide_event", "pagehide")}} به‌طور خودکار ایجاد می‌کند.

## نحو

```js-nolint
new PageTransitionEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نام رویداد را مشخص می‌کند.
    این مقدار به بزرگی/کوچکی حروف حساس است و مرورگر آن را به `pageshow` یا `pagehide` تنظیم می‌کند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، دارای ویژگی زیر است:
    - `persisted` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد آیا سند از حافظه پنهان (cache) بارگذاری شده است یا خیر.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("PageTransitionEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`pageshow`](/en-US/docs/Web/API/Window/pageshow_event)
- رویداد [`pagehide`](/en-US/docs/Web/API/Window/pagehide_event)