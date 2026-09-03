---
title: "ProcessingInstruction: target property"
short-title: target
slug: Web/API/ProcessingInstruction/target
page-type: web-api-instance-property
browser-compat: api.ProcessingInstruction.target
---

{{ApiRef("DOM")}}

ویژگی فقط‌خواندنی **`target`** در رابط {{domxref("ProcessingInstruction")}} نمایانگر برنامه‌ای است که این `ProcessingInstruction` به آن ارسال شده است.

برای مثال:

```html
<?xml version="1.0"?>
```

یک دستور پردازش است که `target` آن `xml` است.

## مقدار

رشته‌ای شامل نام برنامه.

## مثال

### در یک سند XML

```html hidden
<output></output>
```

```js
let parser = new DOMParser();
const doc = parser.parseFromString(
  '<?xml version="1.0"?><test/>',
  "application/xml",
);
const pi = doc.createProcessingInstruction(
  "xml-stylesheet",
  'href="mycss.css" type="text/css"',
);
doc.insertBefore(pi, doc.firstChild);

const output = document.querySelector("output");
output.textContent = `This processing instruction's target is: ${doc.firstChild.target}`;
```

{{EmbedLiveSample("In an XML document", "100%", 50)}}

### در یک سند HTML

خط دستور پردازش به‌عنوان یک شیء {{domxref("Comment")}} در نظر گرفته شده و نمایش داده می‌شود.

```html
<?xml version="1.0"?>
<pre></pre>
```

```js
const node = document.querySelector("pre").previousSibling.previousSibling;
const result = `Node with the processing instruction: ${node.nodeName}: ${node.nodeValue}\n`;
document.querySelector("pre").textContent = result;
```

{{EmbedLiveSample("In an HTML document", "100%", 50)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [DOM API](/en-US/docs/Web/API/Document_Object_Model)