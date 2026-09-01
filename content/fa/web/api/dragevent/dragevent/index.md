```yaml
---
title: "DragEvent: DragEvent() constructor"
short-title: DragEvent()
slug: Web/API/DragEvent/DragEvent
page-type: web-api-constructor
browser-compat: api.DragEvent.DragEvent
---

{{APIRef("HTML Drag and Drop API")}}

این سازنده برای ایجاد یک شیء {{domxref("DragEvent")}} مصنوعی (synthetic) استفاده می‌شود.

اگرچه این رابط یک سازنده دارد، اما نمی‌توان از طریق اسکریپت یک شیء {{domxref("DataTransfer")}} مفید ایجاد کرد، زیرا اشیاء {{domxref("DataTransfer")}} دارای یک مدل پردازش و امنیت هستند که توسط مرورگر در طول عملیات کشیدن و رها کردن (drag-and-drop) هماهنگ می‌شود.

این رابط ویژگی‌هایی را از {{domxref("MouseEvent")}} و {{domxref("Event")}} به ارث می‌برد.

## Syntax

```js-nolint
new DragEvent(type)
new DragEvent(type, dragEventInit)
```

### Parameters

- `type`
  - : یک رشته که نام رویداد را نشان می‌دهد (به [انواع رویداد DragEvent](/en-US/docs/Web/API/DragEvent#event_types) مراجعه کنید).

- `eventInitDict` {{optional_inline}}
  - : یک شیء شامل ویژگی‌های زیر:
    - `dataTransfer` {{optional_inline}}
      - : یک {{domxref("DataTransfer")}}. پیش‌فرض `null` است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```