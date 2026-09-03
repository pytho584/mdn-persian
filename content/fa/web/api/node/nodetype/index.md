---
title: "Node: nodeType property"
short-title: nodeType
slug: Web/API/Node/nodeType
page-type: web-api-instance-property
browser-compat: api.Node.nodeType
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`nodeType`** از رابط {{domxref("Node")}} یک عدد صحیح است که نوع گره را مشخص می‌کند. این ویژگی انواع مختلف گره‌ها مانند {{domxref("Element", "المان‌ها")}}، {{domxref("Text", "متن‌ها")}} و {{domxref("Comment", "کامنت‌ها")}} را از یکدیگر متمایز می‌کند.

## مقدار

یک عدد صحیح که نوع گره را مشخص می‌کند. مقادیر ممکن عبارتند از:

- `Node.ELEMENT_NODE` (`1`)
  - : یک گره {{domxref("Element")}} مانند {{HTMLElement("p")}} یا {{HTMLElement("div")}}.
- `Node.ATTRIBUTE_NODE` (`2`)
  - : یک {{domxref("Attr", "صفت")}} از یک {{domxref("Element")}}.
- `Node.TEXT_NODE` (`3`)
  - : {{domxref("Text", "متن")}} واقعی درون یک {{domxref("Element")}} یا {{domxref("Attr")}}.
- `Node.CDATA_SECTION_NODE` (`4`)
  - : یک {{domxref("CDATASection")}}، مانند `<!CDATA[[ … ]]>`
- `Node.PROCESSING_INSTRUCTION_NODE` (`7`)
  - : یک {{domxref("ProcessingInstruction")}} از یک سند XML، مانند `<?xml-stylesheet … ?>`.
- `Node.COMMENT_NODE` (`8`)
  - : یک گره {{domxref("Comment", "کامنت")}}، مانند `<!-- … -->`.
- `Node.DOCUMENT_NODE` (`9`)
  - : یک گره {{domxref("Document")}}.
- `Node.DOCUMENT_TYPE_NODE` (`10`)
  - : یک گره {{domxref("DocumentType")}}، مانند `<!doctype html>`.
- `Node.DOCUMENT_FRAGMENT_NODE` (`11`)
  - : یک گره {{domxref("DocumentFragment")}}.

ثابت‌های زیر منسوخ شده‌اند و دیگر استفاده نمی‌شوند: `Node.ENTITY_REFERENCE_NODE` (`5`)،
`Node.ENTITY_NODE` (`6`) و `Node.NOTATION_NODE` (`12`).

## مثال‌ها

### انواع مختلف گره‌ها

```js
document.nodeType === Node.DOCUMENT_NODE; // true
document.doctype.nodeType === Node.DOCUMENT_TYPE_NODE; // true

document.createDocumentFragment().nodeType === Node.DOCUMENT_FRAGMENT_NODE; // true

const p = document.createElement("p");
p.textContent = "Once upon a time…";

p.nodeType === Node.ELEMENT_NODE; // true
p.firstChild.nodeType === Node.TEXT_NODE; // true
```

### کامنت‌ها

این مثال بررسی می‌کند که آیا اولین گره داخل المان سند یک کامنت است یا خیر، و در غیر این صورت یک پیام نمایش می‌دهد.

```js
const node = document.documentElement.firstChild;
if (node.nodeType !== Node.COMMENT_NODE) {
  console.warn("You should comment your code!");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}