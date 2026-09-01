---
title: "FocusEvent: FocusEvent() constructor"
short-title: FocusEvent()
slug: Web/API/FocusEvent/FocusEvent
page-type: web-api-constructor
browser-compat: api.FocusEvent.FocusEvent
---

{{APIRef("UI Events")}}

سازندهٔ **`FocusEvent()`** یک شیء {{domxref("FocusEvent")}} تازه‌ساخته با یک {{domxref("EventTarget")}} اختیاری برمی‌گرداند. وقتی رویداد هم مبدأ و هم مقصد دارد، مقدار `relatedTarget` باید روی هدف دیگر تنظیم شود.

## نحو (Syntax)

```js-nolint
new FocusEvent(type)
new FocusEvent(type, options)
```

### پارامترها

_سازندهٔ `FocusEvent()` همچنین آرگومان‌هایی را از {{domxref("UIEvent.UIEvent", "UIEvent()")}} و {{domxref("Event.Event", "Event()")}} به ارث می‌برد._

- `type`
  - : رشته‌ای با نام رویداد. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها آن را به `blur`، `focus`، `focusin` یا `focusout` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که علاوه بر ویژگی‌های تعریف‌شده در {{domxref("UIEvent/UIEvent", "UIEvent()")}}، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `relatedTarget` {{optional_inline}}
      - : یک {{domxref("EventTarget")}} که هدف ثانویهٔ یک {{domxref("FocusEvent")}} را نشان می‌دهد. مقدار پیش‌فرض آن `null` است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("FocusEvent")}} که این سازنده به آن تعلق دارد.