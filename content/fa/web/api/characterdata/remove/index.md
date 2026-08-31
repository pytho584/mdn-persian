---
title: "CharacterData: remove() method"
short-title: remove()
slug: Web/API/CharacterData/remove
page-type: web-api-instance-method
browser-compat: api.CharacterData.remove
---

{{APIRef("DOM")}}

متد **`remove()`** در رابط {{domxref("CharacterData")}} آن را از والد خود حذف می‌کند.
اگر این شیء والد نداشته باشد، فراخوانی `remove()` هیچ کاری انجام نمی‌دهد.

## Syntax

```js-nolint
remove()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Example

### استفاده از `remove()`

```html
<span>Result: </span>A long string.
```

```js
const span = document.querySelector("span");
const textNode = span.nextSibling;

textNode.remove(); // Removes the text
```

{{EmbedLiveSample("Example", "100%", 50)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("CharacterData.deleteData()")}}
- {{domxref("DocumentType.remove()")}}
- {{domxref("Element.remove()")}}