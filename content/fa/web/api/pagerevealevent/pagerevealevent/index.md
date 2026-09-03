---
title: "PageRevealEvent: PageRevealEvent() constructor"
short-title: PageRevealEvent()
slug: Web/API/PageRevealEvent/PageRevealEvent
page-type: web-api-constructor
browser-compat: api.PageRevealEvent.PageRevealEvent
---

{{APIRef("HTML DOM")}}

سازندهٔ **`PageRevealEvent()`** یک نمونهٔ جدید از شیء {{domxref("PageRevealEvent")}} می‌سازد.

## نحو (Syntax)

```js-nolint
new PageRevealEvent(type, init)
```

### پارامترها

- `type`
  - : رشته‌ای که نوع رویداد را نشان می‌دهد. در مورد `PageRevealEvent` این مقدار همیشه `pagereveal` است.
- `init`
  - : شیءایی شامل ویژگی‌های زیر:
    - `viewTransition` {{optional_inline}}
      - : یک شیء {{domxref("ViewTransition")}} که نمایانگر گذار نمای فعال برای ناوبری مرتبط است. اگر گذار نمای فعالی وجود نداشته باشد، مقدار پیش‌فرض آن `null` است.

## مثال‌ها

توسعه‌دهنده معمولاً از این سازنده به صورت دستی استفاده نمی‌کند. یک شیء جدید `PageRevealEvent` هنگام فراخوانی یک handler در نتیجهٔ پرتاب رویداد {{domxref("Window.pagereveal_event", "pagereveal")}} ساخته می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [View Transition API](/en-US/docs/Web/API/View_Transition_API)