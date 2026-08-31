---
title: "CharacterBoundsUpdateEvent: rangeEnd property"
short-title: rangeEnd
slug: Web/API/CharacterBoundsUpdateEvent/rangeEnd
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CharacterBoundsUpdateEvent.rangeEnd
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

خاصیتِ فقط-خواندنی **`CharacterBoundsUpdateEvent.rangeEnd`**، آفستِ آخرین نویسه در ناحیه متنی قابل ویرایش را نشان می‌دهد که سیستم عامل برای آن به مرزها نیاز دارد.

## مقدار

یک {{jsxref("Number")}}.

## مثال‌ها

### خواندن مقدار `rangeEnd`

این مثال نحوه استفاده از رویداد `characterboundsupdate` و خواندن مقدار ویژگی‌های `rangeStart` و `rangeEnd` را نشان می‌دهد.

```js
const editContext = new EditContext();
editorElement.editContext = editContext;

editContext.addEventListener("characterboundsupdate", (e) => {
  console.log(
    `The OS needs the bounds of the chars at ${e.rangeStart} - ${e.rangeEnd}.`,
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}