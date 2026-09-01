---
title: "Document: lastStyleSheetSet property"
short-title: lastStyleSheetSet
slug: Web/API/Document/lastStyleSheetSet
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Document.lastStyleSheetSet
---

{{APIRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

ویژگی **`Document.lastStyleSheetSet`** آخرین مجموعه‌ی استایل‌شیت فعال را برمی‌گرداند. مقدار این ویژگی هرگاه که ویژگی {{domxref("document.selectedStyleSheetSet")}} تغییر کند، تغییر می‌کند.

## مقدار

مجموعه‌ی استایل‌شیتی که اخیراً تنظیم شده است. اگر مجموعه‌ی استایل‌شیت جاری با تنظیم {{domxref("document.selectedStyleSheetSet")}} تغییر نکرده باشد، مقدار بازگشتی `null` است.

> [!NOTE]
> این مقدار هنگام فراخوانی {{domxref("document.enableStyleSheetsForSet()")}} تغییر نمی‌کند.

## مثال‌ها

```js
let lastSheetSet = document.lastStyleSheetSet;

if (!lastSheetSet) {
  lastSheetSet = "Style sheet not yet changed";
} else {
  console.log(`The last style sheet set is: ${lastSheetSet}`);
}
```

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.preferredStyleSheetSet")}}
- {{domxref("document.selectedStyleSheetSet")}}
- {{domxref("document.styleSheetSets")}}
- {{domxref("document.enableStyleSheetsForSet()")}}