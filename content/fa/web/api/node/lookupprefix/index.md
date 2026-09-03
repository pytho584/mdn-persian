---
title: "Node: lookupPrefix() method"
short-title: lookupPrefix()
slug: Web/API/Node/lookupPrefix
page-type: web-api-instance-method
browser-compat: api.Node.lookupPrefix
---

{{APIRef("DOM")}}

متد **`lookupPrefix()`** از رابط {{domxref("Node")}} یک رشته حاوی پیشوند (prefix) برای یک URI فضای نام (namespace) مشخص، در صورت وجود، و در غیر این صورت `null` را برمی‌گرداند. در صورت وجود چندین پیشوند، اولین پیشوند بازگردانده می‌شود.

## نحو (Syntax)

```js-nolint
lookupPrefix(namespace)
```

### پارامترها

- `namespace`
  - : رشته‌ای شامل فضای نامی که باید پیشوند آن جستجو شود. رشته خالی معادل `null` است و در هر دو حالت `null` بازگردانده می‌شود.
    > [!NOTE]
    > این پارامتر اختیاری نیست اما می‌توان آن را `null` قرار داد.

### مقدار بازگشتی

رشته‌ای حاوی پیشوند متناظر، یا در صورت عدم یافتن، `null`. اگر `namespace` برابر `null` یا رشته خالی باشد، `lookupPrefix()` مقدار `null` را برمی‌گرداند.

اگر گره از نوع {{domxref("DocumentType")}} یا {{domxref("DocumentFragment")}} باشد، `lookupPrefix()` همیشه `null` برمی‌گرداند.

## مثال

> [!NOTE]
> این مثال در یک سند HTML اجرا می‌شود، جایی که ویژگی‌های `xmlns:` نادیده گرفته می‌شوند (به جز `xmlns:xlink`). فایرفاکس URI فضای نام همه عناصر را `null` قرار می‌دهد، در حالی که کروم و سافاری به طور مناسب URI فضای نام پیش‌فرض عناصر HTML، SVG و MathML را تنظیم می‌کنند. اگر می‌خواهید آزمایش‌های معنادارتری انجام دهید، می‌توانید یک سند مستقل [SVG](/en-US/docs/Web/SVG) باز کرده و اسکریپت‌ها را در بافت آن اجرا کنید.

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
      <th><code>namespaceURI</code></th>
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

for (const uri of [
  "http://www.w3.org/2000/xmlns/",
  "http://www.w3.org/XML/1998/namespace",
  "http://www.w3.org/1999/xhtml",
  "http://www.w3.org/2000/svg",
  "http://www.w3.org/1999/xlink",
  "http://www.w3.org/1998/Math/MathML",
  "",
  null,
]) {
  const row = document.createElement("tr");
  tbody.appendChild(row);
  row.appendChild(document.createElement("td")).textContent =
    JSON.stringify(uri);
  for (const el of [htmlElt, svgElt, svgEltXLink, mathElt]) {
    console.log(el, uri, el.lookupPrefix(uri));
    row.appendChild(document.createElement("td")).textContent = String(
      el.lookupPrefix(uri),
    );
  }
}
```

{{ EmbedLiveSample('Example','100%',190) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}