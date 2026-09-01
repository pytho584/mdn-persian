---
title: "Element: attachShadow() method"
short-title: attachShadow()
slug: Web/API/Element/attachShadow
page-type: web-api-instance-method
browser-compat: api.Element.attachShadow
---

{{APIRef("Shadow DOM")}}

متد **`attachShadow()`** از رابط {{domxref("Element")}} یک درخت DOM سایه (Shadow DOM tree) را به عنصر مشخص‌شده متصل می‌کند و یک ارجاع به {{domxref("ShadowRoot")}} آن برمی‌گرداند.

## نحو (Syntax)

```js-nolint
attachShadow(options)
```

### پارامترها

- `options`
  - : یک شیء شامل فیلدهای زیر:
    - `mode`
      - : یک رشته که _حالت محصورسازی (encapsulation mode)_ برای درخت DOM سایه را مشخص می‌کند.
        می‌تواند یکی از موارد زیر باشد:
        - `open`
          - : عناصر داخل ریشه سایه از طریق JavaScript با استفاده از ویژگی {{domxref("Element.shadowRoot","shadowRoot")}} عنصر قابل دسترسی هستند.
        - `closed`
          - : عناصر داخل ریشه سایه از طریق JavaScript با استفاده از ویژگی {{domxref("Element.shadowRoot","shadowRoot")}} که به `null` تنظیم می‌شود قابل دسترسی نیستند.

    - `clonable` {{Optional_Inline}}
      - : یک بولی (boolean) که مشخص می‌کند آیا ریشه سایه قابل کلون کردن است یا خیر: وقتی `true` تنظیم شود، میزبان سایه که با {{domxref("Node.cloneNode()")}} یا {{domxref("Document.importNode()")}} کلون می‌شود، ریشه سایه را نیز در کپی خود شامل می‌شود. مقدار پیش‌فرض آن `false` است.

    - `customElementRegistry` {{Optional_Inline}}
      - : یک {{DOMxRef('CustomElementRegistry')}} که به عنوان [ثبت عناصر سفارشی حوزه‌دار (scoped custom element registry)](/en-US/docs/Web/API/Web_components/Using_custom_elements#scoped_custom_element_registries) ریشه سایه متصل استفاده می‌شود.
        اگر `null` یا `undefined` باشد، ریشه سایه از ثبت جهانی که توسط {{domxref("Window.customElements")}} ارجاع داده می‌شود استفاده می‌کند.

    - `delegatesFocus` {{Optional_Inline}}
      - : یک بولی که وقتی `true` تنظیم شود، رفتاری را مشخص می‌کند که مشکلات عناصر سفارشی در مورد قابلیت دریافت فوکوس را کاهش می‌دهد.
        وقتی بخشی از DOM سایه که قابل فوکوس نیست کلیک شود، اولین بخش قابل فوکوس فوکوس می‌گیرد و میزبان سایه هر استایل `:focus` موجود را دریافت می‌کند. مقدار پیش‌فرض آن `false` است.

    - `referenceTarget` {{Optional_Inline}} {{Experimental_Inline}}
      - : یک رشته که هدف مؤثر هر ارجاع عنصری که از خارج عنصر میزبان به میزبان سایه انجام می‌شود را مشخص می‌کند. مقدار باید شناسه (`id`) یک عنصر داخل DOM سایه باشد. اگر تنظیم شود، ارجاع‌های هدف به عنصر میزبان از خارج DOM سایه باعث می‌شوند عنصر مرجع‌شده به هدف مؤثر ارجاع به عنصر میزبان تبدیل شود.

    - `serializable` {{Optional_Inline}}
      - : یک بولی که وقتی `true` تنظیم شود، نشان می‌دهد ریشه سایه قابل سریال‌سازی است.
        اگر تنظیم شود، ریشه سایه ممکن است با فراخوانی متدهای {{DOMxRef('Element.getHTML()')}} یا {{DOMxRef('ShadowRoot.getHTML()')}} با پارامتر `options.serializableShadowRoots` برابر `true` سریال‌سازی شود.
        مقدار پیش‌فرض آن `false` است.

    - `slotAssignment` {{Optional_inline}}
      - : یک رشته که _حالت تخصیص اسلات (slot assignment mode)_ را برای درخت DOM سایه مشخص می‌کند. می‌تواند یکی از موارد زیر باشد:
        - `named`
          - : عناصر به طور خودکار به عناصر {{HTMLElement("slot")}} داخل این ریشه سایه تخصیص می‌یابند.
            هر فرزند سطح بالای میزبان که دارای ویژگی `slot` مطابق با ویژگی `name` یک `<slot>` داخل این ریشه سایه باشد به آن اسلات تخصیص می‌یابد.
            هر فرزند سطح بالای میزبان که ویژگی `slot` نداشته باشد به اولین `<slot>` بدون ویژگی `name` (اسلات پیش‌فرض) تخصیص می‌یابد، در صورت وجود. این مقدار پیش‌فرض است.
        - `manual`
          - : عناصر به صورت دستی با استفاده از {{domxref("HTMLSlotElement.assign()")}} به عناصر اسلات خاص تخصیص می‌یابند. هیچ تخصیص خودکاری انجام نمی‌شود.

### مقدار بازگشتی

یک شیء {{domxref("ShadowRoot")}} برمی‌گرداند.

### استثناها (Exceptions)

- `NotSupportedError` {{domxref("DOMException")}}
  - : این خطا ممکن است وقتی پرتاب شود که سعی کنید یک ریشه سایه را به عنصری متصل کنید که:
    - خارج از فضای نام HTML است یا نمی‌تواند سایه به آن متصل شود.
    - تعریف عنصر آن دارای ویژگی استاتیک `disabledFeatures` با مقدار `"shadow"` باشد.
    - از قبل دارای یک ریشه سایه است که به صورت اعلامی (declaratively) ایجاد نشده است.
    - دارای یک [ریشه سایه اعلامی (declarative shadow root)](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) است اما `mode` مشخص‌شده با حالت موجود مطابقت ندارد.
    - در حالی که مقداری برای `customElementRegistry` ارسال شده که `null` یا یک ثبت حوزه‌دار محلی (که با `new CustomElementRegistry()` ساخته‌اید) نیست. خطا اگر ثبت جهانی را ارسال کنید پرتاب می‌شود.

## توضیحات

متد **`Element.attachShadow()`** یک درخت DOM سایه را به عنصر مشخص‌شده متصل می‌کند و یک ارجاع به {{domxref("ShadowRoot")}} آن برمی‌گرداند.

این مکانیسم برنامه‌نویسی برای ایجاد یک `ShadowRoot` است که گره ریشه یک [DOM سایه](/en-US/docs/Web/API/Web_components/Using_shadow_DOM) متصل به یک عنصر میزبان است (همچنین می‌توان یک `ShadowRoot` را به صورت اعلامی با استفاده از ویژگی [`shadowrootmode`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootmode) عنصر {{htmlelement("template")}} ایجاد کرد). این متد برای ایجاد [عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) استفاده می‌شود.

### عناصری که می‌توانید به آنها سایه متصل کنید

توجه داشته باشید که نمی‌توانید یک ریشه سایه را به هر نوع عنصری متصل کنید. برخی به دلایل امنیتی نمی‌توانند DOM سایه داشته باشند (مثلاً {{htmlelement("a")}}).

لیست زیر عناصری هستند که می‌توانید یک ریشه سایه به آنها متصل کنید:

- هر عنصر سفارشی مستقل (autonomous custom element) با یک [نام معتبر](https://html.spec.whatwg.org/multipage/custom-elements.html#valid-custom-element-name)
- {{htmlelement("article")}}
- {{htmlelement("aside")}}
- {{htmlelement("blockquote")}}
- {{htmlelement("body")}}
- {{htmlelement("div")}}
- {{htmlelement("footer")}}
- {{htmlelement("Heading_Elements", "h1")}}
- {{htmlelement("Heading_Elements", "h2")}}
- {{htmlelement("Heading_Elements", "h3")}}
- {{htmlelement("Heading_Elements", "h4")}}
- {{htmlelement("Heading_Elements", "h5")}}
- {{htmlelement("Heading_Elements", "h6")}}
- {{htmlelement("header")}}
- {{htmlelement("main")}}
- {{htmlelement("nav")}}
- {{htmlelement("p")}}
- {{htmlelement("section")}}
- {{htmlelement("span")}}

### فراخوانی این متد بر روی عنصری که از قبل میزبان سایه است

این متد ممکن است بر روی عنصری که از قبل دارای یک [ریشه سایه اعلامی](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) است فراخوانی شود، به شرطی که `mode` مشخص‌شده با حالت موجود مطابقت داشته باشد. در این صورت {{domxref("ShadowRoot")}} موجود پاک شده و بازگردانده می‌شود. این امکان را برای مواردی فراهم می‌کند که مثلاً رندر سمت سرور (server-side rendering) از قبل یک ریشه سایه به صورت اعلامی ایجاد کرده است و سپس کد سمت کلاینت سعی می‌کند دوباره ریشه را متصل کند.

در غیر این صورت، فراخوانی `attachShadow()` بر روی عنصری که از قبل یک ریشه سایه دارد یک استثنا پرتاب می‌کند.

### ریشه‌های سایه باز و بسته

یک ریشه سایه می‌تواند با یک حالت محصورسازی [mode](#mode) که به صورت `open` یا `closed` مشخص می‌شود متصل شود.

اگر آرگومان `{mode: "open"}` ارسال شود، ویژگی {{domxref("Element.shadowRoot","shadowRoot")}} عنصر میزبان می‌تواند پس از آن برای دریافت ریشه سایه متصل شده استفاده شود. این می‌تواند برای دسترسی به عناصر در DOM سایه استفاده شود:

```js
element.attachShadow({ mode: "open" });
element.shadowRoot; // یک شیء ShadowRoot برمی‌گرداند
```

اگر `{mode: "closed"}` ارسال شود، ویژگی {{domxref("Element.shadowRoot","shadowRoot")}} عنصر به `null` تنظیم می‌شود. توجه داشته باشید که JavaScript همچنان می‌تواند با ذخیره مقدار بازگشتی تابع به یک ریشه سایه بسته دسترسی پیدا کند.

```js
element.attachShadow({ mode: "closed" });
element.shadowRoot; // null برمی‌گرداند
```

## نمونه‌ها

### عنصر سفارشی شمارش کلمات

مثال زیر از دموی [word-count-web-component](https://github.com/mdn/web-components-examples/tree/main/word-count-web-component) ما گرفته شده است ([همچنین به صورت زنده ببینید](https://mdn.github.io/web-components-examples/word-count-web-component/)). می‌بینید که ما از `attachShadow()` در وسط کد برای ایجاد یک ریشه سایه استفاده می‌کنیم و سپس محتویات عنصر سفارشی خود را به آن متصل می‌کنیم.

```js
// Create a class for the element
class WordCount extends HTMLParagraphElement {
  constructor() {
    // Always call super first in constructor
    super();

    // count words in element's parent element
    const wcParent = this.parentNode;

    function countWords(node) {
      const text = node.innerText || node.textContent;
      return text
        .trim()
        .split(/\s+/g)
        .filter((a) => a.trim().length > 0).length;
    }

    const count = `Words: ${countWords(wcParent)}`;

    // Create a shadow root
    const shadow = this.attachShadow({ mode: "open" });

    // Create text node and add word count to it
    const text = document.createElement("span");
    text.textContent = count;

    // Append it to the shadow root
    shadow.appendChild(text);

    // Update count when element content changes
    this.parentNode.addEventListener("input", () => {
      text.textContent = `Words: ${countWords(wcParent)}`;
    });
  }
}

// Define the new element
customElements.define("word-count", WordCount, { extends: "p" });
```

### غیرفعال کردن DOM سایه

اگر عنصر دارای یک ویژگی استاتیک به نام `disabledFeatures` باشد که یک آرایه حاوی رشته `"shadow"` است، آنگاه فراخوانی `attachShadow()` یک استثنا پرتاب می‌کند.

مثال:

```js
class MyCustomElement extends HTMLElement {
  // Disable shadow DOM for this element.
  static disabledFeatures = ["shadow"];

  constructor() {
    super();
  }

  connectedCallback() {
    // Create a shadow root.
    // This will throw an exception.
    const shadow = this.attachShadow({ mode: "open" });
  }
}

// Define the new element
customElements.define("my-custom-element", MyCustomElement);
```

### تخصیص اسلات نام‌گذاری‌شده (Named slot assignment)

این مثال تخصیص اسلات نام‌گذاری‌شده را نشان می‌دهد.

#### ایجاد کامپوننت وب

این کد یک کامپوننت وب ایجاد می‌کند که دارای سه اسلات نام‌گذاری‌شده برای عنوان، فراداده (metadata) و بخش بدنه یک مقاله است.

`ShadowRoot` در سازنده عنصر سفارشی متصل می‌شود. نیازی به تنظیم صریح گزینه `slotAssignment: "named"` نیست زیرا این مقدار پیش‌فرض است.

```js
class MyArticle extends HTMLElement {
  constructor() {
    super();
    // Attach the shadow root
    this.attachShadow({ mode: "open" /* , slotAssignment: "named" */ });
  }

  connectedCallback() {
    this.render();
  }

  render() {
    // Define the internal structure and styles
    this.shadowRoot.innerHTML = `
      <style>
        .header {
          background-color: plum;
        }
        .meta {
          background-color: green;
        }
        .body {
          background-color: lightblue;
        }
      </style>

      <h2 class="header">
        <slot name="title"></slot>
      </h2>

      <div class="meta">
        <slot name="meta"></slot>
      </div>

      <div class="body">
        <slot></slot>
      </div>
    `;
  }
}

// Register the component
customElements.define("my-article", MyArticle);
```

#### استفاده از کامپوننت وب

HTML زیر از کامپوننت وب `<my-article>` که ایجاد کردیم استفاده می‌کند. عناصر تو در تو بر اساس تطابق نام در اسلات‌های کامپوننت رندر می‌شوند. عناصر بدون نام در اسلات بدون نام کامپوننت (بدنه) رندر می‌شوند.

```html
<my-article>
  <span slot="title">Text for the title slot</span>
  <span slot="meta">Text for the meta slot</span>

  <p>
    Text 1 with no slot attribute. Goes into default (unnamed) slot inside the
    "body" div.
  </p>
  <p>
    Text 2 with no slot attribute. Also goes into default (unnamed) slot inside
    the "body" div.
  </p>
</my-article>
```

#### نتایج

مثال زیر باید محتوای اسلات‌ها را در بخش‌های مناسب نشان دهد.

{{EmbedLiveSample('Named slot assignment','100', '220px')}}

### تخصیص اسلات بدون نام (Unnamed slot assignment)

این مثال [تخصیص دستی اسلات](/en-US/docs/Web/API/HTMLSlotElement/assign) را نشان می‌دهد. با این رویکرد، هر عنصر باید به صورت دستی با استفاده از {{domxref("HTMLSlotElement.assign()")}} به یک اسلات خاص تخصیص داده شود. هیچ تخصیص پیش‌فرضی وجود ندارد، بنابراین هر اسلاتی که تخصیص داده نشود خالی خواهد بود.

#### HTML

ابتدا یک هشدار پشتیبانی مخفی داریم که اگر مرورگر از `slotAssignment: "manual"` پشتیبانی نکند از طریق JavaScript نمایش داده می‌شود.

```html
<p id="support-warning" hidden>
  ⛔ Your browser doesn't support manual slot assignment (named assignment is
  used).
</p>
```

سپس، عنصر سفارشی `<my-article>` خود را با عناصر فرزند برای عنوان، فراداده و محتوای بدنه تعریف می‌کنیم. هر فرزند با `id` شناسایی می‌شود؛ بر خلاف تخصیص اسلات نام‌گذاری‌شده، نیازی به ویژگی `slot` نیست.

```html
<my-article>
  <span id="text_title">Text for the title slot</span>
  <span id="text_meta">Text for the meta slot</span>
  <p id="text_body_1">Text 1 for body slot.</p>
  <p id="text_body_2">Text 2 for body slot.</p>
</my-article>
```

#### JavaScript

عنصر سفارشی یک ریشه سایه با `slotAssignment: "manual"` متصل می‌کند. DOM سایه شامل اسلات‌های بدون نام است که با `id` شناسایی می‌شوند. متد `assignSlots()` به صورت دستی عناصر DOM سبک (light DOM) را به اسلات‌ها تخصیص می‌دهد. توجه داشته باشید که چندین گره می‌توانند به یک اسلات تخصیص داده شوند - ترتیب مشخص‌شده، ترتیب رندر را تعیین می‌کند.

```js
class MyArticle extends HTMLElement {
  constructor() {
    super();
    this.attachShadow({ mode: "open", slotAssignment: "manual" });
  }

  connectedCallback() {
    this.render();
    this.assignSlots();
  }

  render() {
    this.shadowRoot.innerHTML = `
      <style>
        .header {
          background-color: plum;
        }
        .meta {
          background-color: green;
        }
        .body {
          background-color: lightblue;
        }
      </style>

      <h2 class="header">
        <slot id="titleSlot"></slot>
      </h2>

      <div class="meta">
        <slot id="metaSlot"></slot>
      </div>

      <div class="body">
        <slot id="bodySlot"></slot>
      </div>
    `;
  }

  assignSlots() {
    // 1. Target your slots
    const titleSlot = this.shadowRoot.querySelector("#titleSlot");
    const metaSlot = this.shadowRoot.querySelector("#metaSlot");
    const bodySlot = this.shadowRoot.querySelector("#bodySlot");

    // 2. Target your light DOM elements
    const titleText = this.querySelector("#text_title");
    const metaText = this.querySelector("#text_meta");
    const body1Text = this.querySelector("#text_body_1");
    const body2Text = this.querySelector("#text_body_2");

    // 3. Manually assign them
    titleSlot.assign(titleText);
    metaSlot.assign(metaText);
    bodySlot.assign(body2Text, body1Text);
  }
}

customElements.define("my-article", MyArticle);
```

این کد بررسی می‌کند که آیا ویژگی {{domxref("ShadowRoot.slotAssignment")}} تعریف شده است یا خیر و در صورت عدم تعریف، هشدار را نمایش می‌دهد.

```js
const isSlotAssignmentSupported = Object.hasOwn(
  ShadowRoot.prototype,
  "slotAssignment",
);

document
  .querySelector("p[hidden]")
  .toggleAttribute("hidden", isSlotAssignmentSupported);
```

#### نتایج

مثال زیر باید محتوای اسلات‌ها را در بخش‌های مناسب نشان دهد.

{{EmbedLiveSample('Unnamed slot assignment','100', '220px')}}

> [!NOTE]
> اگر تخصیص دستی اسلات پشتیبانی نشود، یک هشدار نمایش داده می‌شود و مرورگر از تخصیص `named` استفاده می‌کند. با این حال، از آنجایی که هیچ یک از عناصر DOM سبک دارای ویژگی `slot` نیستند، همه آنها در اولین اسلات بدون نام (اسلات عنوان) درج می‌شوند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("ShadowRoot.mode")}}
- {{domxref("ShadowRoot.delegatesFocus")}}
- {{domxref("ShadowRoot.slotAssignment")}}
- اتصال یک ریشه سایه به صورت اعلامی با ویژگی [`shadowrootmode`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootmode) عنصر [`<template>`](/en-US/docs/Web/HTML/Reference/Elements/template)
- [DOM سایه اعلامی (Declarative shadow DOM)](https://web.dev/articles/declarative-shadow-dom) در web.dev (2023)