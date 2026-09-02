---
title: "MIDIPort: statechange event"
short-title: statechange
slug: Web/API/MIDIPort/statechange_event
page-type: web-api-event
browser-compat: api.MIDIPort.statechange_event
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

رویداد **`statechange`** از رابط {{domxref("MIDIPort")}} وقتی فعال می‌شود که یک پورت از حالت باز به بسته، یا از بسته به باز تغییر وضعیت دهد.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی هندلر رویداد تنظیم کنید.

```js-nolint
addEventListener("statechange", (event) => { })

onstatechange = (event) => { }
```

## نوع رویداد

یک {{domxref("MIDIConnectionEvent")}}. از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("MIDIConnectionEvent")}}

## مثال

در مثال زیر، وضعیت فعلی {{domxref("MIDIPort.state")}} هر بار که تغییر می‌کند در کنسول ثبت می‌شود.

```js
port.onstatechange = (event) => {
  console.log(port.state);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}