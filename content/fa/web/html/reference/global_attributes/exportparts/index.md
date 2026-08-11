---
title: "exportparts HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/exportparts"
translated_by: "n8n + AI"
---

ویژگی سراسری (global attribute) **`exportparts`** به شما اجازه می‌دهد عناصری را که درون {{Glossary("shadow tree", "shadow tree‌ها")}} تو در تو قرار دارند انتخاب و استایل کنید. این کار با «صادر کردن» (exporting) نام‌های `part` آن‌ها انجام می‌شود.

shadow tree یک ساختار ایزوله است که شناسه‌ها (identifiers)، کلاس‌ها و استایل‌های داخل آن توسط selectors یا کوئری‌های DOM معمولی قابل دسترسی نیستند. دو ویژگی HTML وجود دارد که می‌توان روی عناصر shadow tree اعمال کرد تا امکان هدف‌گیری استایل‌های CSS از بیرون shadow tree فراهم شود: `part` و `exportparts`.

ویژگی سراسری [`part`](/en-US/docs/Web/HTML/Reference/Global_attributes/part) یک عنصر shadow tree را برای والد (parent) DOM آن قابل مشاهده می‌کند. نام `part` به عنوان پارامتر شبه‌عنصر {{CSSxRef("::part", "::part()")}} استفاده می‌شود. به این ترتیب می‌توانید استایل‌های CSS را از بیرون shadow tree به عناصر داخل آن اعمال کنید. اما شبه‌عنصر `::part()` فقط برای والد مستقیم DOM قابل مشاهده است. یعنی وقتی یک shadow tree درون shadow tree دیگری قرار گرفته است (nested)، `part`ها برای اجداد بالاتر از والد مستقیم قابل دیدن نیستند. ویژگی `exportparts` این محدودیت را برطرف می‌کند.

ویژگی `exportparts` باعث می‌شود `part`های داخل یک shadow tree در خارج از shadow DOM قابل مشاهده باشند. به این فرایند «صادرات» (exporting) گفته می‌شود. `exportparts` روی _shadow host_ عنصر – یعنی همان عنصری که _shadow tree_ به آن متصل است – قرار می‌گیرد. مقدار این ویژگی یک لیست جداشده با کاما از نام‌های `part` موجود در shadow tree است. این نام‌ها برای DOMهای خارج از ساختار فعلی قابل دسترسی می‌شوند.

```html
<template id="ancestor-component">
  <nested-component exportparts="part1, part2, part5"></nested-component>
</template>
```

هنگام صادر کردن یک `part`، می‌توانید نام متفاوتی به آن اختصاص دهید، همانطور که در قطعه‌کد زیر نشان داده شده است. مقدار `exportparts` در واقع یک لیست جداشده با کاما از نگاشت‌های نام `part` است. بنابراین ویژگی `exportparts` در قطعه‌کد بالا معادل `exportparts="part1:part1, part2:part2, part5:part5` است که نشان می‌دهد هر `part` با همان نام صادر می‌شود. در هر نگاشت، رشته‌ی اول نام `part` درون shadow tree و رشته‌ی دوم نامی است که `part` با آن به بیرون نمایش داده می‌شود.

```html
<template id="ancestor-component">
  <nested-component
    exportparts="part1:exposed1, part2:exposed2"></nested-component>
</template>
```

## مثال‌ها

### کامپوننت پایه

برای نشان دادن اینکه چگونه از `exportparts` برای هدف‌گیری `part`ها در کامپوننت‌های تو در تو استفاده می‌شود، یک کامپوننت می‌سازیم و سپس آن را درون کامپوننت دیگری تودرتو می‌کنیم.

#### HTML

ابتدا یک کامپوننت کارت (card) می‌سازیم که سپس آن را با یک کامپوننت دیگر می‌پوشانیم. همچنین از المنت جدیدی که ساخته‌ایم استفاده می‌کنیم و slotها را با متن ساده به عنوان محتوا پر می‌کنیم.

```html
<template id="card-component-template">
  <style>
    :host {
      display: block;
    }
  </style>
  <div class="base" part="base">
    <div part="header"><slot name="header_slot"></slot></div>
    <div part="body"><slot name="body_slot"></slot></div>
    <div part="footer"><slot name="footer_slot"></slot></div>
  </div>
</template>

<card-component>
  <p slot="header_slot">This is the header</p>
  <p slot="body_slot">This is the body</p>
  <p slot="footer_slot">This is the footer</p>
</card-component>
```

#### JavaScript

با JavaScript کامپوننت وب (web component) تعریف‌شده در HTML بالا را تعریف می‌کنیم:

```md
```js
customElements.define(
  "card-component",
  class extends HTMLElement {
    constructor() {
      super(); // Always call super first in constructor
      const template = document.getElementById("card-component-template");
      const shadowRoot = this.attachShadow({
        mode: "open",
      });
      shadowRoot.appendChild(document.importNode(template.content, true));
    }
  },
);
```

#### CSS

ما بخش‌هایی از درخت سایه (`shadow tree`) کامپوننت `<card-component>` را با استفاده از شبه‌المان `::part` استایل می‌دهیم:

```css
::part(body) {
  color: red;
  font-style: italic;
}
```

#### نتایج

### کامپوننت تودرتو

در ادامهٔ مثال `<card-component>` بالا، یک کامپوننت تودرتو می‌سازیم؛ به این صورت که `<card-component>` را درون کامپوننت دیگری به نام `<card-wrapper>` قرار می‌دهیم. سپس با استفاده از ویژگی `exportparts`، بخش‌هایی از کامپوننت تودرتو را که می‌خواهیم از بیرون درخت سایه قابل استایل باشند صادر می‌کنیم.

#### HTML

```html hidden
<template id="card-component-template">
  <style>
    :host {
      display: block;
    }
  </style>
  <div class="base" part="base">
    <div part="header"><slot name="header_slot"></slot></div>
    <div part="body"><slot name="body_slot"></slot></div>
    <div part="footer"><slot name="footer_slot"></slot></div>
  </div>
