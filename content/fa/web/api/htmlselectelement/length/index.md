---
title: "HTMLSelectElement: length property"
short-title: length
slug: Web/API/HTMLSelectElement/length
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.length
---

{{ APIRef("HTML DOM") }}

ویژگی **`length`** از رابط {{DOMxRef("HTMLSelectElement")}} تعداد عناصر {{htmlelement("option")}} در عنصر {{htmlelement("select")}} را مشخص می‌کند. این ویژگی تعداد گره‌ها را در مجموعهٔ {{DOMxRef("HTMLSelectElement.options", "options")}} نشان می‌دهد. هنگام مقداردهی، مانند {{DOMxRef("HTMLOptionsCollection.length")}} عمل می‌کند.

## مقدار

یک عدد.

## مثال‌ها

```js
const selectElement = document.getElementById("fruits");
console.log(selectElement.length);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTMLElement("select")}}
- {{HTMLElement("option")}}
- {{DOMXref("HTMLSelectElement.options")}}
- {{DOMXref("HTMLSelectElement.selectedOptions")}}
- {{DOMXref("HTMLSelectElement.multiple")}}
- {{DOMXref("HTMLSelectElement.selectedIndex")}}