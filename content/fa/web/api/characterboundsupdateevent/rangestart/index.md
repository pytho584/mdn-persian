---
title: "CharacterBoundsUpdateEvent: rangeStart property"
---

---
title: "CharacterBoundsUpdateEvent: rangeStart property"
short-title: rangeStart
slug: Web/API/CharacterBoundsUpdateEvent/rangeStart
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CharacterBoundsUpdateEvent.rangeStart
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

**خاصیت فقط‌خواندنی `CharacterBoundsUpdateEvent.rangeStart`** افست (offset) اولین کاراکتر در ناحیه‌ی متن قابل‌ویرایش را نشان می‌دهد که سیستم‌عامل به مرزهای (bounds) آن نیاز دارد.

## مقدار

یک {{jsxref("Number")}}.

## مثال‌ها

### خواندن مقدار `rangeStart`

این مثال نحوه‌ی استفاده از رویداد `characterboundsupdate` و خواندن مقدار خاصیت‌های `rangeStart` و `rangeEnd` را نشان می‌دهد.

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

## سازگاری مرورگر

{{Compat}}