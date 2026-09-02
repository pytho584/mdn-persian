---
title: "InterestEvent: InterestEvent() constructor"
short-title: InterestEvent()
slug: Web/API/InterestEvent/InterestEvent
page-type: web-api-constructor
status:
  - experimental
  - non-standard
browser-compat: api.InterestEvent.InterestEvent
---

{{APIRef("Popover API")}}{{SeeCompatTable}}{{non-standard_header}}

سازندهٔ **`InterestEvent()`** یک شیء جدید از نوع {{domxref("InterestEvent")}} می‌سازد.

## نحو (Syntax)

```js-nolint
new InterestEvent(type, init)
```

### پارامترها

- `type`
  - : یک رشته (string) که نوع رویداد را مشخص می‌کند. برای `InterestEvent`، این مقدار همیشه `interest` یا `loseinterest` است.
- `init` {{optional_inline}}
  - : یک شیء که شامل ویژگی زیر است:
    - `source` {{optional_inline}}
      - : یک {{domxref("Element")}} که نشان‌دهندهٔ عنصر فراخوان‌کنندهٔ علاقه (interest invoker element) است که علاقه روی آن نشان داده یا از دست رفته است.

## مثال‌ها

به طور معمول، شما از این سازنده به صورت دستی استفاده نمی‌کنید. یک شیء جدید `InterestEvent` زمانی ساخته می‌شود که یک handler در نتیجهٔ فعال شدن یک رویداد مرتبط فراخوانی شود.

برای مثال‌ها، به راهنمای [استفاده از فراخوان‌کننده‌های علاقه (interest invokers)](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) و صفحهٔ مرجع رویداد {{domxref("HTMLElement.interest_event", "interest")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API Popover](/en-US/docs/Web/API/Popover_API)
- [استفاده از فراخوان‌کننده‌های علاقه (interest invokers)](/en-US/docs/Web/API/Popover_API/Using_interest_invokers)