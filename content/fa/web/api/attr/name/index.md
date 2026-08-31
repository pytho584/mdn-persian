---
title: "Attr: name property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attr/name"
translated_by: "n8n + AI"
---

---
title: "Attr: name property"
short-title: name
slug: Web/API/Attr/name
page-type: web-api-instance-property
browser-compat: api.Attr.name
---

{{APIRef("DOM")}}

ویژگی فقطخواندنی **`name`** از رابط {{domxref("Attr")}}، _نام واجد شرایط_ یک ویژگی را برمی‌گرداند؛ یعنی نام ویژگی، با پیشوند فضای نام (در صورت وجود) در ابتدای آن. برای مثال، اگر نام محلی `lang` و پیشوند فضای نام `xml` باشد، نام واجد شرایط بازگردانده‌شده `xml:lang` خواهد بود.

نام واجد شرایط همیشه با حروف کوچک (lowercase) است، صرف‌نظر از اینکه در زمان ایجاد ویژگی با چه حروفی نوشته شده باشد.

## مقدار

رشته‌ای (string) که نام واجد شرایط ویژگی را نشان می‌دهد.

## مثال

مثال زیر نام واجد شرایط نخستین ویژگی از دو عنصر اول را، هنگام کلیک روی دکمهٔ مربوطه، نمایش می‌دهد.

### HTML

```html
<svg xml:lang="en-US" class="struct" height="1" width="1">Click me</svg>
<label xml:lang="en-US" class="struct"></label>

<p>
  <button>Show value for &lt;svg&gt;</button>
  <button>Show value for &lt;label&gt;</button>
</p>

<p>
  Qualified name of the attribute <code>xml:lang</code>:
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
    outputEl.value = attribute.name;
  });
  i++;
}
```

{{ EmbedLiveSample('Example','100%',100) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی‌های {{domxref("Attr.localName")}} که بخش محلی نام واجد شرایط ویژگی را برمی‌گرداند، و {{domxref("Attr.prefix")}} که پیشوند فضای نام را برمی‌گرداند.
- ویژگی {{domxref("Element.tagName()")}} که نام واجد شرایط یک {{domxref("Element")}} را برمی‌گرداند.