---
title: "Document: styleSheetSets property"
---

---
title: "Document: styleSheetSets property"
short-title: styleSheetSets
slug: Web/API/Document/styleSheetSets
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Document.styleSheetSets
---

{{APIRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

ویژگی فقط‌خواندنی **`styleSheetSets`** فهرستی زنده از تمام مجموعه‌های استایل‌شیتِ موجود در حال حاضر را بازمی‌گرداند.

## مقدار

فهرستی از مجموعه‌های استایل‌شیت که در دسترس هستند.

## مثال‌ها

با در نظر گرفتن یک عنصر {{HTMLElement("ul")}} (فهرست) با شناسه «sheetList»، می‌توانید آن را با نام همهٔ مجموعه‌های استایل‌شیتِ موجود با کدی مانند زیر پر کنید:

```js
const list = document.getElementById("sheetList");
const sheets = document.styleSheetSets;

list.textContent = "";

for (const sheet of sheets) {
  const item = document.createElement("li");
  item.textContent = sheet;
  list.appendChild(item);
}
```

## نکات

فهرست مجموعه‌های استایل‌شیت موجود با شمارش همهٔ استایل‌شیت‌های در دسترس برای سند، به ترتیبی که در ویژگی {{domxref("Document.styleSheets")}} فهرست شده‌اند، ساخته می‌شود و `title` هر استایل‌شیتی که دارای عنوان است به فهرست اضافه می‌شود. موارد تکراری (با مقایسهٔ حساس به بزرگی/کوچکی حروف) از فهرست حذف می‌شوند.

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- {{domxref("Stylesheet")}}
- {{domxref("Document.styleSheets")}}
- {{domxref("document.lastStyleSheetSet")}}
- {{domxref("document.preferredStyleSheetSet")}}
- {{domxref("document.selectedStyleSheetSet")}}
- {{domxref("document.enableStyleSheetsForSet()")}}