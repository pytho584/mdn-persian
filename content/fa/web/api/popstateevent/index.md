---
title: "PopStateEvent"
---

---
title: PopStateEvent
slug: Web/API/PopStateEvent
page-type: web-api-interface
browser-compat: api.PopStateEvent
---

{{APIRef("History API")}}

**`PopStateEvent`** رابطی برای رویداد {{domxref("Window/popstate_event", "popstate")}} است.

رویداد `popstate` هر بار به پنجره ارسال می‌شود که مدخل فعلی تاریخچه (active history entry) بین دو مدخل متعلق به یک سند تغییر کند. اگر مدخل تاریخچه‌ای که فعال می‌شود با فراخوانی `history.pushState()` ساخته شده باشد یا تحت تأثیر فراخوانی `history.replaceState()` قرار گرفته باشد، ویژگی `state` رویداد `popstate` حاوی یک کپی از شیء حالتِ همان مدخل تاریخچه خواهد بود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PopStateEvent.PopStateEvent", "PopStateEvent()")}}
  - : یک شیء `PopStateEvent` جدید می‌سازد.

## ویژگی‌های نمونه

_این رابط، ویژگی‌های والد خود، {{domxref("Event")}} را نیز به ارث می‌برد._

- {{domxref("PopStateEvent.state")}} {{ReadOnlyInline}}
  - : یک کپی از اطلاعات ارائه‌شده به `pushState()` یا `replaceState()` را بازمی‌گرداند.
- {{domxref("PopStateEvent.hasUAVisualTransition", "hasUAVisualTransition")}} {{ReadOnlyInline}}
  - : اگر عامل کاربر (user agent) پیش از ارسال این رویداد، یک انتقال بصری برای این ناوبری انجام داده باشد، `true` و در غیر این صورت `false` بازمی‌گرداند.

## روش‌های نمونه

_این رابط هیچ روشی از خود ندارد، اما روش‌های والد خود، {{domxref("Event")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`popstate`](/en-US/docs/Web/API/Window/popstate_event)
- رویداد [`hashchange`](/en-US/docs/Web/API/Window/hashchange_event)