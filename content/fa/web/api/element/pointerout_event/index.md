---
title: "Element: pointerout event"
short-title: pointerout
slug: Web/API/Element/pointerout_event
page-type: web-api-event
browser-compat: api.Element.pointerout_event
---

{{APIRef("Pointer Events")}}

رویداد `pointerout` به دلایل متعددی شلیک می‌شود، از جمله وقتی که دستگاه اشاره‌گر از مرزهای _hit test_ (آزمون برخورد) یک عنصر خارج می‌شود؛ وقتی که رویداد {{domxref("Element/pointerup_event", "pointerup")}} برای دستگاهی که از حالت hover (نگه‌داشتن اشاره‌گر روی عنصر) پشتیبانی نمی‌کند شلیک می‌شود (به {{domxref("Element/pointerup_event", "pointerup")}} مراجعه کنید)؛ پس از شلیک رویداد {{domxref("Element/pointercancel_event", "pointercancel")}} (به {{domxref("Element/pointercancel_event", "pointercancel")}} مراجعه کنید)؛ و زمانی که قلم دیجیتال از محدودهٔ hover قابل تشخیص توسط دیجیتایزر خارج شود.

رویدادهای `pointerout` نیز همان مشکلات رویداد {{domxref("Element/mouseout_event", "mouseout")}} را دارند. اگر عنصر هدف دارای عناصر فرزند باشد، رویدادهای `pointerout` و `pointerover` هنگام حرکت اشاره‌گر روی مرزهای این عناصر نیز شلیک می‌شوند، نه فقط روی خود عنصر هدف. معمولاً رفتار رویدادهای {{domxref("Element/pointerenter_event", "pointerenter")}} و {{domxref("Element/pointerleave_event", "pointerleave")}} منطقی‌تر است، زیرا حرکت به داخل عناصر فرزند بر آن‌ها تأثیری نمی‌گذارد.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد را تنظیم کنید.

```js-nolint
addEventListener("pointerout", (event) => { })

onpointerout = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const para = document.querySelector("p");

para.addEventListener("pointerout", (event) => {
  console.log("Pointer moved out");
});
```

استفاده از ویژگی کنترل‌کنندهٔ رویداد `onpointerout`:

```js
const para = document.querySelector("p");

para.onpointerout = (event) => {
  console.log("Pointer moved out");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رویدادهای مرتبط
  - {{domxref('Element/gotpointercapture_event', 'gotpointercapture')}}
  - {{domxref('Element/lostpointercapture_event', 'lostpointercapture')}}
  - {{domxref('Element/pointerover_event', 'pointerover')}}
  - {{domxref('Element/pointerenter_event', 'pointerenter')}}
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}
  - {{domxref("Element/mouseout_event", "mouseout")}}