---
title: "Attr: localName property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attr/localName"
translated_by: "n8n + AI"
---

---
title: "Attr: localName property"
short-title: localName
slug: Web/API/Attr/localName
page-type: web-api-instance-property
browser-compat: api.Attr.localName
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`localName`** از رابط {{domxref("Attr")}} بخش _محلی_ از _نام کامل_ یک ویژگی را برمی‌گرداند، یعنی نام ویژگی بدون هر فضای نامی که قبل از آن قرار دارد. برای مثال، اگر نام کامل `xml:lang` باشد، نام محلی بازگشتی `lang` است، اگر عنصر آن فضای نام را پشتیبانی کند.

نام محلی همیشه با حروف کوچک است، صرف‌نظر از حروفی که هنگام ایجاد ویژگی استفاده شده است.

> [!NOTE]
> HTML فقط از مجموعه ثابتی از فضای نام‌ها در عناصر SVG و MathML پشتیبانی می‌کند. این‌ها عبارتند از `xml` (برای ویژگی `xml:lang`)، `xlink` (برای ویژگی‌های `xlink:href`، `xlink:show`، `xlink:target` و `xlink:title`) و `xpath`.
>
> این بدان معناست که نام محلی یک ویژگی در یک عنصر HTML همیشه با نام کامل آن برابر است: دونقطه به عنوان کاراکترهای عادی در نظر گرفته می‌شود. در XML، مانند SVG یا MathML، دونقطه پایان پیشوند را نشان می‌دهد و چیزی که قبل از آن است فضای نام است؛ نام محلی ممکن است با نام کامل متفاوت باشد.

## مقدار

یک رشته که بخش محلی از نام کامل ویژگی را نشان می‌دهد.

## مثال

مثال زیر نام محلی اولین ویژگی از دو عنصر اول را نمایش می‌دهد، وقتی که روی دکمه مناسب کلیک می‌کنیم. عنصر {{SVGElement("svg")}} یک عنصر XML است و از فضای نام‌ها پشتیبانی می‌کند که منجر به متفاوت بودن نام محلی (`lang`) از نام کامل `xml:lang` می‌شود. عنصر {{HTMLElement("label")}} یک عنصر HTML است که از فضای نام‌ها پشتیبانی نمی‌کند و در نتیجه نام محلی و نام کامل هر دو `xml:lang` هستند.

### HTML

```html
<svg xml:lang="en-US" class="struct" height="1" width="1">Click me</svg>
<label xml:lang="en-US" class="struct"></label>

<p>
  <button>Show value for &lt;svg&gt;</button>
  <button>Show value for &lt;label&gt;</button>
</p>

<p>
  Local part of the attribute <code>xml:lang</code>:
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
    outputEl.value = attribute.localName;
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

- ویژگی‌های {{domxref("Attr.name")}}، که نام کامل ویژگی را برمی‌گرداند، و {{domxref("Attr.prefix")}}، پیشوند فضای نام را.
- ویژگی {{domxref("Element.localName()")}}، که نام محلی یک {{domxref("Element")}} را برمی‌گرداند.