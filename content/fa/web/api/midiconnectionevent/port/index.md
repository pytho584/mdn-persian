---
title: "MIDIConnectionEvent: port property"
short-title: port
slug: Web/API/MIDIConnectionEvent/port
page-type: web-api-instance-property
browser-compat: api.MIDIConnectionEvent.port
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`port`** از رابط {{domxref("MIDIConnectionEvent")}}، پورتی را که قطع یا وصل شده است بازمی‌گرداند.

## مقدار

یک شیء {{domxref("MIDIPort")}}.

## مثال‌ها

متد {{domxref("Navigator.requestMIDIAccess()")}} یک وعده (Promise) برمی‌گرداند که با یک شیء {{domxref("MIDIAccess")}} حل می‌شود. وقتی وضعیت یک پورت تغییر کند، یک رویداد `MIDIConnectionEvent` به رویداد {{domxref("MIDIAccess.statechange_event","statechange")}} ارسال می‌شود. سپس اطلاعات مربوط به پورت را می‌توان در کنسول چاپ کرد.

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
