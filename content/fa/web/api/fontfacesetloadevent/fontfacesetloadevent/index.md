---
title: "FontFaceSetLoadEvent: FontFaceSetLoadEvent() constructor"
short-title: FontFaceSetLoadEvent()
slug: Web/API/FontFaceSetLoadEvent/FontFaceSetLoadEvent
page-type: web-api-constructor
browser-compat: api.FontFaceSetLoadEvent.FontFaceSetLoadEvent
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

سازنده‌ی **`FontFaceSetLoadEvent()`** یک شیء جدید {{domxref("FontFaceSetLoadEvent")}} می‌سازد که هر زمان یک {{domxref("FontFaceSet")}} بارگذاری شود، فراخوانی می‌شود.

## Syntax

```js-nolint
new FontFaceSetLoadEvent(type)
new FontFaceSetLoadEvent(type, options)
```

### Parameters

- `type`
  - : یک رشته حاوی نام رویداد. این رشته به بزرگی/کوچکی حروف حساس است و مرورگرها همیشه آن را روی `loading`، `loadingdone` یا `loadingerror` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `fontfaces` {{optional_inline}}
      - : آرایه‌ای از نمونه‌های {{domxref("FontFace")}}. پیش‌فرض آن آرایه‌ی خالی است.

### Return value

یک شیء جدید {{domxref("FontFaceSetLoadEvent")}}.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}