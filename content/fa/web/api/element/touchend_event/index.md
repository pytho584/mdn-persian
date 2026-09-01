---
title: "Element: touchend event"
short-title: touchend
slug: Web/API/Element/touchend_event
page-type: web-api-event
browser-compat: api.Element.touchend_event
---

{{APIRef("Touch Events")}}

رویداد `touchend` زمانی رخ می‌دهد که یک یا چند نقطهٔ لمس از سطح لمس حذف شوند. به یاد داشته باشید که به جای آن ممکن است رویداد [`touchcancel`](/en-US/docs/Web/API/Element/touchcancel_event) رخ دهد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("touchend", (event) => { })

ontouchend = (event) => { }
```

## نوع رویداد

یک {{domxref("TouchEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("TouchEvent")}}

## مثال‌ها

نمونه‌کدهای این رویدادها در صفحهٔ اختصاصی [رویدادهای لمس](/en-US/docs/Web/API/Touch_events) در دسترس هستند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویدادهای لمس](/en-US/docs/Web/API/Touch_events)