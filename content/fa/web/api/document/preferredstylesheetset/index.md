---
title: "Document: preferredStyleSheetSet property"
short-title: preferredStyleSheetSet
slug: Web/API/Document/preferredStyleSheetSet
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Document.preferredStyleSheetSet
---

{{APIRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

خاصیت **`preferredStyleSheetSet`**، مجموعه‌ی برگه‌ی سبک ترجیحی (preferred style sheet set) را که توسط نویسنده‌ی صفحه تعیین شده است، برمی‌گرداند.

## مقدار

مجموعه‌ی برگه‌ی سبک ترجیحی نویسنده. این مقدار بر اساس ترتیب اعلام‌های برگه‌ی سبک و هدر HTTP `Default-Style` تعیین می‌شود.

اگر مجموعه‌ی برگه‌ی سبک ترجیحی توسط نویسنده تعریف نشده باشد، رشته‌ی خالی (`""`) برگردانده می‌شود.

## مثال‌ها

```js
if (document.preferredStyleSheetSet) {
  console.log(
    `The preferred style sheet set is: ${document.preferredStyleSheetSet}`,
  );
} else {
  console.log("There is no preferred style sheet.");
}
```

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.lastStyleSheetSet")}}
- {{domxref("document.selectedStyleSheetSet")}}
- {{domxref("document.styleSheetSets")}}
- {{domxref("document.enableStyleSheetsForSet()")}}