---
title: "PointerEvent: PointerEvent() constructor"
short-title: PointerEvent()
slug: Web/API/PointerEvent/PointerEvent
page-type: web-api-constructor
browser-compat: api.PointerEvent.PointerEvent
---

{{APIRef("Pointer Events")}}

سازندهٔ **`PointerEvent()`** یک نمونه شیء جدید از {{domxref("PointerEvent")}} می‌سازد که مصنوعی (synthetic) و غیرقابل‌اعتماد (untrusted) است.

## Syntax

```js-nolint
new PointerEvent(type)
new PointerEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نام رویداد را نشان می‌دهد (به [انواع رویداد PointerEvent](/en-US/docs/Web/API/PointerEvent#pointer_event_types) مراجعه کنید).
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("MouseEvent/MouseEvent", "MouseEvent()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `pointerId`
      - : یک عدد، پیش‌فرض `0`، که مقدار {{domxref("PointerEvent.pointerId")}} نمونه را تنظیم می‌کند.
    - `width`
      - : یک عدد، پیش‌فرض `1`، که مقدار {{domxref("PointerEvent.width")}} نمونه را تنظیم می‌کند.
    - `height`
      - : یک عدد، پیش‌فرض `1`، که مقدار {{domxref("PointerEvent.height")}} نمونه را تنظیم می‌کند.
    - `pressure`
      - : یک عدد، پیش‌فرض `0`، که مقدار {{domxref("PointerEvent.pressure")}} نمونه را تنظیم می‌کند.
    - `tangentialPressure`
      - : یک عدد، پیش‌فرض `0`، که مقدار {{domxref("PointerEvent.tangentialPressure")}} نمونه را تنظیم می‌کند.
    - `altitudeAngle`
      - : یک عدد که مقدار {{domxref("PointerEvent.altitudeAngle")}} نمونه را تنظیم می‌کند.
    - `azimuthAngle`
      - : یک عدد که مقدار {{domxref("PointerEvent.azimuthAngle")}} نمونه را تنظیم می‌کند.
    - `tiltX`
      - : یک عدد که مقدار {{domxref("PointerEvent.tiltX")}} نمونه را تنظیم می‌کند.
    - `tiltY`
      - : یک عدد که مقدار {{domxref("PointerEvent.tiltY")}} نمونه را تنظیم می‌کند.
    - `twist`
      - : یک عدد، پیش‌فرض `0`، که مقدار {{domxref("PointerEvent.twist")}} نمونه را تنظیم می‌کند.
    - `pointerType`
      - : یک رشته، پیش‌فرض `""`، که مقدار {{domxref("PointerEvent.pointerType")}} نمونه را تنظیم می‌کند.
    - `isPrimary`
      - : یک مقدار بولی، پیش‌فرض `false`، که مقدار {{domxref("PointerEvent.isPrimary")}} نمونه را تنظیم می‌کند.

### مقدار بازگشتی

یک شیء جدید {{domxref("PointerEvent")}}.

## مثال‌ها

```js
const moveEvent = new PointerEvent("pointermove");

const downEvent = new PointerEvent("pointerdown", {
  pointerId: 1,
  bubbles: true,
  cancelable: true,
  pointerType: "touch",
  width: 100,
  height: 100,
  isPrimary: true,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}