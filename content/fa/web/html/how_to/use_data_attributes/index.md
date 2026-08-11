---
title: "Use data attributes"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/How_to/Use_data_attributes"
translated_by: "n8n + AI"
---

HTML به‌گونه‌ای طراحی شده که برای ذخیره‌سازی داده‌هایی که باید با یک عنصر خاص مرتبط باشند اما نیازی به معنای مشخصی ندارند، قابلیت توسعه‌پذیری دارد. [`data-*` attributes](/en-US/docs/Web/HTML/Reference/Global_attributes/data-*) به ما امکان می‌دهند اطلاعات اضافی را روی عناصر استاندارد و معنادار HTML ذخیره کنیم، بدون اینکه نیاز به روش‌های غیراستاندارد مانند attributeهای اضافی یا پراپرتی‌های اضافی روی DOM داشته باشیم.

## نحو HTML

نحو آن ساده است. هر attribute روی هر عنصر که نامش با `data-` شروع شود، یک data attribute محسوب می‌شود. فرض کنید چند مقاله دارید و می‌خواهید اطلاعات اضافی‌ای ذخیره کنید که نمایش بصری ندارند. کافی‌ست از `data` attributes استفاده کنید:

```html
<main>
  <article
    id="electric-cars"
    data-columns="3"
    data-index-number="12314"
    data-parent="cars">
    <!-- محتوای مقاله ماشین‌های برقی -->
  </article>

  <article
    id="solar-cars"
    data-columns="3"
    data-index-number="12315"
    data-parent="cars">
    <!-- محتوای مقاله ماشین‌های خورشیدی -->
  </article>

  <article
    id="flying-cars"
    data-columns="4"
    data-index-number="12316"
    data-parent="cars">
    <!-- محتوای مقاله ماشین‌های پرنده -->
  </article>
</main>
```

## دسترسی با JavaScript

خواندن مقادیر این attributes در [JavaScript](/en-US/docs/Web/JavaScript) نیز بسیار ساده است. می‌توانید از {{domxref("Element.getAttribute", "getAttribute()")}} با نام کامل HTML آن‌ها استفاده کنید، اما استاندارد راه ساده‌تری تعریف کرده: یک {{domxref("DOMStringMap")}} که از طریق پراپرتی {{domxref("HTMLElement/dataset", "dataset")}} قابل خواندن است.

برای دریافت یک `data` attribute از طریق شیء `dataset`، پراپرتی را بر اساس بخشی از نام attribute که بعد از `data-` می‌آید (توجه داشته باشید که خط تیره‌ها به {{Glossary("camel_case", "camel case")}} تبدیل می‌شوند) بخوانید:

```js
const article = document.querySelector("#electric-cars");
// همچنین کار می‌کند:
// const article = document.getElementById("electric-cars")

article.dataset.columns; // "3"
article.dataset.indexNumber; // "12314"
article.dataset.parent; // "cars"
```

هر پراپرتی یک رشته است و می‌توان آن را خواند و نوشت. در مثال بالا، تنظیم `article.dataset.columns = 5` آن attribute را به `"5"` تغییر می‌دهد.

همچنین می‌توانید از [`document.querySelector()`](/en-US/docs/Web/API/Document/querySelector) یا [`document.querySelectorAll()`](/en-US/docs/Web/API/Document/querySelectorAll) با انتخابگرهای data attribute برای پیدا کردن یک یا همه عناصر منطبق استفاده کنید:

```js
// پیدا کردن همه عناصر دارای attribute data-columns
const articles = document.querySelectorAll("[data-columns]");

// پیدا کردن همه عناصر با data-columns="3"
const threeColumnArticles = document.querySelectorAll('[data-columns="3"]');
// سپس می‌توانید روی نتایج پیمایش کنید
threeColumnArticles.forEach((article) => {
  console.log(article.dataset.indexNumber);
});
```

## دسترسی با CSS

توجه داشته باشید که چون data attributes همان attributeهای عادی HTML هستند، می‌توانید از [CSS](/en-US/docs/Web/CSS) نیز به آن‌ها دسترسی داشته باشید. مثلاً برای نمایش داده‌های والد روی مقاله، می‌توانید از [محتویات تولیدشده](/en-US/docs/Web/CSS/Reference/Properties/content) در CSS با تابع {{cssxref("attr()")}} استفاده کنید:

```css
article::before {
  content: attr(data-parent);
}
```

همچنین می‌توانید از [attribute selectors](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) در CSS برای تغییر استایل بر اساس داده استفاده کنید:

```css
article[data-columns="3"] {
  width: 400px;
}
article[data-columns="4"] {
  width: 600px;
}
```

