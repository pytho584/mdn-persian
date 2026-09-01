---
title: "Element: pointerover event"
short-title: pointerover
slug: Web/API/Element/pointerover_event
page-type: web-api-event
browser-compat: api.Element.pointerover_event
---

{{APIRef("Pointer Events")}}

رویداد `pointerover` زمانی فعال می‌شود که یک ابزار اشاره‌گر به داخل مرزهای آزمایش برخورد (hit test) یک عنصر حرکت کند.

رویدادهای `pointerover` همان مشکلات {{domxref("Element/mouseover_event", "mouseover")}} را دارند. اگر عنصر هدف دارای عناصر فرزند باشد، رویدادهای `pointerout` و `pointerover` نیز هنگام حرکت اشاره‌گر روی مرزهای این عناصر فعال می‌شوند، نه فقط خود عنصر هدف. معمولاً رفتار رویدادهای {{domxref("Element/pointerenter_event", "pointerenter")}} و {{domxref("Element/pointerleave_event", "pointerleave")}} منطقی‌تر است، زیرا با ورود به عناصر فرزند تحت تأثیر قرار نمی‌گیرند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pointerover", (event) => { })

onpointerover = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. ارث‌بری از {{domxref("Event")}}.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

### استفاده از `addEventListener()`

```js
const para = document.querySelector("p");

para.addEventListener("pointerover", (event) => {
  console.log("Pointer moved in");
});
```

### استفاده از ویژگی کنترل‌کننده رویداد `onpointerover`

```js
const para = document.querySelector("p");

para.onpointerover = (event) => {
  console.log("Pointer moved in");
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط
  - {{domxref('Element/gotpointercapture_event', 'gotpointercapture')}}
  - {{domxref('Element/lostpointercapture_event', 'lostpointercapture')}}
  - {{domxref('Element/pointerenter_event', 'pointerenter')}}
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}
  - {{domxref("Element/mouseover_event", "mouseover")}}