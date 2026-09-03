---
title: "Node: lookupNamespaceURI() method"
short-title: lookupNamespaceURI()
slug: Web/API/Node/lookupNamespaceURI
page-type: web-api-instance-method
browser-compat: api.Node.lookupNamespaceURI
---

{{APIRef("DOM")}}

می‌توان از متد **`lookupNamespaceURI()`** در رابط {{domxref("Node")}} یک پیشوند (prefix) به عنوان پارامتر دریافت کرد و URI فضای نام مرتبط با آن پیشوند را در گره موردنظر، در صورت یافتن، بازمی‌گرداند (و در صورت عدم یافتن، `null`). وجود این متد باعث می‌شود که اشیاء `Node` بتوانند به عنوان تفکیک‌گر فضای نام به {{domxref("XPathEvaluator.createExpression()")}} و {{domxref("XPathEvaluator.evaluate()")}} ارسال شوند.

## Syntax

```js-nolint
lookupNamespaceURI(prefix)
```

### Parameters

- `prefix`
  - : پیشوندی که باید جستجو شود. رشتهٔ خالی معادل `null` است و به معنای فضای نام پیش‌فرض می‌باشد.
    > [!NOTE]
    > این پارامتر اختیاری نیست، اما می‌توان آن را `null` قرار داد.

### Return value

رشته‌ای شامل URI فضای نام متناظر با پیشوند.

- اگر گره یک {{domxref("DocumentFragment")}}، {{domxref("DocumentType")}}، {{domxref("Document")}} بدون {{domxref("Document/documentElement", "documentElement")}}، یا {{domxref("Attr")}} بدون عنصر مرتبط باشد، همیشه `null` برمی‌گرداند.
- اگر `prefix` برابر با `"xml"` باشد، مقدار بازگشتی همیشه `"http://www.w3.org/XML/1998/namespace"` است.
- اگر `prefix` برابر با `"xmlns"` باشد، مقدار بازگشتی همیشه `"http://www.w3.org/2000/xmlns/"` است.
- اگر `prefix` برابر با `null` باشد، مقدار بازگشتی URI فضای نام پیش‌فرض است.
- اگر پیشوند یافت نشود، مقدار بازگشتی `null` است.

## Example

> [!NOTE]
> این مثال در یک سند HTML اجرا می‌شود، جایی که ویژگی‌های `xmlns:` نادیده گرفته می‌شوند (به جز `xmlns:xlink`). فایرفاکس URI فضای نام همهٔ عناصر را `null` قرار می‌دهد، در حالی که کروم و سافاری به‌درستی URI فضای نام پیش‌فرض عناصر HTML، SVG و MathML را تنظیم می‌کنند. اگر می‌خواهید آزمایش‌های معنادارتری انجام دهید، می‌توانید یک سند مستقل [SVG](/en-US/docs/Web/SVG) باز کرده و اسکریپت‌ها را در بافت آن اجرا کنید.

```html
<div class="hidden">
  <div>Test HTML element</div>
  <svg>
    <text>Test SVG element</text>
  </svg>
  <svg xmlns:xlink="http://www.w3.org/1999/xlink" id="with-xlink">
    <text>Test SVG element with xlink</text>
  </svg>
  <math>Test MathML element</math>
</div>

<table>
  <thead>
    <tr>
      <th><code>prefix</code></th>
      <th><code>&lt;div&gt;</code></th>
      <th><code>&lt;svg&gt;</code></th>
      <th><code>&lt;svg xmlns:xlink&gt;</code></th>
      <th><code>&lt;math&gt;</code></th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
```

```css hidden
.hidden {
  display: none;
}
```

```js
const htmlElt = document.querySelector("div");
const svgElt = document.querySelector("svg");
const svgEltXLink = document.querySelector("#with-xlink");
const mathElt = document.querySelector("math");

const tbody = document.querySelector("tbody");

for (const prefix of ["xmlns", "xml", "html", "svg", "xlink", "", null]) {
  const row = document.createElement("tr");
  tbody.appendChild(row);
  row.appendChild(document.createElement("td")).textContent =
    JSON.stringify(prefix);
  for (const el of [htmlElt, svgElt, svgEltXLink, mathElt]) {
    console.log(el, prefix, el.lookupNamespaceURI(prefix));
    row.appendChild(document.createElement("td")).textContent = String(
      el.lookupNamespaceURI(prefix),
    );
  }
}
```

{{ EmbedLiveSample('Example','100%',190) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Node.lookupPrefix")}}
- {{domxref("Node.isDefaultNameSpace")}}