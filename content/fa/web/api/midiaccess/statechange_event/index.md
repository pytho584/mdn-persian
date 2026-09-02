---
title: "MIDIAccess: statechange event"
short-title: statechange
slug: Web/API/MIDIAccess/statechange_event
page-type: web-api-event
browser-compat: api.MIDIAccess.statechange_event
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

رویداد **`statechange`** از رابط {{domxref("MIDIAccess")}} زمانی که یک پورت MIDI جدید اضافه میشود یا یک پورت موجود تغییر وضعیت میدهد، فعال میشود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("statechange", (event) => { })

onstatechange = (event) => { }
```

## نوع رویداد

یک {{domxref("MIDIConnectionEvent")}} که از {{domxref("Event")}} ارث میبرد.

{{InheritanceDiagram("MIDIConnectionEvent")}}

## مثال

روش {{domxref("Navigator.requestMIDIAccess()")}} یک promise برمیگرداند که با یک شیء {{domxref("MIDIAccess")}} resolve میشود. وقتی یک پورت تغییر وضعیت میدهد، اطلاعات مربوط به آن پورت در کنسول چاپ میشود.

```js
navigator.requestMIDIAccess().then((access) => {
  access.onstatechange = (event) => {
    console.log(event.port.name, event.port.manufacturer, event.port.state);
  };
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}