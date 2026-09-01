---
title: "Element: pointerrawupdate event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Element/pointerrawupdate_event"
---

---
title: "Element: pointerrawupdate event"
short-title: pointerrawupdate
slug: Web/API/Element/pointerrawupdate_event
page-type: web-api-event
browser-compat: api.Element.pointerrawupdate_event
---

{{APIRef("Pointer Events")}}{{secureContext_header}}

رویداد **`pointerrawupdate`** زمانی فعال میشود که یک اشارهگر (pointer) هر ویژگی‌ای را تغییر دهد که رویدادهای {{domxref('Element/pointerdown_event', 'pointerdown')}} یا {{domxref('Element/pointerup_event', 'pointerup')}} را فعال نمی‌کند. برای فهرست این ویژگی‌ها به {{domxref('Element/pointermove_event', 'pointermove')}} مراجعه کنید.

رویداد `pointerrawupdate` ممکن است دارای رویدادهای ادغام‌شده (coalesced events) باشد، اگر از قبل رویداد `pointerrawupdate` دیگری با همان شناسه اشارهگر وجود داشته باشد که هنوز در حلقه رویداد (event loop) ارسال نشده است. برای اطلاعات درباره رویدادهای ادغام‌شده، مستندات {{domxref("PointerEvent.getCoalescedEvents()")}} را ببینید.

`pointerrawupdate` برای برنامه‌هایی در نظر گرفته شده است که به پردازش ورودی با دقت بالا نیاز دارند و نمی‌توانند با استفاده از رویدادهای ادغام‌شده [`pointermove`](/en-US/docs/Web/API/Element/pointermove_event) به تنهایی تعامل روانی را به دست آورند. با این حال، چون گوش دادن به رویدادهای `pointerrawupdate` می‌تواند بر عملکرد تأثیر بگذارد، باید این شنونده‌ها را تنها زمانی اضافه کنید که جاوااسکریپت شما به رویدادهای با فرکانس بالا نیاز دارد و می‌تواند آن‌ها را به همان سرعتی که ارسال می‌شوند پردازش کند. برای بیشتر موارد استفاده، سایر انواع رویدادهای اشارهگر کافی هستند.

این رویداد [حباب می‌زند](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و [ترکیب‌پذیر](/en-US/docs/Web/API/Event/composed) است، اما [قابل لغو](/en-US/docs/Web/API/Event/cancelable) نیست و هیچ اقدام پیش‌فرضی ندارد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pointerrawupdate", (event) => { })

onpointerrawupdate = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}} که از {{domxref("Event")}} به ارث رسیده است.

{{InheritanceDiagram("PointerEvent")}}

## مثال

```js
addEventListener("pointerrawupdate", (event) => {
  if (event.getCoalescedEvents && event.getCoalescedEvents().length > 1) {
    console.log("Coalesced events:", event.getCoalescedEvents().length);
    for (let coalescedEvent of event.getCoalescedEvents()) {
      // Do something with the coalesced events.
    }
  } else {
    // Do something with the event.
    console.log("Raw event", event);
  }
});
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
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}