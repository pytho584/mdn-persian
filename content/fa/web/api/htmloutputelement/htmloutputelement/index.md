---
title: "HTMLOutputElement: HTMLOutputElement() constructor"
short-title: HTMLOutputElement()
slug: Web/API/HTMLOutputElement/HTMLOutputElement
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.HTMLOutputElement.HTMLOutputElement
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

سازندهٔ **`HTMLOutputElement()`** یک شیء جدید {{domxref("HTMLOutputElement")}} ایجاد می‌کند.

> [!NOTE]
> در حال حاضر فقط سافاری این سازنده را پیاده‌سازی کرده است، بنابراین برای سازگاری بیشتر توصیه می‌شود از {{domxref("Document.createElement()")}} استفاده کنید — به [مثال زیر](#creating_an_output_element_programmatically) مراجعه کنید.

## Syntax

```js-nolint
new HTMLOutputElement()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء جدید {{domxref("HTMLOutputElement")}}.

### استثناها

- {{jsxref("TypeError")}}
  - : در مرورگرهایی که از این سازنده پشتیبانی نمی‌کنند، با پیغام `"Illegal constructor"` پرتاب می‌شود.

## مثال‌ها

### ایجاد یک عنصر output به صورت برنامه‌نویسی

> [!NOTE]
> در عمل، معمولاً عناصر {{htmlelement("output")}} را با استفاده از {{domxref("Document.createElement()")}} ایجاد می‌کنید تا این سازنده، زیرا `createElement()` در همه مرورگرها پشتیبانی می‌شود.

این مثال یک عنصر {{htmlelement("output")}} را با استفاده از سازندهٔ `HTMLOutputElement()` ایجاد می‌کند و آن را در فرمی که دو عدد را با هم جمع می‌کند، قرار می‌دهد.

```html
<form id="my-form">
  <label>
    Number one
    <input type="number" id="a" value="5" />
  </label>
  +
  <label>
    Number two
    <input type="number" id="b" value="3" />
  </label>
  =
  <span id="output-container"></span>
</form>
<p id="warning" hidden>
  ⚠️ Your browser does not support the
  <code>HTMLOutputElement()</code> constructor.
</p>
```

```css hidden
body {
  font-family: system-ui;
}

input {
  width: 3rem;
  font-size: inherit;
}

p {
  padding: 0.25rem;
  background-color: #fff2cc;
}
```

```js
try {
  new HTMLOutputElement();
} catch {
  document.getElementById("warning").hidden = false;
}

const output = new HTMLOutputElement();
output.id = "result";
output.setAttribute("for", "a b");
document.getElementById("output-container").appendChild(output);

function updateResult() {
  const a = document.getElementById("a");
  const b = document.getElementById("b");
  output.value = a.valueAsNumber + b.valueAsNumber;
}

document.getElementById("my-form").addEventListener("input", updateResult);
updateResult();
```

{{EmbedLiveSample("creating_an_output_element_programmatically", "", "150")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLOutputElement")}}
- {{HTMLElement("output")}}
- {{domxref("Document.createElement()")}}