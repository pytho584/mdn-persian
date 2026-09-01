---
title: "Element: pointerleave event"
short-title: pointerleave
slug: Web/API/Element/pointerleave_event
page-type: web-api-event
browser-compat: api.Element.pointerleave_event
---

{{APIRef("Pointer Events")}}

رویداد `pointerleave` زمانی به‌کار می‌افتد که دستگاه اشاره‌گر از مرزهای hit test یک عنصر خارج شود. برای دستگاه‌های قلمی، این رویداد زمانی رخ می‌دهد که قلم از محدودهٔ hover قابل تشخیص توسط digitizer خارج شود. در غیر این صورت، رفتار `pointerleave` مانند {{domxref("Element/mouseleave_event", "mouseleave")}} است و هم‌زمان با آن ارسال می‌شود. همچنین در صورت لزوم، هم‌زمان با رویدادهای {{domxref("Element/mouseout_event", "mouseout")}} و {{domxref("Element/pointerout_event", "pointerout")}} نیز ارسال می‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی رویدادگردان (event handler property) تنظیم کنید.

```js-nolint
addEventListener("pointerleave", (event) => { })

onpointerleave = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. به‌ارث‌برده شده از {{domxref("Event")}}.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const para = document.querySelector("p");

para.addEventListener("pointerleave", (event) => {
  console.log("Pointer left element");
});
```

استفاده از ویژگی رویدادگردان `onpointerleave`:

```js
const para = document.querySelector("p");

para.onpointerleave = (event) => {
  console.log("Pointer left element");
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
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}
  - {{domxref("Element/mouseleave_event", "mouseleave")}}