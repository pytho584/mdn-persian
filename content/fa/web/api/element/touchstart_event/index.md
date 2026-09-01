---
title: "Element: touchstart event"
short-title: touchstart
slug: Web/API/Element/touchstart_event
page-type: web-api-event
browser-compat: api.Element.touchstart_event
---

{{APIRef("Touch Events")}}

رویداد `touchstart` زمانی فعال می‌شود که یک یا چند نقطهٔ لمسی روی سطح لمسی قرار می‌گیرند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("touchstart", (event) => { })

ontouchstart = (event) => { }
```

## نوع رویداد

یک {{domxref("TouchEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("TouchEvent")}}

## مثال‌ها

نمونه‌کدهای مربوط به این رویدادها در صفحهٔ اختصاصی [Touch events](/en-US/docs/Web/API/Touch_events) موجود است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Touch events](/en-US/docs/Web/API/Touch_events) (رویدادهای لمسی)