</template>
```

```html
<template id="card-wrapper">
  <style>
    :host {
      display: block;
    }
  </style>
  <card-component exportparts="base, header, body">
    <slot name="H" slot="header_slot"></slot>
    <slot name="B" slot="body_slot"></slot>
    <slot name="F" slot="footer_slot"></slot>
  </card-component>
</template>
```

ما یک المان سفارشی (`custom element`) `<card-wrapper>` و یک `<card-component>` برای مقایسه قرار می‌دهیم:

```html
<h2>Card wrapper</h2>

<card-wrapper>
  <p slot="H">This is the header</p>
  <p slot="B">This is the body</p>
  <p slot="F">This is the footer</p>
</card-wrapper>

<h2>Card component</h2>

<card-component>
  <p slot="header_slot">This is the header</p>
  <p slot="body_slot">This is the body</p>
  <p slot="footer_slot">This is the footer</p>
</card-component>
```

#### JavaScript

```js hidden
customElements.define(
  "card-component",
  class extends HTMLElement {
    constructor() {
      super(); // Always call super first in constructor
      const template = document.getElementById("card-component-template");
      const shadowRoot = this.attachShadow({
        mode: "open",
      });
      shadowRoot.appendChild(document.importNode(template.content, true));
    }
  },
);
```

```js
customElements.define(
  "card-wrapper",
  class extends HTMLElement {
    constructor() {
      super(); // Always call super first in constructor
      const template = document.getElementById("card-wrapper");
      const shadowRoot = this.attachShadow({
        mode: "open",
      });
      shadowRoot.appendChild(document.importNode(template.content, true));
    }
  },
);
```

#### CSS

حالا می‌توانیم بخش‌های `<card-component>` را مستقیماً و همچنین وقتی درون `<card-wrapper>` قرار گرفته است، به این شکل هدف قرار دهیم:

```css
h2 {
  background-color: #dedede;
}

card-wrapper,
card-component {
  border: 1px dashed blue;
  width: fit-content;
}

::part(body) {
  color: red;
  font-style: italic;
}

::part(header),
::part(footer) {
  font-weight: bold;
}
```

#### نتایج

توجه کنید که در حالت تودرتو، `footer` بولد نیست، چون آن را در `exportparts` قرار نداده‌ایم.

### نمایش بخش‌های نگاشت‌شده

برای تغییر نام بخش‌های صادرشده، یک لیست جدا شده با کاما از بخش‌های نگاشت‌شده قرار می‌دهیم؛ هر بخش نگاشت‌شده شامل نام اصلی و نام صادرشده است که با دونقطه (`:`) از هم جدا شده‌اند:

#### HTML

المان سفارشی `<card-wrapper>` قبلی را با سینتکس نگاشت مجدد به‌روزرسانی می‌کنیم (و `body` را از لیست بخش‌های صادرشده حذف می‌کنیم):
```

```html hidden
<template id="card-component-template">
  <div class="base" part="base">
    <div part="header"><slot name="header_slot"></slot></div>
    <div part="body"><slot name="body_slot"></slot></div>
    <div part="footer"><slot name="footer_slot"></slot></div>
  </div>
</template>

<card-wrapper>
  <p slot="H">This is the header</p>
  <p slot="B">This is the body</p>
  <p slot="F">This is the footer</p>
</card-wrapper>
```

```html
<template id="card-wrapper">
  <card-component
    exportparts="
       base:card__base,
       header:card__header,
       footer:card__footer
     ">
    <span slot="header_slot"><slot name="H"></slot></span>
    <span slot="body_slot"><slot name="B"></slot></span>
    <span slot="footer_slot"><slot name="F"></slot></span>
  </card-component>
</template>
```

#### JavaScript

```js hidden
customElements.define(
  "card-component",
  class extends HTMLElement {
    constructor() {
      super(); // Always call super first in constructor
      const template = document.getElementById("card-component-template");
      const shadowRoot = this.attachShadow({
        mode: "open",
      });
      shadowRoot.appendChild(document.importNode(template.content, true));
    }
  },
);
```

```js
customElements.define(
  "card-wrapper",
  class extends HTMLElement {
    constructor() {
      super(); // Always call super first in constructor
      const template = document.getElementById("card-wrapper");
      const shadowRoot = this.attachShadow({
        mode: "open",
      });
      shadowRoot.appendChild(document.importNode(template.content, true));
    }
  },
);
```

#### CSS

هنگام هدف قرار دادن بخش‌های `<card-component>` از درون `<card-wrapper>`، فقط می‌توان بخش‌های صادرشده را با نام‌های معرفی‌شده‌شان استایل کرد:

```css
/* selects the exported parts name */
::part(card__header) {
  font-weight: bold;
}
/* selects nothing: these part names were not exported */
::part(footer),
::part(body) {
  font-weight: bold;
}
```

#### نتایج

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [`part`](/en-US/docs/Web/HTML/Reference/Global_attributes/part) ویژگی HTML
- عنصرهای HTML `<template>` و `<slot>`
- شبه‌عنصرهای `::part` و `::slotted`
- شبه‌کلاس `:host`
- رابط `ShadowRoot`
- ویژگی `Element.part`
- [استفاده از templateها و slotها](/en-US/docs/Web/API/Web_components/Using_templates_and_slots)
- [ماژول CSS Scoping](/en-US/docs/Web/CSS/Guides/Scoping)