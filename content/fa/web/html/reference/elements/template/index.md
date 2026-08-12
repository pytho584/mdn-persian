---
title: <template> HTML content template element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/template
translated_by: n8n + AI
---

# \<template> — عنصر قالب محتوای HTML

عنصر **`<template>`** در [HTML](../../../../../../../en-US/docs/Web/HTML/) به عنوان مکانیزمی برای نگهداری قطعات HTML عمل می‌کند؛ قطعاتی که می‌توانند بعداً با JavaScript استفاده شوند یا بلافاصله در shadow DOM تولید شوند.

## Attributes

این عنصر شامل [attribute‌های سراسری](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) می‌شود.

* `shadowrootmode`
  *   : یک [shadow root](../../../../../../../en-US/docs/Glossary/Shadow_tree/) برای عنصر والد می‌سازد. این نسخهٔ اعلانی متد `Element.attachShadow()` است و همان مقادیر enumerated را می‌پذیرد.

      * `open`
        * : DOM داخلی shadow root را در اختیار JavaScript قرار می‌دهد (برای بیشتر موارد استفاده توصیه می‌شود).
      * `closed`
        * : DOM داخلی shadow root را از JavaScript پنهان می‌کند.

      > \[!NOTE] HTML parser برای اولین `<template>` در یک node که این attribute روی مقدار مجاز تنظیم شده باشد، یک شیء `ShadowRoot` در DOM می‌سازد. اگر attribute تنظیم نشده باشد، یا روی مقدار مجاز نباشد — یا اگر قبلاً به صورت declarative یک `ShadowRoot` در همان والد ساخته شده باشد — یک `HTMLTemplateElement` ساخته می‌شود. پس از parsing، دیگر نمی‌توان یک `HTMLTemplateElement` را به shadow root تبدیل کرد، مثلاً با تنظیم `HTMLTemplateElement.shadowRootMode`.

      > \[!NOTE] ممکن است در آموزش‌ها و مثال‌های قدیمی‌تر با attribute غیراستاندارد `shadowroot` مواجه شوید که در Chrome نسخه‌های ۹۰ تا ۱۱۰ پشتیبانی می‌شد. این attribute حذف شده و با attribute استاندارد `shadowrootmode` جایگزین شده است.
* `shadowrootclonable`
  * : مقدار property `clonable` یک `ShadowRoot` ساخته‌شده با این عنصر را روی `true` تنظیم می‌کند. اگر تنظیم شود، یک clone از shadow host (عنصر والد این `<template>`) که با `Node.cloneNode()` یا `Document.importNode()` ساخته شده باشد، شامل shadow root در کپی خواهد بود.
* `shadowrootcustomelementregistry`
  * : property `customElementRegistry` یک `ShadowRoot` ساخته‌شده با این عنصر را به جای registry عناصر سفارشی document، روی `null` تنظیم می‌کند. این کار اجازه می‌دهد یک `CustomElementRegistry` scope‌دار بعداً با `CustomElementRegistry.initialize()` متصل شود.
* `shadowrootdelegatesfocus`
  * : مقدار property `delegatesFocus` یک `ShadowRoot` ساخته‌شده با این عنصر را روی `true` تنظیم می‌کند. اگر این مقدار تنظیم شود و یک عنصر غیرقابل‌فوکوس در shadow tree انتخاب شود، فوکوس به اولین عنصر قابل‌فوکوس در درخت واگذار می‌شود. مقدار پیش‌فرض `false` است.
* `shadowrootreferencetarget` (آزمایشی) (غیراستاندارد)
  * : مقدار property `referenceTarget` یک `ShadowRoot` ساخته‌شده با این عنصر را تنظیم می‌کند. مقدار باید ID یک عنصر داخل shadow DOM باشد. اگر تنظیم شود، ارجاع‌های هدف به عنصر میزبان از خارج shadow DOM باعث می‌شوند عنصر ارجاع‌شده به هدف مؤثر ارجاع به عنصر میزبان تبدیل شود.
