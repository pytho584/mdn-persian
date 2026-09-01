---
title: "Element: lostpointercapture event"
short-title: lostpointercapture
slug: Web/API/Element/lostpointercapture_event
page-type: web-api-event
browser-compat: api.Element.lostpointercapture_event
---

{{APIRef("Pointer Events")}}

رویداد **`lostpointercapture`** زمانی منتشر می‌شود که یک [اشاره‌گر ثبت‌شده](/en-US/docs/Web/API/Pointer_events#pointer_capture) آزاد می‌شود.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا به‌عنوان یک ویژگی کنترل‌کننده رویداد استفاده کنید.

```js-nolint
addEventListener("lostpointercapture", (event) => { })

onlostpointercapture = (event) => { }
```

## Event type

یک {{domxref("PointerEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("PointerEvent")}}

## Examples

این مثال رویداد `lostpointercapture` را برای یک عنصر گوش می‌دهد و در رویداد `pointerdown` اشاره‌گر را برای آن عنصر ثبت می‌کند. وقتی کاربر بعداً اشاره‌گر را رها کند، رویداد `lostpointercapture` منتشر می‌شود.

```js
const para = document.querySelector("p");

para.addEventListener("lostpointercapture", () => {
  console.log("I've been released!");
});

para.addEventListener("pointerdown", (event) => {
  para.setPointerCapture(event.pointerId);
});
```

همان مثال، اما با استفاده از ویژگی کنترل‌کننده رویداد `onlostpointercapture`:

```js
const para = document.querySelector("p");

para.onlostpointercapture = () => {
  console.log("I've been released!");
};

para.addEventListener("pointerdown", (event) => {
  para.setPointerCapture(event.pointerId);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رویدادهای مرتبط
  - {{domxref('Element/gotpointercapture_event', 'gotpointercapture')}}
  - {{domxref('Element/pointerover_event', 'pointerover')}}
  - {{domxref('Element/pointerenter_event', 'pointerenter')}}
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}