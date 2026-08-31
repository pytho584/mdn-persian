---
title: "CompositionEvent"
---

---
title: CompositionEvent
slug: Web/API/CompositionEvent
page-type: web-api-interface
browser-compat: api.CompositionEvent
---

{{APIRef("UI Events")}}

**`CompositionEvent`** در DOM رویدادهایی را نمایش میدهد که در نتیجهی ورود غیرمستقیم متن توسط کاربر رخ میدهند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CompositionEvent.CompositionEvent()", "CompositionEvent()")}}
  - : یک نمونهی جدید از شیء `CompositionEvent` ایجاد میکند.

## ویژگیهای نمونه

_این رابط همچنین ویژگیهای والد خود، {{domxref("UIEvent")}}، و نیای آن — {{domxref("Event")}} — را به ارث میبرد._

- {{domxref("CompositionEvent.data")}} {{ReadOnlyInline}}
  - : نویسههایی را برمیگرداند که توسط روش ورودیِ ایجادکنندهی رویداد تولید شدهاند؛ این مقدار بسته به نوع رویدادی که شیء `CompositionEvent` را ایجاد کرده است، متفاوت است.
- {{domxref("CompositionEvent.locale")}} {{ReadOnlyInline}} {{deprecated_inline}} {{Non-standard_Inline}}
  - : منطقهی (locale) روش ورودی فعلی را برمیگرداند (برای مثال، منطقهی چیدمان صفحهکلید اگر ترکیب با یک {{glossary("Input method editor")}} مرتبط باشد).

## روشهای نمونه

_این رابط همچنین روشهای والد خود، {{domxref("UIEvent")}}، و نیای آن — {{domxref("Event")}} — را به ارث میبرد._

- {{domxref("CompositionEvent.initCompositionEvent()")}} {{deprecated_inline}}
  - : ویژگیهای یک شیء `CompositionEvent` را مقداردهی اولیه میکند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [compositionstart](/en-US/docs/Web/API/Element/compositionstart_event)
- [compositionend](/en-US/docs/Web/API/Element/compositionend_event)
- [compositionupdate](/en-US/docs/Web/API/Element/compositionupdate_event)
- [UIEvent](/en-US/docs/Web/API/UIEvent)
- [Event](/en-US/docs/Web/API/Event)