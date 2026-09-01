---
title: "DataTransfer: addElement() method"
short-title: addElement()
slug: Web/API/DataTransfer/addElement
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.DataTransfer.addElement
---

{{APIRef("HTML Drag and Drop API")}}{{SeeCompatTable}}{{Non-standard_header}}

روش **`DataTransfer.addElement()`**، منبع کشیدن (drag source) را به عنصر داده‌شده تنظیم می‌کند. این عنصر، عنصری خواهد بود که رویدادهای {{domxref("HTMLElement/drag_event", "drag")}} و {{domxref("HTMLElement/dragend_event", "dragend")}} به آن فرستاده می‌شوند، و نه هدف پیش‌فرض (گره‌ای که کشیده شد).

> [!NOTE]
> این روش مختص فایرفاکس است.

## Syntax

```js-nolint
addElement(element)
```

### Parameters

- `element`
  - : {{domxref("Element")}}ای که به عنوان منبع کشیدن تنظیم می‌شود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

این مثال استفاده از روش `addElement()` را نشان می‌دهد.

```js
function changeDragNode(event, node) {
  const dt = event.dataTransfer;
  dt.addElement(node);
}
```

## Specifications

این روش در هیچ استاندارد وب تعریف نشده است.

## Browser compatibility

{{Compat}}

## See also

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با ذخیره‌گاه داده‌ی کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)