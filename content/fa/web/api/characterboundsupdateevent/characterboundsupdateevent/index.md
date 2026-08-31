---
title: "CharacterBoundsUpdateEvent: CharacterBoundsUpdateEvent() constructor"
---

---
title: "CharacterBoundsUpdateEvent: CharacterBoundsUpdateEvent() constructor"
short-title: CharacterBoundsUpdateEvent()
slug: Web/API/CharacterBoundsUpdateEvent/CharacterBoundsUpdateEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.CharacterBoundsUpdateEvent.CharacterBoundsUpdateEvent
---

{{APIRef("CharacterBoundsUpdateEvent API")}}{{SeeCompatTable}}

سازندهی **`CharacterBoundsUpdateEvent()`** یک شیء جدید {{DOMxRef("CharacterBoundsUpdateEvent")}} برمیگرداند.

## نحو

```js-nolint
new CharacterBoundsUpdateEvent(type)
new CharacterBoundsUpdateEvent(type, options)
```

### پارامترها

- `type`
  - : رشتهای است که نوع رویداد را مشخص میکند. مقادیر ممکن: `"characterboundsupdate"`.
- `options` {{optional_inline}}
  - : یک شیء اختیاری با ویژگیهای زیر:
    - `rangeStart`
      - : عددی برای تنظیم افست نخستین نویسه در ناحیهی متنی قابل ویرایش که این رویداد روی آن اعمال میشود.
    - `rangeEnd`
      - : عددی برای تنظیم افست آخرین نویسه در ناحیهی متنی قابل ویرایش که این رویداد روی آن اعمال میشود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("CharacterBoundsUpdateEvent")}} که این سازنده به آن تعلق دارد.