---
title: "Attr: value property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attr/value"
translated_by: "n8n + AI"
---

---
title: "Attr: value property"
short-title: value
slug: Web/API/Attr/value
page-type: web-api-instance-property
browser-compat: api.Attr.value
---

{{APIRef("DOM")}}

ویژگی **`value`** از رابط {{domxref("Attr")}} حاوی مقدار ویژگی است.

## مقدار

یک رشته که مقدار ویژگی را نشان می‌دهد.

## مثال

مثال زیر مقدار فعلی ویژگی `test` را نمایش می‌دهد. با کلیک روی دکمه، این مقدار به مقدار دیگری تغییر می‌کند و دوباره خوانده می‌شود تا مقدار نمایش‌داده‌شده به‌روزرسانی شود.

### HTML

```html
<label test="initial value"></label>

<button>Click me to set test to <code>"a new value"</code>…</button>

<p>
  Current value of the <code>test</code> attribute:
  <output id="result">None.</output>
</p>
```

### JavaScript

```js
const element = document.querySelector("label");
const button = document.querySelector("button");
const result = document.querySelector("#result");

const attribute = element.attributes[0];
result.value = attribute.value;

button.addEventListener("click", () => {
  attribute.value = "a new value";
  result.value = attribute.value;
});
```

{{ EmbedLiveSample('Example','100%',100) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}