---
title: "Element: removeAttributeNode() method"
short-title: removeAttributeNode()
slug: Web/API/Element/removeAttributeNode
page-type: web-api-instance-method
browser-compat: api.Element.removeAttributeNode
---

{{ APIRef("DOM") }}

متد **`removeAttributeNode()`** از رابط {{domxref("Element")}}، گره {{domxref("Attr")}} مشخص‌شده را از عنصر حذف می‌کند.

اگر نیازی به بررسی گره ویژگی قبل از حذف آن ندارید، می‌توانید از متد {{domxref("Element.removeAttribute()")}} استفاده کنید.

## Syntax

```js-nolint
removeAttributeNode(attributeNode)
```

### Parameters

- `attributeNode`
  - : گره ویژگی‌ای که باید از عنصر حذف شود.

### Return value

گره ویژگی‌ای که حذف شده است.

### Exceptions

- `NotFoundError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که فهرست ویژگی‌های عنصر شامل گره ویژگی مورد نظر نباشد.

## Examples

```js
// Given: <div id="foo" lang="en-US" />
const d = document.getElementById("foo");
const dLang = d.getAttributeNode("lang");
d.removeAttributeNode(dLang);
// lang is now removed: <div id="foo" />
```

## Notes

اگر ویژگی حذف‌شده دارای مقدار پیش‌فرض باشد، بلافاصله جایگزین می‌شود. ویژگی جایگزین دارای همان URI فضای نام و نام محلی، و همچنین پیشوند اصلی (در صورت وجود) است.

متدی به نام `removeAttributeNodeNS` وجود ندارد؛ متد `removeAttributeNode` می‌تواند هم ویژگی‌های دارای فضای نام و هم ویژگی‌های بدون فضای نام را حذف کند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document.createAttribute()")}}
- {{domxref("Element.getAttributeNode()")}}
- {{domxref("Element.setAttributeNode()")}}