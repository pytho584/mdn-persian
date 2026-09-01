---
title: "DOMImplementation: createHTMLDocument() method"
short-title: createHTMLDocument()
slug: Web/API/DOMImplementation/createHTMLDocument
page-type: web-api-instance-method
browser-compat: api.DOMImplementation.createHTMLDocument
---

{{ApiRef("DOM")}}

متد **`DOMImplementation.createHTMLDocument()`** یک سند HTML جدید از نوع {{ domxref("Document") }} می‌سازد.

## نحو (Syntax)

```js-nolint
createHTMLDocument()
createHTMLDocument(title)
```

### پارامترها

- `title` {{optional_inline}}
  - : رشته‌ای حاوی عنوانی که برای سند HTML جدید در نظر گرفته می‌شود.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("Document")}} (سند HTML).

## مثال‌ها

این مثال یک سند HTML جدید ایجاد می‌کند و آن را در یک {{HTMLElement("iframe")}} در سند جاری قرار می‌دهد.

در اینجا HTML مربوط به این مثال آمده است:

```html live-sample___new-doc
<button id="create-doc">Create new document</button>
<iframe id="theFrame" src="about:blank"></iframe>
```

پیاده‌سازی جاوااسکریپت تابع `makeDocument()` به این صورت است:

```js live-sample___new-doc
function makeDocument() {
  const frame = document.getElementById("theFrame");

  const doc = document.implementation.createHTMLDocument("New Document");
  const p = doc.createElement("p");
  p.textContent = "This is a new paragraph.";

  try {
    doc.body.appendChild(p);
  } catch (e) {
    console.log(e);
  }

  // Copy the new HTML document into the frame

  const destDocument = frame.contentDocument;
  const srcNode = doc.documentElement;
  const newNode = destDocument.importNode(srcNode, true);

  destDocument.replaceChild(newNode, destDocument.documentElement);
}

document.getElementById("create-doc").addEventListener("click", makeDocument);
```

این کد ایجاد سند HTML جدید و درج محتوایی در آن را مدیریت می‌کند. `createHTMLDocument()` یک سند HTML جدید می‌سازد که {{ HTMLElement("title") }} آن برابر با `"New Document"` است. سپس یک عنصر پاراگراف جدید با محتوایی ساده می‌سازیم و آن را در سند جدید قرار می‌دهیم.

`destDocument` مقدار `contentDocument` فریم را ذخیره می‌کند؛ این همان سندی است که محتوای جدید را در آن تزریق می‌کنیم. دو خط بعدی محتوای سند جدید را به زمینهٔ سند مقصد وارد می‌کنند. در نهایت، `destDocument.replaceChild` محتوای فریم را با محتوای سند جدید جایگزین می‌کند.

{{EmbedLiveSample("new-doc", "", 200)}}

سند بازگردانده‌شده از قبل با HTML زیر ساخته شده است:

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>title</title>
  </head>
  <body>
    …
  </body>
</html>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("DOMImplementation")}} که این متد به آن تعلق دارد.