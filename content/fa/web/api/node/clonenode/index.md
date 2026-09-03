---
title: "Node: cloneNode() method"
short-title: cloneNode()
slug: Web/API/Node/cloneNode
page-type: web-api-instance-method
browser-compat: api.Node.cloneNode

{{APIRef("DOM")}}

متد **`cloneNode()`** در رابط {{domxref("Node")}} یک کپی از گره‌ای که این متد روی آن فراخوانی شده است برمی‌گرداند. پارامتر آن مشخص می‌کند که آیا زیردرخت موجود در گره نیز کلون شود یا خیر.

به‌طور پیش‌فرض، کلون کردن یک گره همهٔ ویژگی‌ها (attributes) و مقادیر آن‌ها را کپی می‌کند، از جمله شنونده‌های رویداد (event listeners) که از طریق ویژگی‌ها مشخص شده‌اند. با تنظیم پارامتر `deep`، می‌توانید زیردرخت موجود در گره را نیز کپی کنید. این کار داده‌های داخلی دیگری مانند شنونده‌های رویدادی که با [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) یا ویژگی‌های `onevent` (مثلاً `node.onclick = someFunction`) اضافه شده‌اند، یا تصویر ترسیم‌شده برای یک عنصر {{HTMLElement("canvas")}} را کپی _نمی‌کند_.

متد {{domxref("Document.importNode()")}} نیز یک کپی از گره ایجاد می‌کند. تفاوت در این است که `importNode()` گره را در بافت (context) سند فراخواننده کلون می‌کند، در حالی که `cloneNode()` از سند خود گره‌ای که در حال کلون شدن است استفاده می‌کند. بافت سند، {{domxref("CustomElementRegistry")}} را برای ساخت هر عنصر سفارشی (custom element) تعیین می‌کند. به همین دلیل، برای کلون کردن گره‌هایی که قرار است در سند دیگری استفاده شوند، از `importNode()` روی سند مقصد استفاده کنید. محتوای {{domxref("HTMLTemplateElement.content")}} متعلق به یک سند جداگانه است، بنابراین باید با `document.importNode()` کلون شود تا عناصر سفارشی descendant با استفاده از تعاریف موجود در سند جاری ساخته شوند.

> [!WARNING]
> استفاده از `cloneNode()` ممکن است به شناسه‌های (id) تکراری در یک سند منجر شود! اگر گره اصلی دارای ویژگی `id` باشد و کلون در همان سند قرار گیرد، باید شناسهٔ کلون را به‌گونه‌ای تغییر دهید که یکتا باشد.
>
> همچنین، بسته به اینکه آیا نام‌های تکراری مورد انتظار هستند یا خیر، ممکن است لازم باشد ویژگی‌های `name` نیز تغییر داده شوند.

## نحو (Syntax)

```js-nolint
cloneNode()
cloneNode(deep)
```

### پارامترها

- `deep` {{optional_inline}}
  - : اگر `true` باشد، گره و کل زیردرخت آن،
    از جمله متنی که ممکن است در گره‌های فرزند {{domxref("Text")}} وجود داشته باشد،
    نیز کپی می‌شود.

    اگر `false` باشد یا حذف شود، فقط خود گره کلون می‌شود.
    زیردرخت، از جمله هر متنی که گره شامل آن است، کلون نمی‌شود.

    توجه داشته باشید که `deep` هیچ تأثیری بر {{glossary("void element", "عناصر void")}}،
    مانند عناصر {{HTMLElement("img")}} و {{HTMLElement("input")}} ندارد.

    مقدار پیش‌فرض آن `false` است.

### مقدار بازگشتی

{{domxref("Node")}} جدید کلون‌شده.
گره کلون‌شده والد ندارد و بخشی از سند نیست،
_تا زمانی که_ با استفاده از {{domxref("Node.appendChild()")}} یا روشی مشابه به گره دیگری که بخشی از سند است اضافه شود.

## مثال

### استفاده از cloneNode()

```js
const p = document.getElementById("para1");
const p2 = p.cloneNode(true);
```

### استفاده از cloneNode() با الگوها (templates)

از به‌کار بردن `cloneNode()` روی محتوای یک عنصر {{htmlelement("template")}} خودداری کنید، زیرا اگر الگو شامل عناصر سفارشی باشد، آن‌ها تا زمانی که در سند درج نشوند ارتقا (upgrade) نخواهند یافت.

```js
class MyElement extends HTMLElement {
  constructor() {
    super();
    console.log("MyElement created");
  }
}
customElements.define("my-element", MyElement);

const template = document.createElement("template");
template.innerHTML = `<my-element></my-element>`;

const clone = template.content.cloneNode(true);
// هیچ logی در اینجا نیست؛ my-element در سند الگو تعریف‌نشده است
customElements.upgrade(clone);
// هنوز logی نیست؛ my-element همچنان در سند الگو تعریف‌نشده است
document.body.appendChild(clone);
// «MyElement created» ثبت می‌شود؛ my-element اکنون ارتقا یافته است
```

در عوض، از `document.importNode()` برای کلون کردن محتوای الگو استفاده کنید تا هر عنصر سفارشی با استفاده از تعاریف موجود در سند جاری ارتقا یابد:

```js
const clone = document.importNode(template.content, true);
// «MyElement created» ثبت می‌شود؛ my-element با تعاریف سند ارتقا یافته است
document.body.appendChild(clone);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}