* `shadowrootserializable`
  * : مقدار property `serializable` یک `ShadowRoot` ساخته‌شده با این عنصر را روی `true` تنظیم می‌کند. اگر تنظیم شود، می‌توان shadow root را با فراخوانی متدهای `Element.getHTML()` یا `ShadowRoot.getHTML()` و با تنظیم پارامتر `options.serializableShadowRoots` روی `true` سریال‌سازی کرد. مقدار پیش‌فرض `false` است.
* `shadowrootslotassignment`
  * : ویژگی [`slotAssignment`](../../../../../../../en-US/docs/Web/API/ShadowRoot/slotAssignment/) مربوط به یک [`ShadowRoot`](../../../../../../../en-US/docs/Web/API/ShadowRoot/) را تنظیم می‌کند که با استفاده از این عنصر ساخته شده است. این معادل declarative گزینهٔ [`slotAssignment`](../../../../../../../en-US/docs/Web/API/Element/attachShadow/#slotassignment) در متد `Element.attachShadow()` است.
    * `named`
      *   : عنصرها به‌صورت خودکار به عنصرهای `<slot>` داخل این shadow root تخصیص داده می‌شوند. این مقدار پیش‌فرض است.

          عنصرهایی که [`ویژگی slot`](../../../../../../../en-US/docs/Web/API/Element/slot/) دارند، به اولین `<slot>` در template که ویژگی `name` متناظر را دارد تخصیص داده می‌شوند. اگر چند عنصر نام slot یکسانی داشته باشند، همگی به اولین slot در template با آن نام اضافه می‌شوند و به ترتیبی که تعریف شده‌اند رندر می‌شوند. همهٔ عنصرهای بدون نام — یعنی عنصرهایی که ویژگی `slot` ندارند — به ترتیب تعریف به slot پیش‌فرض تخصیص داده می‌شوند. این slot، اولین `<slot>` بدون نام در template است.
    * `manual`
      * : عنصرها به‌صورت دستی با استفاده از `HTMLSlotElement.assign()` به عنصرهای slot خاصی تخصیص داده می‌شوند. هیچ تخصیص خودکاری انجام نمی‌شود.

## Usage notes

این عنصر محتوای مجاز ندارد، چون هر چیزی که در HTML داخل آن قرار می‌گیرد در واقع فرزندِ عنصر `<template>` نمی‌شود. ویژگی `Node.childNodes` عنصر `<template>` همیشه خالی است و شما فقط از طریق ویژگی خاص `content` می‌توانید به آن محتوای تو در تو دسترسی داشته باشید. اما اگر روی عنصر `<template>` متدهایی مثل `Node.appendChild()` یا مشابه آن را صدا بزنید، در این صورت فرزندانی را داخل خود `<template>` قرار داده‌اید که با مدل محتوایی آن مغایرت دارد و در عمل `DocumentFragment` برگشتی توسط ویژگی `content` را به‌روزرسانی نمی‌کند.

به دلیل نحوهٔ parse شدن عنصر `<template>`، همهٔ تگ‌های باز و بستهٔ `<html>`، `<head>` و `<body>` داخل template خطای نحوی هستند و توسط parser نادیده گرفته می‌شوند؛ بنابراین `<template><head><title>Test</title></head></template>` با `<template><title>Test</title></template>` یکسان است.

دو روش اصلی برای استفاده از عنصر `<template>` وجود دارد.

### قطعه سند عنصر `<template>`

به‌طور پیش‌فرض، محتوای عنصر رندر نمی‌شود. رابط متناظر یعنی `HTMLTemplateElement` یک ویژگی استاندارد `content` دارد (بدون معادل به‌صورت attribute). این ویژگی `content` فقط خواندنی است و یک `DocumentFragment` نگه می‌دارد که شامل زیردرخت DOM نمایش‌داده‌شده توسط template است.

متدهای `Node.cloneNode()` و `Document.importNode()` هر دو یک رونوشت از گره می‌سازند. تفاوت این است که `importNode()` گره را در بافت (context) سندی که متد روی آن فراخوانی شده کپی می‌کند، در حالی که `cloneNode()` از سندِ متعلق به گره استفاده می‌کند. بافت سند تعیین می‌کند که از کدام `CustomElementRegistry` برای ساخت custom elementها استفاده شود. به همین دلیل، برای رونوشت گرفتن از fragment مربوط به `content` از `document.importNode()` استفاده کنید تا عنصرهای سفارشی فرزند با تعریف‌های سند فعلی ساخته شوند، نه با سند جداگانه‌ای که محتوای template متعلق به آن است. برای جزئیات بیشتر به مثال‌های صفحهٔ `Node.cloneNode()` مراجعه کنید.

توجه داشته باشید که خودِ ظرف `DocumentFragment` نباید داده‌ای به آن متصل شود. برای جزئیات بیشتر، مثال [«داده‌های روی DocumentFragment کپی نمی‌شوند»](index.md#data_on_the_documentfragment_is_not_cloned) را ببینید.

### Declarative Shadow DOM

اگر المنت `<template>` دارای ویژگی `shadowrootmode` با مقدار `open` یا `closed` باشد، پارسر HTML بلافاصله یک shadow DOM می‌سازد. این المنت در DOM با محتوایش که در یک `ShadowRoot` قرار گرفته جایگزین می‌شود؛ این `ShadowRoot` به المنت والد متصل است. این روش اعلامی معادل فراخوانی `Element.attachShadow()` برای اتصال یک shadow root به یک المنت است.

اگر المنت مقدار دیگری برای `shadowrootmode` داشته باشد یا اصلاً این ویژگی را نداشته باشد، پارسر یک `HTMLTemplateElement` تولید می‌کند. به همین ترتیب، اگر چند shadow root اعلامی وجود داشته باشد، فقط اولین‌شان با `ShadowRoot` جایگزین می‌شود — نمونه‌های بعدی به صورت `HTMLTemplateElement` پارس می‌شوند.

سایر ویژگی‌هایی که با پیشوند `shadowroot` شروع می‌شوند، امکان سفارشی‌سازی اعلامی `ShadowRoot` را فراهم می‌کنند؛ مثلاً کنترل نحوه تخصیص slotها.

## مثال‌ها

### ایجاد ردیف‌های جدول

ابتدا با بخش HTML این مثال شروع می‌کنیم.

```html
<table id="producttable">
  <thead>
    <tr>
      <td>UPC_Code</td>
      <td>Product_Name</td>
    </tr>
  </thead>
  <tbody>
    <!-- existing data could optionally be included here -->
  </tbody>
</table>

<template id="productrow">
  <tr>
    <td class="record"></td>
    <td></td>
  </tr>
</template>
```

ابتدا یک جدول داریم که بعداً با استفاده از کد جاوااسکریپت محتوایی در آن وارد می‌کنیم. سپس template آمده است که ساختار یک قطعه HTML را به عنوان یک ردیف جدول توصیف می‌کند.

حالا که جدول ساخته شده و template تعریف شده، از جاوااسکریپت برای درج ردیف‌ها در جدول استفاده می‌کنیم؛ هر ردیف بر اساس این template ساخته می‌شود.

```js
// Test to see if the browser supports the HTML template element by checking
// for the presence of the template element's content attribute.
if ("content" in document.createElement("template")) {
  // Instantiate the table with the existing HTML tbody
  // and the row with the template
  const tbody = document.querySelector("tbody");
  const template = document.querySelector("#productrow");

  // Clone the new row and insert it into the table
  const clone = document.importNode(template.content, true);
  let td = clone.querySelectorAll("td");
  td[0].textContent = "1235646565";
  td[1].textContent = "Stuff";

  tbody.appendChild(clone);

  // Clone the new row and insert it into the table
  const clone2 = document.importNode(template.content, true);
  td = clone2.querySelectorAll("td");
  td[0].textContent = "0384928528";
  td[1].textContent = "Acme Kidney Beans 2";

  tbody.appendChild(clone2);
} else {
  // Find another way to add the rows to the table because
  // the HTML template element is not supported.
}
```

نتیجه، همان جدول HTML اولیه است که دو ردیف جدید با جاوااسکریپت به آن اضافه شده است.

```css
table {
  background: black;
}
table td {
  background: white;
}
```

### پیاده‌سازی shadow DOM اعلامی

در این مثال، یک هشدار پشتیبانی پنهان در ابتدای مارک‌آپ قرار گرفته است. اگر مرورگر ویژگی `shadowrootmode` را پشتیبانی نکند، این هشدار بعداً با جاوااسکریپت نمایش داده می‌شود. در ادامه، دو المنت `<article>` وجود دارد که هر کدام شامل المنت‌های `<style>` تو در تو با رفتارهای متفاوت هستند. المنت `<style>` اول در کل سند سراسری است. دومی به shadow root ای محدود می‌شود که به دلیل وجود ویژگی `shadowrootmode` به جای المنت `<template>` ایجاد شده است.

```html
<p hidden>
  ⛔ Your browser doesn't support <code>shadowrootmode</code> attribute yet.
</p>
<article>
  <style>
    p {
      padding: 8px;
      background-color: wheat;
    }
  </style>
  <p>I'm in the DOM.</p>
</article>
<article>
  <template shadowrootmode="open">
    <style>
      p {
        padding: 8px;
        background-color: plum;
      }
    </style>
    <p>I'm in the shadow DOM.</p>
  </template>
</article>
```

```js
const isShadowRootModeSupported = Object.hasOwn(
  HTMLTemplateElement.prototype,
  "shadowRootMode",
);

document
  .querySelector("p[hidden]")
  .toggleAttribute("hidden", isShadowRootModeSupported);
```

### Declarative Shadow DOM با واگذاری focus

این مثال نشان می‌دهد که `shadowrootdelegatesfocus` چگونه روی یک shadow root که به صورت declarative ساخته شده اعمال می‌شود و چه تأثیری روی focus می‌گذارد.

کد ابتدا یک shadow root درون یک `<div>` تعریف می‌کند، با استفاده از عنصر `<template>` و attribute `shadowrootmode`. این کار یک `<div>` غیرقابل focus (شامل متن) و یک `<input>` قابل focus را نمایش می‌دهد. همچنین از CSS برای استایل‌دهی به عناصر با `:focus` (به رنگ آبی) و تنظیم استایل پیش‌فرض عنصر میزبان (host) استفاده شده است.

```html
<div>
  <template shadowrootmode="open">
    <style>
      :host {
        display: block;
        border: 1px dotted black;
        padding: 10px;
        margin: 10px;
      }
      :focus {
        outline: 2px solid blue;
      }
    </style>
    <div>Clickable Shadow DOM text</div>
    <input type="text" placeholder="Input inside Shadow DOM" />
  </template>
</div>
```

بلوک کد دوم دقیقاً مشابه است، با این تفاوت که attribute `shadowrootdelegatesfocus` را تنظیم می‌کند. این ویژگی focus را به اولین عنصر focusable در درخت واگذار می‌کند، اگر یک عنصر غیر focusable انتخاب شود.

```html
<div>
  <template shadowrootmode="open" shadowrootdelegatesfocus>
    <style>
      :host {
        display: block;
        border: 1px dotted black;
        padding: 10px;
        margin: 10px;
      }
      :focus {
        outline: 2px solid blue;
      }
    </style>
    <div>Clickable Shadow DOM text</div>
    <input type="text" placeholder="Input inside Shadow DOM" />
  </template>
</div>
```

در انتها، از CSS زیر برای اعمال یک border قرمز روی `<div>` والد در زمان focus استفاده می‌کنیم.

```css
div:focus {
  border: 2px solid red;
}
```

نتایج در زیر نمایش داده شده است. وقتی HTML ابتدا رندر می‌شود، عناصر هیچ استایلی ندارند، همان‌طور که در تصویر اول دیده می‌شود. برای shadow root که `shadowrootdelegatesfocus` روی آن تنظیم نشده، می‌توانید هر جایی به جز `<input>` کلیک کنید و focus تغییر نمی‌کند (اگر `<input>` را انتخاب کنید، تصویر دوم را خواهید دید).

برای shadow root با `shadowrootdelegatesfocus` تنظیم شده، کلیک روی متن (که غیر focusable است) عنصر `<input>` را انتخاب می‌کند، زیرا این اولین عنصر focusable در درخت است. این کار همچنین عنصر والد را نیز focus می‌کند، همان‌طور که در تصویر زیر نشان داده شده است.

### Declarative shadow DOM با تخصیص slot نام‌گذاری شده

این مثال نشان می‌دهد که چگونه عناصر می‌توانند به slot‌هایی در shadow DOM بر اساس attribute [`slot`](../../../../../../../en-US/docs/Web/API/Element/slot/) خود (مطابق با `name` slot) تخصیص داده شوند.

#### HTML

ابتدا یک عنصر \{{HTMLElement("article")\}} تعریف می‌کنیم که اطلاعات عنوان، متادیتا و بدنه مقاله را نمایش می‌دهد.

مقاله شامل یک عنصر `<template>` است که به دلیل وجود attribute `shadowrootmode` به یک shadow root تبدیل می‌شود. نیازی به تنظیم `shadowrootslotassignment` نیست، زیرا تخصیص slot نام‌گذاری شده پیش‌فرض است.

الگو، عناصری را تعریف می‌کند که دارای slotهای نام‌گذاری‌شده برای اطلاعات «header» و «meta» و یک slot بدون نام برای اطلاعات «body» هستند. عناصر با استایل‌های متفاوت نمایش داده می‌شوند تا تشخیص آنها آسان باشد.

```html
<article id="host">
  <template shadowrootmode="open" shadowrootslotassignment="named">
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
  </template>

  <p>
    متن ۱ بدون ویژگی slot. داخل slot پیش‌فرض (بدون نام) درون div «body» قرار می‌گیرد.
  </p>
  <span slot="title">متن مربوط به slot عنوان</span>
  <span slot="meta">متن مربوط به slot متا</span>
  <p>
    متن ۲ بدون ویژگی slot. همچنین داخل slot پیش‌فرض (بدون نام) درون div «body» قرار می‌گیرد.
  </p>
</article>
```

درون همان host، پایین template، چهار عنصر برای پر کردن slotها داریم. عناصر `<span>` دارای ویژگی `slot` هستند که با `name` slotهای داخل template مطابقت دارد و slotهای مربوطه را پر می‌کنند. دو عنصر `<p>` بدون نام هستند، بنابراین هر دو داخل `<slot>` بی‌نام درون عنصر «body» قرار می‌گیرند.

#### نتایج

مثال زیر باید محتوای slotها را در بخش‌های مناسب نمایش دهد.

### Declarative shadow DOM با تخصیص دستی slot

این مثال نشان می‌دهد که چگونه می‌توان عناصر را با استفاده از تخصیص دستی slot به slotهای یک shadow DOM اختصاص داد.

در این روش، هر عنصر باید به‌صورت دستی به یک slot خاص اختصاص داده شود. تخصیص پیش‌فرضی وجود ندارد، بنابراین هر slot که اختصاص داده نشود خالی خواهد ماند.

#### HTML

ابتدا یک هشدار پشتیبانی مخفی داریم. این هشدار بعداً از طریق JavaScript تنظیم می‌شود تا در صورت عدم پشتیبانی مرورگر از ویژگی `shadowrootslotassignment` نمایش داده شود.

```html
<p id="support-warning" hidden>
  ⛔ مرورگر شما هنوز از ویژگی <code>shadowrootslotassignment</code> پشتیبانی نمی‌کند.
</p>
```

سپس، یک عنصر `<article>` تعریف می‌کنیم که اطلاعات عنوان، متاداده و بدنه مقاله را نمایش می‌دهد. این عنصر شامل یک `<template>` است که به دلیل وجود ویژگی `shadowrootmode` به یک shadow root تبدیل می‌شود و چون `shadowrootslotassignment="manual"` تنظیم شده، از تخصیص دستی slot استفاده می‌کند.

الگو عناصری را تعریف می‌کند که دارای slotهایی برای اطلاعات «header»، «meta» و «body» هستند که می‌توان با ویژگی `id` به آنها اشاره کرد. عناصر با استایل‌های متفاوت نمایش داده می‌شوند تا تشخیص آنها آسان باشد.

```html
<article id="host">
  <template shadowrootmode="open" shadowrootslotassignment="manual">
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
  </template>

  <span id="text_title">متن مربوط به slot عنوان</span>
  <span id="text_meta">متن مربوط به slot متا</span>
  <p id="text_body_1">متن ۱ برای slot بدنه.</p>
  <p id="text_body_2">متن ۲ برای slot بدنه.</p>
</article>
```

درون همان host، پایین template، چهار عنصر برای پر کردن slotها داریم. این عناصر با id نیز مشخص شده‌اند.

#### JavaScript

کد جاوااسکریپت برای انتساب دستی slot در زیر نشان داده شده است. ابتدا کد slot های داخل shadow root را دریافت می‌کند، سپس متنی را که باید درج شود دریافت می‌کند، و در نهایت متن را به slot اختصاص می‌دهد. توجه داشته باشید که می‌توانید هر گره را فقط یک بار به یک slot خاص اختصاص دهید، و اگر با استفاده از `HTMLSlotElement.assign()` چند گره را به یک slot اختصاص دهید، ترتیب مشخص‌شدن آن‌ها، ترتیب اضافه‌شدن را تعیین می‌کند.

```js
const host = document.querySelector("#host");
const shadow = host.shadowRoot;

// 1. Target your slots
const titleSlot = shadow.querySelector("#titleSlot");
const metaSlot = shadow.querySelector("#metaSlot");
const bodySlot = shadow.querySelector("#bodySlot");

// 2. Target the Elements to slot
const body1Text = document.querySelector("#text_body_1");
const body2Text = document.querySelector("#text_body_2");
const titleText = document.querySelector("#text_title");
const metaText = document.querySelector("#text_meta");

// 3. Manually assign them
titleSlot.assign(titleText);
metaSlot.assign(metaText);
bodySlot.assign(body2Text, body1Text);
```

اگر انتساب slot پشتیبانی نشود، این کد هشدار پشتیبانیِ پنهان را نمایش می‌دهد.

```js
const isShadowRootSlotAssignmentSupported = Object.hasOwn(
  HTMLTemplateElement.prototype,
  "shadowRootSlotAssignment",
);

document
  .querySelector("p[hidden]")
  .toggleAttribute("hidden", isShadowRootSlotAssignmentSupported);
```

#### نتایج

مثال زیر باید محتوای slot ها را در بخش‌های مناسب نمایش دهد.

> \[!NOTE] اگر attribute به نام `shadowrootslotassignment` پشتیبانی نشود، یک یادداشت هشدار نمایش داده می‌شود و مرورگر از انتساب `named` استفاده می‌کند. با این حال، چون هیچ‌کدام از slot ها یا element های درج‌شونده نام‌گذاری نشده‌اند، همهٔ element ها در slot عنوان درج می‌شوند (چون این اولین slot بدون نام است و بنابراین slot «پیش‌فرض» محسوب می‌شود).

### داده‌های روی DocumentFragment کپی نمی‌شوند

وقتی یک مقدار `DocumentFragment` ارسال می‌شود، `Node.appendChild` و روش‌های مشابه فقط _گره‌های فرزند_ آن مقدار را به گرهٔ هدف منتقل می‌کنند. بنابراین، معمولاً بهتر است event handlerها را به فرزندان یک `DocumentFragment` متصل کنید، نه به خودِ `DocumentFragment`.

#### HTML

```html
<div id="container"></div>

<template id="template">
  <div>Click me</div>
</template>
```

#### JavaScript

```js
const container = document.getElementById("container");
const template = document.getElementById("template");

function clickHandler(event) {
  event.target.append(" — Clicked this div");
}

const firstClone = document.importNode(template.content, true);
firstClone.addEventListener("click", clickHandler);
container.appendChild(firstClone);

const secondClone = document.importNode(template.content, true);
secondClone.children[0].addEventListener("click", clickHandler);
container.appendChild(secondClone);
```

#### نتیجه

چون `firstClone` یک `DocumentFragment` است، هنگام فراخوانی `appendChild` فقط فرزندان آن به `container` اضافه می‌شوند؛ event handlerهای `firstClone` کپی نمی‌شوند. در مقابل، چون یک event handler به اولین _گرهٔ فرزند_ از `secondClone` اضافه شده است، هنگام فراخوانی `appendChild` event handler کپی می‌شود و کلیک روی آن همان‌طور که انتظار می‌رود کار می‌کند.

| [Content categories](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | [Metadata content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#metadata_content)، [flow content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content)، [phrasing content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#phrasing_content)، [script-supporting element](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#script-supporting_elements)     |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| محتواي مجاز                                                                               | هیچ‌کدام (به [نکات استفاده](index.md#usage_notes) مراجعه کنید)                                                                                                                                                                                                                                                                                                                                                                                        |
| حذف تگ                                                                                    | هیچکدام؛ تگ آغاز و پایان هر دو اجباری هستند.                                                                                                                                                                                                                                                                                                                                                                                                          |
| والدین مجاز                                                                               | هر عنصری که [metadata content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#metadata_content)، [phrasing content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#phrasing_content) یا [script-supporting elements](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#script-supporting_elements) را بپذیرد. همچنین می‌تواند فرزند یک عنصر `<colgroup>` باشد که _ندارد_ یک ویژگی `span`. |
| نقش ARIA ضمنی                                                                             | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role)                                                                                                                                                                                                                                                                                                                                                                       |
| نقش‌های ARIA مجاز                                                                         | هیچ `role` مجاز نیست                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| رابط DOM                                                                                  | `HTMLTemplateElement`                                                                                                                                                                                                                                                                                                                                                                                                                                 |

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

* ویژگی‌های HTML [`part`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/part/) و [`exportparts`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/exportparts/)
* عنصر HTML `<slot>`
* شبه‌کلاس‌های CSS `:has-slotted`، `:host`، `:host()` و `:host-context()`
* شبه‌عناصر CSS `::part` و `::slotted`
* رابط `ShadowRoot`
* [استفاده از قالب‌ها و slotها](../../../../../../../en-US/docs/Web/API/Web_components/Using_templates_and_slots/)
* ماژول [CSS scoping](../../../../../../../en-US/docs/Web/CSS/Guides/Scoping/)
* [Shadow DOM اعلانی (به همراه HTML)](../../../../../../../en-US/docs/Web/API/Web_components/Using_shadow_DOM/#declaratively_with_html) در _استفاده از Shadow DOM_
* [Shadow DOM اعلانی](https://web.dev/articles/declarative-shadow-dom) در web.dev (2023)
