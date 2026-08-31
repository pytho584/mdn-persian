---
title: "ClipboardChangeEvent: ClipboardChangeEvent() constructor"
---

---
title: "ClipboardChangeEvent: ClipboardChangeEvent() constructor"
short-title: ClipboardChangeEvent()
slug: Web/API/ClipboardChangeEvent/ClipboardChangeEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.ClipboardChangeEvent.ClipboardChangeEvent
---

{{securecontext_header}}{{APIRef("Clipboard API")}}{{SeeCompatTable}}

سازندهٔ **`ClipboardChangeEvent()`** یک نمونهٔ جدید از {{domxref("ClipboardChangeEvent")}} می‌سازد که هنگام رخ دادن رویداد `clipboardchange` استفاده می‌شود. رویداد `clipboardchange` هر زمان که محتوای کلیپ‌بورد سیستم توسط یک برنامهٔ وب یا هر برنامهٔ سیستم دیگری تغییر کند، به وقوع می‌پیوندد.

> [!NOTE]
> این سازندهٔ رویداد عموماً برای وب‌سایت‌های تولیدی لازم نیست. کاربرد اصلی آن در تست‌هایی است که نیاز به یک نمونه از این رویداد دارند.

## سینتکس

```js-nolint
new ClipboardChangeEvent(type)
new ClipboardChangeEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای است که نام رویداد را مشخص می‌کند. باید همیشه روی `clipboardchange` تنظیم شود.
- `options` {{Optional_Inline}}
  - : یک شیء که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `types`
      - : آرایه‌ای از رشته‌ها که انواع داده‌های موجود در کلیپ‌بورد سیستم را نشان می‌دهد.
    - `changeId`
      - : یک عدد صحیح که شناسهٔ یکتایی برای عملیات تغییر کلیپ‌بورد است.

### مقدار بازگشتی

یک شیء جدید {{domxref("ClipboardChangeEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}