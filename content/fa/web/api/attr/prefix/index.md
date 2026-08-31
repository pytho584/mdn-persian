---
title: "Attr: prefix property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attr/prefix"
translated_by: "n8n + AI"
---

---
title: "Attr: prefix property"
short-title: prefix
slug: Web/API/Attr/prefix
page-type: web-api-instance-property
browser-compat: api.Attr.prefix
---

{{APIRef("DOM")}}

ویژگی فقط خواندنی **`prefix`** از {{domxref("Attr")}}، پیشوند فضای نام (namespace prefix) ویژگی را برمی‌گرداند، یا اگر پیشوندی مشخص نشده باشد، `null` را برمی‌گرداند.

پیشوند همیشه با حروف کوچک (lower case) است، صرف‌نظر از اینکه در زمان ایجاد ویژگی از چه حروفی استفاده شده باشد.

> [!NOTE]
> فقط XML از فضاهای نام پشتیبانی می‌کند. HTML این کار را نمی‌کند. به این معنی که پیشوند یک ویژگی از یک عنصر HTML همیشه `null` خواهد بود.

همچنین، فقط فضاهای نام `xml` (برای ویژگی `xml:lang`)، `xlink` (برای ویژگی‌های `xlink:href`، `xlink:show`، `xlink:target` و `xlink:title`) و `xpath` پشتیبانی می‌شوند، و فقط روی عناصر SVG و MathML.

## مقدار

یک رشته (string) که شامل پیشوند فضای نامی است که ویژگی به آن تعلق دارد. اگر هیچکدام نباشد، `null` را برمی‌گرداند.

## مثال

### HTML

```html
<svg xml:lang="en-US" class="struct" height="1" width="1">Click me</svg>
<label xml:lang="en-US" class="struct"></label>

<p>
  <button>نمایش مقدار برای &lt;svg&gt;</button>
  <button>نمایش مقدار برای &lt;label&gt;</button>
</p>

<p>
  پیشوند ویژگی <code>xml:lang</code>:
  <output id="result">هیچکدام.</output>
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
    outputEl.value = attribute.prefix;
  });
  i++;
}
```

{{ EmbedLiveSample('Example','100%',100) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی‌های {{domxref("Attr.name")}} که نام واجد شرایط (qualified name) ویژگی را برمی‌گرداند، و {{domxref("Attr.localName")}}، نام محلی آن.
- ویژگی {{domxref("Element.prefix()")}} که پیشوند فضای نام یک {{domxref("Element")}} را برمی‌گرداند.