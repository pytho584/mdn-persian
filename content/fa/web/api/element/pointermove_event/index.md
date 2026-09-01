---
title: "Element: pointermove event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Element/pointermove_event"
---

---
title: "Element: pointermove event"
short-title: pointermove
slug: Web/API/Element/pointermove_event
page-type: web-api-event
browser-compat: api.Element.pointermove_event
---

{{APIRef("Pointer Events")}}

رویداد `pointermove` زمانی رخ می‌دهد که مختصات یک اشاره‌گر تغییر کند و اشاره‌گر توسط [touch-action](/en-US/docs/Web/CSS/Reference/Properties/touch-action) مرورگر [لغو](/en-US/docs/Web/API/Element/pointercancel_event) نشده باشد. این رویداد شباهت زیادی به رویداد {{domxref("Element/mousemove_event", "mousemove")}} دارد، با این تفاوت که امکانات بیشتری را فراهم می‌کند.

این رویدادها صرف‌نظر از فشرده بودن یا نبودن دکمه‌های اشاره‌گر رخ می‌دهند. ممکن است با نرخ بسیار بالایی رخ دهند که این نرخ به سرعت حرکت اشاره‌گر توسط کاربر، سرعت دستگاه، سایر وظایف و فرآیندهای در حال اجرا و موارد دیگر بستگی دارد.

## Syntax

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا آن را به عنوان یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pointermove", (event) => { })

onpointermove = (event) => { }
```

## Event type

یک {{domxref("PointerEvent")}} که از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("PointerEvent")}}

## Usage notes

این رویداد که از نوع {{domxref("PointerEvent")}} است، تمام اطلاعات مورد نیاز شما درباره تعامل کاربر با دستگاه اشاره‌گر را فراهم می‌کند؛ از جمله موقعیت، فاصله حرکت، وضعیت دکمه‌ها و موارد بسیار دیگر.

## Examples

برای افزودن یک کنترل‌کننده به رویدادهای `pointermove` با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}}:

```js
const para = document.querySelector("p");

para.addEventListener("pointermove", (event) => {
  console.log("Pointer moved");
});
```

همچنین می‌توانید از ویژگی کنترل‌کننده رویداد `onpointermove` استفاده کنید:

```js
const para = document.querySelector("p");

para.onpointermove = (event) => {
  console.log("Pointer moved");
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رویدادهای مرتبط
  - {{domxref('Element/gotpointercapture_event', 'gotpointercapture')}}
  - {{domxref('Element/lostpointercapture_event', 'lostpointercapture')}}
  - {{domxref('Element/pointerover_event', 'pointerover')}}
  - {{domxref('Element/pointerenter_event', 'pointerenter')}}
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointercancel_event', 'pointercancel')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}
  - {{domxref("Element/mousemove_event", "mousemove")}}