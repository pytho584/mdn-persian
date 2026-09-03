---
title: "PageSwapEvent: PageSwapEvent() constructor"
---

---
title: "PageSwapEvent: PageSwapEvent() constructor"
short-title: PageSwapEvent()
slug: Web/API/PageSwapEvent/PageSwapEvent
page-type: web-api-constructor
browser-compat: api.PageSwapEvent.PageSwapEvent
---

{{APIRef("HTML DOM")}}

سازندهٔ **`PageSwapEvent()`** یک نمونهٔ جدید از شیء {{domxref("PageSwapEvent")}} می‌سازد.

## نحو

```js-nolint
new PageSwapEvent(type, init)
```

### پارامترها

- `type`
  - : رشته‌ای که نوع رویداد را نشان می‌دهد. در مورد `PageSwapEvent` این مقدار همیشه `pageswap` است.
- `init`
  - : شیءای شامل ویژگی‌های زیر:
    - `activation`
      - : یک شیء {{domxref("NavigationActivation")}} که نوع ناوبری و ورودی‌های تاریخچهٔ سند فعلی و مقصد را نشان می‌دهد. اگر ناوبری مرتبط یک ناوبری متقابل-مبدأ (cross-origin) باشد، پیش‌فرض آن `null` است.
    - `viewTransition`
      - : یک شیء {{domxref("ViewTransition")}} که انتقال نمای فعال برای ناوبری مرتبط را نشان می‌دهد. اگر انتقال نمای فعالی وجود نداشته باشد، پیش‌فرض آن `null` است.

## مثال‌ها

یک توسعه‌دهنده معمولاً این سازنده را به‌صورت دستی استفاده نمی‌کند. یک شیء جدید `PageSwapEvent` زمانی ساخته می‌شود که یک مدیریت‌کننده در نتیجهٔ رخ دادن رویداد {{domxref("Window.pageswap_event", "pageswap")}} فراخوانده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [View Transition API](/en-US/docs/Web/API/View_Transition_API)