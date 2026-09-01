---
title: "Element: pointerdown event"
short-title: pointerdown
slug: Web/API/Element/pointerdown_event
page-type: web-api-event
browser-compat: api.Element.pointerdown_event
---

{{APIRef("Pointer Events")}}

رویداد `pointerdown` زمانی پرتاب می‌شود که یک اشاره‌گر (pointer) فعال شود. برای ماوس، زمانی پرتاب می‌شود که دستگاه از حالتی که هیچ دکمه‌ای فشرده نیست به حالتی که حداقل یک دکمه فشرده شده است تغییر وضعیت دهد. برای لمس، زمانی پرتاب می‌شود که تماس فیزیکی با دیجیتایزر برقرار شود. برای قلم، زمانی پرتاب می‌شود که stylus با دیجیتایزر تماس فیزیکی برقرار کند.

این رفتار با رویدادهای {{domxref("Element/mousedown_event", "mousedown")}} متفاوت است. هنگام استفاده از ماوس فیزیکی، رویدادهای `mousedown` هر بار که هر دکمه‌ای روی ماوس فشرده شود پرتاب می‌شوند. رویدادهای `pointerdown` فقط با فشردن اولین دکمه پرتاب می‌شوند؛ فشردن دکمه‌های بعدی رویدادهای `pointerdown` را پرتاب نمی‌کنند.

> [!NOTE]
> برای مرورگرهای لمسی که [دستکاری مستقیم](https://w3c.github.io/pointerevents/#dfn-direct-manipulation) را مجاز می‌دانند، یک رویداد `pointerdown` [تسخیر ضمنی اشاره‌گر](https://w3c.github.io/pointerevents/#dfn-implicit-pointer-capture) را فعال می‌کند، که باعث می‌شود هدف، همه رویدادهای اشاره‌گر بعدی را طوری ضبط کند که گویی در بالای هدف تسخیرکننده رخ می‌دهند. بنابراین، تا زمانی که این تسخیر فعال باشد، `pointerover`، `pointerenter`، `pointerleave` و `pointerout` **پرتاب نخواهند شد**. این تسخیر می‌تواند به صورت دستی با فراخوانی {{domxref('element.releasePointerCapture')}} روی عنصر هدف آزاد شود، یا به صورت ضمنی پس از یک رویداد `pointerup` یا `pointercancel` آزاد خواهد شد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pointerdown", (event) => { })

onpointerdown = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const para = document.querySelector("p");

para.addEventListener("pointerdown", (event) => {
  console.log("Pointer down event");
});
```

استفاده از ویژگی کنترل‌کننده رویداد `onpointerdown`:

```js
const para = document.querySelector("p");

para.onpointerdown = (event) => {
  console.log("Pointer down event");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط
  - {{domxref('Element/gotpointercapture_event', 'gotpointercapture')}}
  - {{domxref('Element/lostpointercapture_event', 'lostpointercapture')}}
  - {{domxref('Element/pointerover_event', 'pointerover')}}
  - {{domxref('Element/pointerenter_event', 'pointerenter')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}
  - {{domxref("Element/mousedown_event", "mousedown")}}