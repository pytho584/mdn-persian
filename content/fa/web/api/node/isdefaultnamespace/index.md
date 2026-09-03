---
title: "Node: isDefaultNamespace() method"
---

---
title: "Node: isDefaultNamespace() method"
short-title: isDefaultNamespace()
slug: Web/API/Node/isDefaultNamespace
page-type: web-api-instance-method
browser-compat: api.Node.isDefaultNamespace
---

{{APIRef("DOM")}}

متد **`isDefaultNamespace()`** از رابط {{domxref("Node")}} یک URI فضای نام را به عنوان آرگومان می‌پذیرد. این متد یک مقدار بولین برمی‌گرداند که اگر آن فضای نام، فضای نام پیش‌فرض روی گره موردنظر باشد `true` و در غیر این صورت `false` است. می‌توان فضای نام پیش‌فرض را با استفاده از {{domxref("Node.lookupNamespaceURI()")}} و با ارسال `null` به عنوان آرگومان به دست آورد.

## Syntax

```js-nolint
isDefaultNamespace(namespaceURI)
```

### Parameters

- `namespaceURI`
  - : رشته‌ای که فضای نام مورد بررسی برای عنصر را مشخص می‌کند. رشته خالی معادل `null` است.
    > [!NOTE]
    > `namespaceURI` یک پارامتر اختیاری نیست، اما می‌تواند `null` باشد.

### Return value

یک مقدار بولین که مقدار بازگشتی `true` یا `false` را نگه می‌دارد و نشان می‌دهد که آیا پارامتر، فضای نام پیش‌فرض است یا نه. این معادل عبارت `node.lookupNamespaceURI(null) === namespaceURI` است.

## Example

> [!NOTE]
> این مثال در یک سند HTML اجرا می‌شود، جایی که ویژگی‌های `xmlns:` نادیده گرفته می‌شوند (به‌جز `xmlns:xlink`). Firefox برای همه عناصر، URI فضای نام را `null` تنظیم می‌کند، در حالی که Chrome و Safari به‌درستی URI فضای نام پیش‌فرض عناصر HTML، SVG و MathML را تنظیم می‌کنند. اگر می‌خواهید آزمایش‌های معنادارتری انجام دهید، می‌توانید یک سند مستقل [SVG](/en-US/docs/Web/SVG) را باز کرده و اسکریپت‌ها را در بافت آن اجرا کنید.

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
    console.log(el, uri, el.isDefaultNamespace(uri));
    row.appendChild(document.createElement("td")).textContent = String(
      el.isDefaultNamespace(uri),
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

- {{domxref("Node.lookupNamespaceURI")}}
- {{domxref("Node.lookupPrefix")}}