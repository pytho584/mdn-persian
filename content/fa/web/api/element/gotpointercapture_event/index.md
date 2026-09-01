---
title: "Element: gotpointercapture event"
short-title: gotpointercapture
slug: Web/API/Element/gotpointercapture_event
page-type: web-api-event
browser-compat: api.Element.gotpointercapture_event
---

{{APIRef("Pointer Events")}}

رویداد **`gotpointercapture`** زمانی رخ می‌دهد که یک عنصر، اشاره‌گر (pointer) را با استفاده از [`setPointerCapture()`](/en-US/docs/Web/API/Element/setPointerCapture) در اختیار می‌گیرد.

## نحو (Syntax)

برای استفاده از نام رویداد می‌توانید از روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("gotpointercapture", (event) => { })

ongotpointercapture = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

در این مثال، یک عنصر `<p>` گرفته می‌شود و رویداد `gotpointercapture` گوش داده می‌شود. سپس در رویداد `pointerdown` متد `setPointerCapture()` روی آن عنصر فراخوانی می‌شود که باعث فعال شدن `gotpointercapture` می‌گردد.

```js
const para = document.querySelector("p");

para.addEventListener("gotpointercapture", () => {
  console.log("من گرفته شدم!");
});

para.addEventListener("pointerdown", (event) => {
  para.setPointerCapture(event.pointerId);
});
```

همان مثال، با استفاده از ویژگی مدیریت‌کننده رویداد `ongotpointercapture`:

```js
const para = document.querySelector("p");

para.ongotpointercapture = () => {
  console.log("من گرفته شدم!");
};

para.addEventListener("pointerdown", (event) => {
  para.setPointerCapture(event.pointerId);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط
  - {{domxref('Element/lostpointercapture_event', 'lostpointercapture')}}
  - {{domxref('Element/pointerover_event', 'pointerover')}}
  - {{domxref('Element/pointerenter_event', 'pointerenter')}}
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}