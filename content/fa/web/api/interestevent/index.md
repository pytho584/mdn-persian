---
title: InterestEvent
slug: Web/API/InterestEvent
page-type: web-api-interface
status:
  - experimental
  - non-standard
browser-compat: api.InterestEvent
---

{{APIRef("Popover API")}}{{SeeCompatTable}}{{non-standard_header}}

رابطِ **`InterestEvent`** رویدادی را بازنمایی می‌کند که وقتی به یک [interest invoker](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) علاقه نشان داده می‌شود یا از بین می‌رود، رخ می‌دهد.

این، شیء رویداد برای رویدادهای {{domxref("HTMLElement.interest_event", "interest")}} و {{domxref("HTMLElement.loseinterest_event", "loseinterest")}} است که به‌ترتیب زمانی روی عنصر هدف رخ می‌دهند که علاقه نشان داده می‌شود یا از بین می‌رود.

{{InheritanceDiagram}}

## سازنده

- {{DOMxRef("InterestEvent.InterestEvent", "InterestEvent()")}} {{experimental_inline}} {{non-standard_inline}}
  - یک شیء `InterestEvent` می‌سازد.

## ویژگی‌های نمونه

_این رابط ویژگی‌ها را از والد خود، {{DOMxRef("Event")}}، به ارث می‌برد._

- {{DOMxRef("InterestEvent.source")}} {{ReadOnlyInline}} {{experimental_inline}} {{non-standard_inline}}
  - نمونه‌ای از {{domxref("Element")}} که نشان‌دهندهٔ عنصر interest invoker است؛ عنصری که با نشان دادن علاقه به آن یا از بین رفتن علاقه نسبت به آن، رویداد رخ داده است.

## مثال‌ها

برای مثال‌ها، راهنمای [استفاده از فراخواننده‌های علاقه (interest invokers)](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) و صفحهٔ مرجع رویداد {{domxref("HTMLElement.interest_event", "interest")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Popover API](/en-US/docs/Web/API/Popover_API)
- [استفاده از فراخواننده‌های علاقه (interest invokers)](/en-US/docs/Web/API/Popover_API/Using_interest_invokers)