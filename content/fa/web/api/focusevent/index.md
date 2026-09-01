---
title: FocusEvent
slug: Web/API/FocusEvent
page-type: web-api-interface
browser-compat: api.FocusEvent
---

{{APIRef("UI Events")}}

رابط **`FocusEvent`** رویدادهای مرتبط با تمرکز (focus) را نشان می‌دهد، از جمله {{domxref("Element/focus_event", "focus")}}، {{domxref("Element/blur_event", "blur")}}، {{domxref("Element/focusin_event", "focusin")}} و {{domxref("Element/focusout_event", "focusout")}}.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("FocusEvent.FocusEvent", "FocusEvent()")}}
  - : یک رویداد `FocusEvent` با پارامترهای داده شده ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

_این رابط همچنین ویژگی‌های والد خود {{domxref("UIEvent")}} و به طور غیرمستقیم {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("FocusEvent.relatedTarget")}}
  - : یک {{domxref("EventTarget")}} که هدف ثانویه این رویداد را نشان می‌دهد. در برخی موارد (مانند زمانی که با کلید Tab وارد صفحه می‌شوید یا از آن خارج می‌شوید)، این ویژگی ممکن است به دلایل امنیتی `null` باشد.

## روش‌های نمونه (Instance methods)

_این رابط روش خاصی ندارد. روش‌های والد خود {{domxref("UIEvent")}} و به طور غیرمستقیم {{domxref("Event")}} را به ارث می‌برد._

## ترتیب رویدادها

هنگامی که تمرکز از عنصر A به عنصر B منتقل می‌شود، رویدادهای تمرکز به ترتیب زیر صادر می‌شوند:

1. `blur`: پس از اینکه عنصر A تمرکز خود را از دست می‌دهد، ارسال می‌شود.
2. `focusout`: پس از رویداد `blur` ارسال می‌شود.
3. `focus`: پس از اینکه عنصر B تمرکز دریافت می‌کند، ارسال می‌شود.
4. `focusin`: پس از رویداد `focus` ارسال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رابط پایه {{domxref("Event")}}