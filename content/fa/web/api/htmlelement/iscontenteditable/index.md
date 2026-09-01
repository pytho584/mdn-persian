---
title: "HTMLElement: isContentEditable property"
short-title: isContentEditable
slug: Web/API/HTMLElement/isContentEditable
page-type: web-api-instance-property
browser-compat: api.HTMLElement.isContentEditable
---

{{ APIRef("HTML DOM") }}

ویژگی فقط‌خواندنی **`HTMLElement.isContentEditable`** یک مقدار بولی برمی‌گرداند که اگر محتویات عنصر قابل ویرایش باشند، `true` است؛ در غیر این صورت `false` برمی‌گرداند.

## مقدار

یک مقدار بولی.

## مثال‌ها

### HTML

```html
<p id="firstParagraph">Uneditable Paragraph</p>
<p id="secondParagraph" contenteditable="true">Editable Paragraph</p>

<p id="infoText1">Is the first paragraph editable?</p>
<p id="infoText2">Is the second paragraph editable?</p>
```

### JavaScript

```js
const firstParagraph = document.getElementById("firstParagraph");
const secondParagraph = document.getElementById("secondParagraph");

const infoText1 = document.getElementById("infoText1");
const infoText2 = document.getElementById("infoText2");

infoText1.textContent += ` ${firstParagraph.isContentEditable}`;
infoText2.textContent += ` ${secondParagraph.isContentEditable}`;
```

### نتیجه

{{ EmbedLiveSample('Examples', '100%', 160) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement/contentEditable")}}
- ویژگی سراسری [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable)