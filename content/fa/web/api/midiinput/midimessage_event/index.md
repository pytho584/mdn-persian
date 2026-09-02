---
title: "MIDIInput: midimessage event"
short-title: midimessage
slug: Web/API/MIDIInput/midimessage_event
page-type: web-api-event
browser-compat: api.MIDIInput.midimessage_event
---

{{APIRef("Web MIDI API")}}{{securecontext_header}}

رویداد `midimessage` در [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API) زمانی رخ می‌دهد که پورت MIDI متناظر با این {{domxref("MIDIInput")}} دریافت یک یا چند پیام MIDI را به پایان می‌رساند. یک نمونه از {{domxref("MIDIMessageEvent")}} که شامل پیام دریافت‌شده است به کنترل‌کننده رویداد ارسال می‌شود.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("midimessage", (event) => { })

onmidimessage = (event) => { }
```

## نوع رویداد

یک {{domxref("MIDIMessageEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("MIDIMessageEvent")}}

## مثال‌ها

در مثال زیر، رویدادهای `midimessage` روی تمام درگاه‌های ورودی شنیده می‌شوند. هنگامی که یک پیام دریافت می‌شود، ویژگی {{domxref("MIDIMessageEvent.data")}} در کنسول چاپ می‌شود.

```js
inputs.forEach((input) => {
  input.onmidimessage = (message) => {
    console.log(message.data);
  };
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}