---
title: "Attr: namespaceURI property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attr/namespaceURI"
translated_by: "n8n + AI"
---

---
title: "Attr: namespaceURI property"
short-title: namespaceURI
slug: Web/API/Attr/namespaceURI
page-type: web-api-instance-property
browser-compat: api.Attr.namespaceURI
---

{{APIRef("DOM")}}

خصوصیت فقط خواندنی **`namespaceURI`** از رابط {{domxref("Attr")}}، URI فضای نام ویژگی را برمی‌گرداند،
یا اگر عنصر در یک فضای نام نباشد، `null` را برمی‌گرداند.

URI فضای نام در زمان ایجاد {{domxref("Attr")}} تنظیم می‌شود و قابل تغییر نیست.
یک ویژگی با فضای نام را می‌توان با استفاده از {{domxref("Element.setAttributeNS()")}} ایجاد کرد.

> [!NOTE]
> یک ویژگی فضای نام خود را از عنصری که به آن متصل است به ارث نمی‌برد.
> اگر به یک ویژگی به صراحت فضای نامی داده نشود، فضای نامی ندارد.

مرورگر به خودی خود اعتبارسنجی فضای نام را مدیریت یا اعمال نمی‌کند. این وظیفه برنامه جاوااسکریپت است
که هرگونه اعتبارسنجی لازم را انجام دهد. همچنین توجه داشته باشید که پیشوند فضای نام، پس از آنکه
با یک گره ویژگی خاصی مرتبط شد، قابل تغییر نیست.

## مقدار

یک رشته حاوی URI فضای نام، یا اگر ویژگی در یک فضای نام نباشد، `null`.

## مثال

مثال زیر نتیجه را برای یک ویژگی با پیشوند روی یک عنصر HTML و یک عنصر SVG نشان می‌دهد.
از آنجایی که HTML با فضای نام کار نمی‌کند، در آن حالت همیشه `null` برمی‌گرداند.
در مورد عنصر SVG، URI فضای نام XML یعنی `http://www.w3.org/XML/1998/namespace` را برمی‌گرداند.

### HTML

```html
<svg xml:lang="en-US" class="struct" height="1" width="1">Click me</svg>
<label xml:lang="en-US" class="struct"></label>

<p>
  <button>Show value for &lt;svg&gt;</button>
  <button>Show value for &lt;label&gt;</button>
</p>

<p>
  Namespace URI of the attribute <code>xml:lang</code>:
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
    outputEl.value = attribute.namespaceURI;
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

- خصوصیات {{domxref("Attr.name")}}، که نام واجد شرایط ویژگی را برمی‌گرداند، {{domxref("Attr.localName")}}، بخش محلی نام، و {{domxref("Attr.prefix")}}، پیشوند فضای نام.
- خصوصیت {{domxref("Element.namespaceURI")}}، معادل این خصوصیت اما برای یک {{domxref("Element")}}.
- متد {{domxref("Element.setAttributeNS()")}}، که یک ویژگی با فضای نام مشخص ایجاد می‌کند.