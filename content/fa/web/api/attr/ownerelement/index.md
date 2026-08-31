---
title: "Attr: ownerElement property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attr/ownerElement"
translated_by: "n8n + AI"
---

---
title: "Attr: ownerElement property"
short-title: ownerElement
slug: Web/API/Attr/ownerElement
page-type: web-api-instance-property
browser-compat: api.Attr.ownerElement
---

{{APIRef("DOM")}}

ویژگی فقط‑خواندنی **`ownerElement`** از رابط {{domxref("Attr")}}، {{domxref("Element")}}ای را که ویژگی به آن تعلق دارد، برمی‌گرداند.

## مقدار

{{domxref("Element")}}ای که ویژگی به آن تعلق دارد، یا اگر ویژگی به هیچ عنصری متصل نباشد، `null`.

## مثال

مثال زیر، نام واجد شرایط عنصر دو عنصر اول را هنگامی که روی دکمه مناسب کلیک می‌کنیم، نمایش می‌دهد.

### HTML

```html
<svg xml:lang="en-US" class="struct" height="1" width="1">Click me</svg>
<label xml:lang="en-US" class="struct"></label>

<p>
  <button>Show value for &lt;svg&gt;</button>
  <button>Show value for &lt;label&gt;</button>
</p>

<p>
  Qualified name of the owner element of the attribute <code>xml:lang</code>:
  <output id="result">None.</output>
</p>
```

### JavaScript

```js
const elements = document.querySelectorAll(".struct");
const buttons = document.querySelectorAll("button");
const outputEl = document.querySelector("#result");

let i = 0;
for (const button of buttons) {
  const element = elements[i];
  button.addEventListener("click", () => {
    const attribute = element.attributes[0];
    outputEl.value = attribute.ownerElement.tagName.toLowerCase();
  });
  i++;
}
```

{{ EmbedLiveSample('Example','100%',100) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}