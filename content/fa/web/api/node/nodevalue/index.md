---
title: "Node: nodeValue property"
short-title: nodeValue
slug: Web/API/Node/nodeValue
page-type: web-api-instance-property
browser-compat: api.Node.nodeValue
---

{{APIRef("DOM")}}

ویژگی **`nodeValue`** از رابط {{domxref("Node")}} مقدار گره جاری را بازگردانده یا تنظیم می‌کند.

## مقدار

یک رشته شامل مقدار گره جاری، در صورت وجود.
برای خود سند، `nodeValue` مقدار `null` را برمی‌گرداند.
برای گره‌های متنی، توضیح (comment) و CDATA، `nodeValue` محتوای گره را برمی‌گرداند.
برای گره‌های ویژگی (attribute)، مقدار ویژگی بازگردانده می‌شود.

جدول زیر مقادیر بازگشتی را برای انواع مختلف گره‌ها نشان می‌دهد.

| گره                                 | مقدار `nodeValue`                    |
| ------------------------------------ | ------------------------------------ |
| {{domxref("CDATASection")}}          | محتوای بخش CDATA                     |
| {{domxref("Comment")}}               | محتوای توضیح                         |
| {{domxref("Document")}}              | `null`                               |
| {{domxref("DocumentFragment")}}      | `null`                               |
| {{domxref("DocumentType")}}          | `null`                               |
| {{domxref("Element")}}               | `null`                               |
| {{domxref("NamedNodeMap")}}          | `null`                               |
| {{domxref("ProcessingInstruction")}} | تمام محتوا به جز هدف (target)         |
| {{domxref("Text")}}                  | محتوای گره متنی                      |

> [!NOTE]
> زمانی که `nodeValue` به صورت `null` تعریف شده باشد، تنظیم آن هیچ اثری ندارد.

## مثال

```html
<div id="d1">Hello world</div>
<!-- Example of comment -->
<output id="result">Not calculated yet.</output>
```

و اسکریپت زیر:

```js
let node = document.querySelector("body").firstChild;
let result = "Node names are:\n";
while (node) {
  result += `Value of ${node.nodeName}: ${node.nodeValue}\n`;
  node = node.nextSibling;
}

const output = document.getElementById("result");
output.innerText = result;
```

{{ EmbedLiveSample("Example", "100%", "250") }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}