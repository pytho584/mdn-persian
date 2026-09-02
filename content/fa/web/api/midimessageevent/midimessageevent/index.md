---
title: "MIDIMessageEvent: MIDIMessageEvent() constructor"
---

---
title: "MIDIMessageEvent: MIDIMessageEvent() constructor"
short-title: MIDIMessageEvent()
slug: Web/API/MIDIMessageEvent/MIDIMessageEvent
page-type: web-api-constructor
browser-compat: api.MIDIMessageEvent.MIDIMessageEvent
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

سازندهٔ **`MIDIMessageEvent()`** یک شیء جدید از نوع {{domxref("MIDIMessageEvent")}} می‌سازد. معمولاً از این سازنده استفاده نمی‌شود، زیرا رویدادها زمانی ساخته می‌شوند که یک {{domxref("MIDIInput")}} دریافتِ یک یا چند پیام MIDI را به پایان می‌رساند.

## سینتکس

```js-nolint
new MIDIMessageEvent(type)
new MIDIMessageEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای که نام رویداد را مشخص می‌کند.
    این مقدار به بزرگی و کوچکی حروف حساس است و مرورگرها همیشه آن را برابر با `MIDIMessageEvent` قرار می‌دهند.
- `options` {{optional_inline}}
  - : یک شیء، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی زیر را داشته باشد:
    - `data`
      - : یک نمونه از {{jsxref("Uint8Array")}} که بایت‌های دادهٔ پیام MIDI را در بر دارد.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("MIDIMessageEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}