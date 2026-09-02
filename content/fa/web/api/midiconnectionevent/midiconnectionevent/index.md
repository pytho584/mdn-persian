---
title: "MIDIConnectionEvent: MIDIConnectionEvent() constructor"
---

---
title: "MIDIConnectionEvent: MIDIConnectionEvent() constructor"
short-title: MIDIConnectionEvent()
slug: Web/API/MIDIConnectionEvent/MIDIConnectionEvent
page-type: web-api-constructor
browser-compat: api.MIDIConnectionEvent.MIDIConnectionEvent
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

سازندهی **`MIDIConnectionEvent()`** یک شیء جدید از نوع {{domxref("MIDIConnectionEvent")}} می‌سازد. به‌طور معمول از این سازنده استفاده نمی‌شود، زیرا رویدادها زمانی ایجاد می‌شوند که یک درگاه جدید در دسترس قرار می‌گیرد و شیء به رویداد {{domxref("MIDIAccess.statechange_event", "statechange")}} منتقل می‌شود.

## Syntax

```js-nolint
new MIDIConnectionEvent(type)
new MIDIConnectionEvent(type, midiConnectionEventInit)
```

### Parameters

- `type`
  - : یک رشته که یکی از مقادیر `"connect"` یا `"disconnect"` را دارد.
- `midiConnectionEventInit` {{optional_inline}}
  - : یک دیکشنری شامل فیلدهای زیر:
    - `port`
      - : نمونه‌ی {{domxref("MIDIPort")}} که درگاهی را که متصل یا قطع شده است نشان می‌دهد.
    - `bubbles` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد آیا رویداد حباب می‌کند یا نه. پیش‌فرض `false` است.
    - `cancelable` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد آیا رویداد قابل لغو است یا نه. پیش‌فرض `false` است.
    - `composed` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد آیا رویداد شنونده‌هایی خارج از ریشه سایه (shadow root) را فعال می‌کند یا نه (برای جزئیات بیشتر به {{domxref("Event.composed")}} مراجعه کنید). پیش‌فرض `false` است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}