---
title: "Element: mousedown event"
slug: Web/API/Element/mousedown_event
page-type: web-api-event
browser-compat: api.Element.mousedown_event
---

{{APIRef("UI Events")}}

رویداد **`mousedown`** زمانی روی یک {{domxref("Element")}} فعال می‌شود که دکمه‌ای از دستگاه اشاره‌گر (مانند ماوس) در حالی که نشانگر داخل آن عنصر قرار دارد، فشرده شود.

این رویداد با رویداد {{domxref("Element/click_event", "click")}} تفاوت دارد؛ زیرا `click` پس از انجام کامل یک کلیک فعال می‌شود؛ یعنی دکمه ماوس فشرده و رها می‌شود در حالی که نشانگر همچنان داخل همان عنصر باقی مانده است. اما `mousedown` در همان لحظه‌ای که دکمه ابتدا فشرده می‌شود، فعال می‌گردد.

این رفتار با رویدادهای {{domxref("Element/pointerdown_event", "pointerdown")}} نیز متفاوت است. هنگام استفاده از ماوس فیزیکی، رویدادهای `mousedown` هر بار که هر دکمه‌ای از ماوس فشرده شود، فعال می‌شوند. اما رویدادهای `pointerdown` فقط با فشردن اولین دکمه فعال می‌شوند؛ فشردن دکمه‌های بعدی رویداد `pointerdown` را فعال نمی‌کند.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("mousedown", (event) => { })

onmousedown = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث برده است.

{{InheritanceDiagram("MouseEvent")}}

## مثال‌ها

برای کدهای نمونه، به [رویداد `mousemove`](/en-US/docs/Web/API/Element/mousemove_event#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [یادگیری: آشنایی با رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/mousemove_event", "mousemove")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mouseover_event", "mouseover")}}
- {{domxref("Element/mouseout_event", "mouseout")}}
- {{domxref("Element/mouseenter_event", "mouseenter")}}
- {{domxref("Element/mouseleave_event", "mouseleave")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/pointerdown_event", "pointerdown")}}