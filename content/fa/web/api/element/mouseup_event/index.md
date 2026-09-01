---
title: "Element: mouseup event"
short-title: mouseup
slug: Web/API/Element/mouseup_event
page-type: web-api-event
browser-compat: api.Element.mouseup_event
---

{{APIRef("UI Events")}}

رویداد **`mouseup`** روی یک {{domxref("Element")}} زمانی رخ می‌دهد که دکمه‌ای روی یک دستگاه اشاره‌گر (مانند ماوس یا ترک‌پد) در حالی که نشانگر داخل آن عنصر قرار دارد، رها شود.

رویدادهای `mouseup` در مقابل رویدادهای {{domxref("Element.mousedown_event", "mousedown")}} قرار می‌گیرند.

این رفتار با رویدادهای {{domxref("Element/pointerup_event", "pointerup")}} تفاوت دارد. هنگام استفاده از ماوس فیزیکی، رویدادهای `mouseup` هر زمان که هر دکمه‌ای روی ماوس رها شود، رخ می‌دهند. رویدادهای `pointerup` فقط با رها شدن آخرین دکمه فعال می‌شوند؛ رها شدن دکمه‌های قبلی، در حالی که دکمه‌های دیگر هنوز نگه داشته شده‌اند، رویداد `pointerup` را فعال نمی‌کنند.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده‌ی رویداد تنظیم کنید.

```js-nolint
addEventListener("mouseup", (event) => { })

onmouseup = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("MouseEvent")}}

## مثال‌ها

برای کد نمونه، به رویداد [`mousemove`](/en-US/docs/Web/API/Element/mousemove_event#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mousemove_event", "mousemove")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mouseover_event", "mouseover")}}
- {{domxref("Element/mouseout_event", "mouseout")}}
- {{domxref("Element/mouseenter_event", "mouseenter")}}
- {{domxref("Element/mouseleave_event", "mouseleave")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/pointerup_event", "pointerup")}}