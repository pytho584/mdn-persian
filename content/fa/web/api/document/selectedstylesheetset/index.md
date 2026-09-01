---
title: "Document: selectedStyleSheetSet property"
short-title: selectedStyleSheetSet
slug: Web/API/Document/selectedStyleSheetSet
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Document.selectedStyleSheetSet
---

{{APIRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

ویژگی **`selectedStyleSheetSet`** نام مجموعه‌ی برگه‌های سبکی را که در حال حاضر استفاده می‌شود، نشان می‌دهد.

## مقدار

نام مجموعه‌ی برگه‌های سبکی که در حال حاضر در حال استفاده است. همچنین می‌توانید مجموعه‌ی برگه‌های سبکی فعلی را با استفاده از این ویژگی تنظیم کنید.

تنظیم مقدار این ویژگی معادل فراخوانی
{{domxref("document.enableStyleSheetsForSet()")}} با مقدار
`currentStyleSheetSet` و سپس تنظیم مقدار
`lastStyleSheetSet` بر روی همان مقدار است.

> [!NOTE]
> مقدار این ویژگی زنده است؛ تغییر مستقیم
> ویژگی `disabled` روی برگه‌های سبک، بر مقدار این ویژگی نیز تأثیر می‌گذارد.

## مثال‌ها

```js
console.log(`Current style sheet set: ${document.selectedStyleSheetSet}`);

document.selectedStyleSheetSet = "Some other style sheet";
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.lastStyleSheetSet")}}
- {{domxref("document.preferredStyleSheetSet")}}
- {{domxref("document.styleSheetSets")}}
- {{domxref("document.enableStyleSheetsForSet()")}}