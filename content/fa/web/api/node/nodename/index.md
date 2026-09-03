---
title: "Node: nodeName property"
short-title: nodeName
slug: Web/API/Node/nodeName
page-type: web-api-instance-property
browser-compat: api.Node.nodeName
---

{{APIRef("DOM")}}

ویژگی فقط خواندنی **`nodeName`** از {{domxref("Node")}} نام گره جاری را به صورت یک رشته بازمی‌گرداند.

## مقدار

یک رشته. مقادیر برای انواع مختلف گره‌ها به شرح زیر است:

- {{domxref("Attr")}}
  - : مقدار {{domxref("Attr.name")}}، یعنی _نام واجد شرایط_ ویژگی.
- {{domxref("CDATASection")}}
  - : رشته `"#cdata-section"`.
- {{domxref("Comment")}}
  - : رشته `"#comment"`.
- {{domxref("Document")}}
  - : رشته `"#document"`.
- {{domxref("DocumentFragment")}}
  - : رشته `"#document-fragment"`.
- {{domxref("DocumentType")}}
  - : مقدار {{domxref("DocumentType.name")}}
- {{domxref("Element")}}
  - : مقدار {{domxref("Element.tagName")}}، یعنی _نام بزرگ_ (uppercase) تگ عنصر اگر یک عنصر HTML باشد،
    یا _نام کوچک_ (lowercase) تگ عنصر اگر یک عنصر XML (مانند عناصر SVG یا MathML) باشد.
- {{domxref("ProcessingInstruction")}}
  - : مقدار {{domxref("ProcessingInstruction.target")}}
- {{domxref("Text")}}
  - : رشته `"#text"`.

## مثال

این مثال نام گره‌های چند گره را نمایش می‌دهد.

```html
This is some HTML:
<div id="d1">Hello world</div>
<!-- Example of comment -->
Text <span>Text</span> Text<br />
<svg height="20" width="20">
  <circle cx="10" cy="10" r="5" stroke="black" stroke-width="1" fill="red" />
</svg>
<hr />
<output id="result">Not calculated yet.</output>
```

و اسکریپت زیر:

```js
let node = document.querySelector("body").firstChild;
let result = "Node names are:\n";
while (node) {
  result += `${node.nodeName}\n`;
  node = node.nextSibling;
}

const output = document.getElementById("result");
output.innerText = result;
```

{{ EmbedLiveSample("Example", "100%", "450") }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.tagName")}}
- {{domxref("Attr.name")}}
- {{domxref("DocumentType.name")}}
- {{domxref("ProcessingInstruction.target")}}