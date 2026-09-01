---
title: "Document: enableStyleSheetsForSet() method"
---

{{APIRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

برگه‌های سبک (style sheets) مطابق با نام مشخص‌شده در مجموعه‌ی برگه‌های سبک فعلی را فعال می‌کند و تمام برگه‌های سبک دیگر را غیرفعال می‌کند (به جز آن‌هایی که عنوان ندارند، که همیشه فعال هستند).

## Syntax

```js-nolint
enableStyleSheetsForSet(name)
```

### Parameters

- `name`
  - : نام برگه‌های سبکی که باید فعال شوند. تمام برگه‌های سبکی که عنوانی دارند و با این نام مطابقت دارند فعال می‌شوند، در حالی که سایر برگه‌هایی که عنوان دارند غیرفعال می‌شوند. برای غیرفعال کردن تمام برگه‌های سبک جایگزین و ترجیحی (اما نه برگه‌های سبک پایدار؛ یعنی آن‌هایی که ویژگی `title` ندارند)، یک رشته‌ی خالی برای پارامتر _name_ مشخص کنید.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Notes

- تطابق عنوان‌ها به حروف بزرگ و کوچک حساس است.
- فراخوانی این متد با _name_ برابر با `null` اثری ندارد؛ اگر می‌خواهید تمام برگه‌های سبک جایگزین و ترجیحی را غیرفعال کنید، **باید** رشته‌ی خالی "" را ارسال کنید.
- برگه‌های سبکی که عنوان ندارند، هرگز تحت تأثیر این متد قرار نمی‌گیرند.
- این متد هرگز بر مقادیر {{domxref("document.lastStyleSheetSet")}} یا {{domxref("document.preferredStyleSheetSet")}} تأثیر نمی‌گذارد.

## Examples

```js
document.enableStyleSheetsForSet("Some style sheet set name");
```

## Specifications

بخشی از هیچ مشخصاتی نیست.

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Stylesheet")}}
- {{domxref("Document.styleSheets")}}
- {{domxref("document.lastStyleSheetSet")}}
- {{domxref("document.preferredStyleSheetSet")}}
- {{domxref("document.selectedStyleSheetSet")}}