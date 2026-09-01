```markdown
---
title: "Element: pointerenter event"
---

---
title: "Element: pointerenter event"
short-title: pointerenter
slug: Web/API/Element/pointerenter_event
page-type: web-api-event
browser-compat: api.Element.pointerenter_event
---

{{APIRef("Pointer Events")}}

رویداد `pointerenter` زمانی شلیک می‌شود که یک دستگاه اشاره‌گر به داخل مرزهای برخوردیابی یک عنصر یا یکی از فرزندان آن حرکت کند، از جمله در نتیجهٔ یک رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} از دستگاهی که از قابلیت hover پشتیبانی نمی‌کند (به {{domxref("Element/pointerdown_event", "pointerdown")}} مراجعه کنید). در غیر این صورت، `pointerenter` دقیقاً مانند {{domxref("Element/mouseenter_event", "mouseenter")}} عمل می‌کند و همزمان با آن ارسال می‌شود. همچنین این رویدادها در صورت لزوم همزمان با رویدادهای {{domxref("Element/mouseover_event", "mouseover")}} و {{domxref("Element/pointerover_event", "pointerover")}} ارسال می‌شوند.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pointerenter", (event) => { })

onpointerenter = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const para = document.querySelector("p");

para.addEventListener("pointerenter", (event) => {
  console.log("Pointer entered element");
});
```

استفاده از ویژگی مدیریت‌کننده رویداد `onpointerenter`:

```js
const para = document.querySelector("p");

para.onpointerenter = (event) => {
  console.log("Pointer entered element");
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
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}
  - {{domxref("Element/mouseenter_event", "mouseenter")}}
```