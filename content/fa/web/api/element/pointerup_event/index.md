---
title: "Element: pointerup event"
---

---
title: "Element: pointerup event"
short-title: pointerup
slug: Web/API/Element/pointerup_event
page-type: web-api-event
browser-compat: api.Element.pointerup_event
---

{{APIRef("Pointer Events")}}

رویداد `pointerup` زمانی پرتاب می‌شود که یک اشاره‌گر دیگر فعال نباشد. به خاطر داشته باشید که ممکن است به‌جای آن رویداد [`pointercancel`](/en-US/docs/Web/API/Element/pointercancel_event) رخ دهد.

این رفتار با رویدادهای `mouseup` متفاوت است. هنگام استفاده از یک موس فیزیکی، رویدادهای `mouseup` هر بار که هر دکمه‌ای از موس رها شود، پرتاب می‌شوند. رویدادهای `pointerup` فقط پس از رها شدن آخرین دکمه پرتاب می‌شوند؛ رها شدن دکمه‌های قبلی، در حالی که سایر دکمه‌ها نگه داشته شده‌اند، رویداد `pointerup` را پرتاب نمی‌کنند.

## نحو

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("pointerup", (event) => { })

onpointerup = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}} که از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const para = document.querySelector("p");

para.addEventListener("pointerup", (event) => {
  console.log("Pointer up");
});
```

استفاده از ویژگی مدیریت رویداد `onpointerup`:

```js
const para = document.querySelector("p");

para.onpointerup = (event) => {
  console.log("Pointer up");
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
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}
  - {{domxref("Element/mouseup_event", "mouseup")}}