مقادیر داده‌ها رشته‌ای هستند. مقادیر عددی باید در انتخابگر داخل گیومه قرار گیرند تا استایل اعمال شود.

## مثال‌ها

### تغییرات استایل

تصور کنید یک کلاس `callout` دارید. حالا می‌خواهید انواع مختلفی مانند "note" و "warning" پیاده‌سازی کنید. معمولاً توسعه‌دهندگان از نام‌های کلاس متفاوت استفاده می‌کنند.

```html
<div class="callout callout--note">...</div>
<div class="callout callout--warning">...</div>
```

```css
.callout {
  margin: 0.5em 0;
  padding: 0.5em;
  border-radius: 4px;
  border-width: 2px;
  border-style: solid;
}

.callout--note {
  border-color: rgb(15 15 235);
  background-color: rgb(15 15 235 / 0.2);
}
.callout--warning {
  border-color: rgb(235 15 15);
  background-color: rgb(235 15 15 / 0.2);
}
```

با استفاده از data attributes می‌توانید روش جایگزین زیر را در نظر بگیرید:

```html live-sample___callout-data-attr
<div class="callout">...</div>
<div class="callout" data-variant="note">...</div>
<div class="callout" data-variant="warning">...</div>
```

```css live-sample___callout-data-attr
.callout {
  margin: 0.5em 0;
  padding: 0.5em;
  border-radius: 4px;
  border-width: 2px;
  border-style: solid;
}

/* استایل پیش‌فرض */
.callout:not([data-variant]) {
  border-color: rgb(15 15 15);
  background-color: rgb(15 15 15 / 0.2);
}
.callout[data-variant="note"] {
  border-color: rgb(15 15 235);
  background-color: rgb(15 15 235 / 0.2);
}
.callout[data-variant="warning"] {
  border-color: rgb(235 15 15);
  background-color: rgb(235 15 15 / 0.2);
}
```

این روش چند مزیت دارد:

- تعداد حالت‌های نامعتبر را کاهش می‌دهد؛ مثلاً اعمال `callout--note` بدون کلاس `callout` یا استفاده همزمان از چند variant.
- وجود یک attribute مجزا به نام `data-variant` امکان تحلیل ایستای مقادیر معتبر را از طریق linting یا type checking فراهم می‌کند.
- تغییر variant ساده‌تر می‌شود: می‌توانید از `div.dataset.variant = "warning";` استفاده کنید، بدون نیاز به دستکاری `classList` که چند مرحله دارد.

### ارتباط دادن داده‌های دلخواه با عناصر DOM

در بسیاری از برنامه‌های وب، داده‌های JavaScript منبع حقیقت (source of truth) برای وضعیت UI هستند. در این موارد، فقط attribute‌هایی که برای رندر شدن لازم‌اند به HTML اضافه می‌شوند. Data attributes وقتی مفیدند که همه چیز از قبل در markup وجود دارد و JavaScript فقط برای مدیریت رویدادها، همگام‌سازی وضعیت و موارد مشابه استفاده می‌شود.

مثلاً در مثال [carousel with scroll margin](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver/scrollMargin#carousel_with_scroll_margin) یک صفحه HTML داریم که با تعداد زیادی `<img>` پر شده است. منبع تصویر ابتدا در `data-src` ذخیره می‌شود تا هیچ درخواستی ارسال نشود و `src` واقعی تنها زمانی اضافه می‌شود که `<img>` وارد viewport شود. داده (منبع تصویر) در کنار عنصر قرار دارد و JavaScript فقط وظیفه تعریف رفتار را بر عهده دارد.

## مشکلات

محتواهایی که باید قابل مشاهده و دسترس‌پذیر باشند را در data attributes ذخیره نکنید، زیرا فناوری‌های کمکی ممکن است به آن‌ها دسترسی نداشته باشند. همچنین خزنده‌های جستجو ممکن است مقادیر data attributes را ایندکس نکنند. اگر فقط قصد نمایش داده‌ی attribute را دارید، معمولاً می‌توانید مستقیماً `textContent` را تغییر دهید.

## همچنین ببینید

- این مقاله برگرفته از [Using data attributes in JavaScript and CSS on hacks.mozilla.org](https://hacks.mozilla.org/2012/10/using-data-attributes-in-javascript-and-css/) است.
- Custom attributes در SVG 2 نیز پشتیبانی می‌شوند؛ برای اطلاعات بیشتر به `HTMLElement.dataset` و `SVGAttr.data-*` مراجعه کنید.
- [How to use HTML data attributes](https://www.sitepoint.com/how-why-use-html5-custom-data-attributes/) (Sitepoint)