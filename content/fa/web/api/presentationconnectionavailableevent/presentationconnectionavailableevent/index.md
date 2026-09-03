```
---
title: "PresentationConnectionAvailableEvent: PresentationConnectionAvailableEvent() constructor"
---

---
title: "PresentationConnectionAvailableEvent: PresentationConnectionAvailableEvent() constructor"
short-title: PresentationConnectionAvailableEvent()
slug: Web/API/PresentationConnectionAvailableEvent/PresentationConnectionAvailableEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.PresentationConnectionAvailableEvent.PresentationConnectionAvailableEvent
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

سازندهٔ **`PresentationConnectionAvailableEvent()`** یک شیء جدید از جنس {{domxref("PresentationConnectionAvailableEvent")}} می‌سازد.

## سینتکس

```js-nolint
new PresentationConnectionAvailableInit(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای که نام رویداد را مشخص می‌کند. این نام به بزرگی و کوچکی حروف حساس است و مرورگرها آن را روی `connectionavailable` تنظیم می‌کنند.
- `options`
  - : شیءای که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `connection`
      - : شیء {{domxref("PresentationConnection")}} مرتبط.

### مقدار بازگشتی

یک شیء جدید از {{domxref("PresentationConnectionAvailableEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```