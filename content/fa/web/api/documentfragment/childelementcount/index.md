---
title: "DocumentFragment: childElementCount property"
short-title: childElementCount
slug: Web/API/DocumentFragment/childElementCount
page-type: web-api-instance-property
browser-compat: api.DocumentFragment.childElementCount
---

{{ APIRef("DOM") }}

خاصیت فقط خواندنی **`DocumentFragment.childElementCount`** تعداد عناصر فرزند یک `DocumentFragment` را برمی‌گرداند.

برای دریافت تعداد فرزندان یک عنصر خاص، به {{domxref("Element.childElementCount")}} مراجعه کنید.

## Value

یک عدد که تعداد فرزندان قطعه سند (document fragment) را نشان می‌دهد.

## Examples

```js
let fragment = new DocumentFragment();
fragment.childElementCount; // 0

let paragraph = document.createElement("p");
fragment.appendChild(paragraph);

fragment.childElementCount; // 1
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element.childElementCount")}}
- {{domxref("Document.childElementCount")}}