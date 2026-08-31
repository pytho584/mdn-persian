---
title: "ClipboardEvent: ClipboardEvent() constructor"
short-title: ClipboardEvent()
slug: Web/API/ClipboardEvent/ClipboardEvent
page-type: web-api-constructor
browser-compat: api.ClipboardEvent.ClipboardEvent
---

{{APIRef("Clipboard API")}}

سازنده **`ClipboardEvent()`** یک شیء جدید از نوع {{domxref("ClipboardEvent")}} را برمی‌گرداند که نمایانگر رویدادی مرتبط با تغییرات در کلیپ‌بورد (حافظه موقت) است؛ یعنی رویدادهای {{domxref("Element/cut_event", "cut")}} (برش)، {{domxref("Element/copy_event", "copy")}} (کپی) و {{domxref("Element/paste_event", "paste")}} (چسباندن).

## نحو (Syntax)

```js-nolint
new ClipboardEvent(type)
new ClipboardEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته (string) که نام نوع `ClipboardEvent` را مشخص می‌کند. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها آن را به `copy`، `cut` یا `paste` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، دارای ویژگی‌های زیر است:
    - `clipboardData` {{optional_inline}}
      - : یک شیء {{domxref("DataTransfer")}} که داده‌های مربوط به رویداد کلیپ‌بورد را دربر می‌گیرد. مقدار پیش‌فرض آن `null` است.
    - `dataType` {{non-standard_inline}} {{optional_inline}}
      - : یک رشته (string) که نوع MIME داده‌های موجود در آرگومان `data` را مشخص می‌کند. مقدار پیش‌فرض آن `""` است.
    - `data` {{non-standard_inline}} {{optional_inline}}
      - : یک رشته (string) که داده‌های مربوط به رویداد کلیپ‌بورد را دربر می‌گیرد. مقدار پیش‌فرض آن `""` است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("ClipboardEvent")}}.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط با کپی: {{domxref("Element/copy_event", "copy")}}، {{domxref("Element/cut_event", "cut")}}، {{domxref("Element/paste_event", "paste")}}
- رابط {{domxref("ClipboardEvent")}} که این سازنده به آن تعلق دارد.
- [API کلیپ‌بورد](/en-US/docs/Web/API/Clipboard_API)