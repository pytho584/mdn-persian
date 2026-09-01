---
title: "GestureEvent"
---

---
title: GestureEvent
slug: Web/API/GestureEvent
page-type: web-api-interface
status:
  - non-standard
browser-compat: api.GestureEvent
---

{{APIRef("UI Events")}}{{Non-standard_header}}

**`GestureEvent`** یک رابط اختصاصی مخصوص WebKit است که اطلاعات مربوط به ژست‌های لمسی چندلمسی را فراهم می‌کند. رویدادهایی که از این رابط استفاده می‌کنند عبارت‌اند از {{domxref("Element/gesturestart_event", "gesturestart")}}، {{domxref("Element/gesturechange_event", "gesturechange")}} و {{domxref("Element/gestureend_event", "gestureend")}}.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های والدهای خود، {{domxref("UIEvent")}} و {{domxref("Event")}}، را به ارث می‌برد._

- {{domxref("GestureEvent.rotation")}} {{ReadOnlyInline}} {{Non-standard_Inline}}
  - : تغییر چرخش (بر حسب درجه) از آغاز رویداد. مقادیر مثبت نشان‌دهنده چرخش در جهت عقربه‌های ساعت و مقادیر منفی نشان‌دهنده چرخش در خلاف جهت عقربه‌های ساعت هستند. مقدار اولیه: `0.0`.
- {{domxref("GestureEvent.scale")}} {{ReadOnlyInline}} {{Non-standard_Inline}}
  - : فاصله بین دو انگشت از آغاز رویداد. این مقدار به‌صورت یک مضرب اعشاری از فاصله اولیه بین انگشت‌ها در آغاز ژست بیان می‌شود. مقادیر کمتر از `1.0` نشان‌دهنده نیشگون گرفتن به سمت داخل (کوچک‌نمایی) هستند. مقادیر بیشتر از `1.0` نشان‌دهنده باز کردن نیشگون به سمت خارج (بزرگ‌نمایی) هستند. مقدار اولیه: `1.0`.

## متدهای نمونه

_این رابط همچنین متدهای والدهای خود، {{domxref("UIEvent")}} و {{domxref("Event")}}، را به ارث می‌برد._

- {{domxref("GestureEvent.initGestureEvent()")}} {{Non-standard_Inline}}
  - : مقدار یک `GestureEvent` را مقداردهی اولیه می‌کند. اگر رویداد قبلاً ارسال شده باشد، این متد هیچ کاری انجام نمی‌دهد.

## انواع رویداد ژست

- {{domxref("Element/gesturestart_event", "gesturestart")}}
- {{domxref("Element/gesturechange_event", "gesturechange")}}
- {{domxref("Element/gestureend_event", "gestureend")}}

## مشخصات

_هیچ بخشی از هیچ مشخصه‌ای نیست._ اپل [توضیحی در کتابخانه توسعه‌دهندگان Safari](https://developer.apple.com/documentation/webkitjs/gestureevent) دارد.

## سازگاری مرورگر

{{Compat}}