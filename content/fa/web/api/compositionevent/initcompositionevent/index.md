---
title: "CompositionEvent: initCompositionEvent() method"
short-title: initCompositionEvent()
slug: Web/API/CompositionEvent/initCompositionEvent
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.CompositionEvent.initCompositionEvent
---

{{deprecated_header}}{{APIRef("UI Events")}}

متد **`initCompositionEvent()`** از رابط {{domxref("CompositionEvent")}} ویژگی‌های یک نمونه از شیء `CompositionEvent` را مقداردهی اولیه می‌کند.

> [!NOTE] روش صحیح ایجاد یک {{domxref("CompositionEvent")}} استفاده از سازنده {{domxref("CompositionEvent.CompositionEvent", "CompositionEvent()")}} است.

## Syntax

```js-nolint
initCompositionEvent(type, canBubble, cancelable, view, data, locale)
```

### پارامترها

- `type`
  - : یک رشته (string) که نوع رویداد ترکیب (composition event) را مشخص می‌کند؛ این مقدار یکی از `compositionstart`، `compositionupdate` یا `compositionend` خواهد بود.
- `canBubble`
  - : یک مقدار بولی (boolean) که مشخص می‌کند آیا رویداد می‌تواند بالا برود (bubble) یا خیر.
- `cancelable`
  - : یک مقدار بولی که نشان می‌دهد آیا رویداد قابل لغو شدن است یا خیر.
- `view`
  - : شیء {{domxref("Window")}}ای که رویداد از آن تولید شده است.
- `data`
  - : یک رشته که مقدار ویژگی `data` را نشان می‌دهد.
- `locale`
  - : یک رشته که مقدار ویژگی `locale` را نشان می‌دهد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CompositionEvent")}}