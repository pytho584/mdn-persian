---
title: "Element: touchmove event"
short-title: touchmove
slug: Web/API/Element/touchmove_event
page-type: web-api-event
browser-compat: api.Element.touchmove_event
---

{{APIRef("Touch Events")}}

رویداد `touchmove` زمانی شلیک می‌شود که یک یا چند نقطهٔ لمس (touch point) در امتداد سطح لمس حرکت کنند.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("touchmove", (event) => { })

ontouchmove = (event) => { }
```

## نوع رویداد

یک {{domxref("TouchEvent")}} که از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("TouchEvent")}}

## مثال‌ها

نمونه‌کدهای مربوط به این رویدادها در صفحهٔ اختصاصی [رویدادهای لمس (Touch events)](/en-US/docs/Web/API/Touch_events) در دسترس هستند.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [رویدادهای لمس (Touch events)](/en-US/docs/Web/API/Touch_events)
- {{domxref("Element/mousemove_event", "mousemove")}}