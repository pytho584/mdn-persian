---
title: "<tr> HTML table row element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/tr"
translated_by: "n8n + AI"
---

عنصر HTML **`<tr>`** یک ردیف (row) از سلول‌ها را در جدول تعریف می‌کند. سلول‌های این ردیف با استفاده از عناصر {{HTMLElement("td")}} (سلول داده) و {{HTMLElement("th")}} (سلول سرستون) مشخص می‌شوند.

```html interactive-example
<table>
  <caption>
    Alien football stars
  </caption>
  <thead>
    <tr>
      <th scope="col">Player</th>
      <th scope="col">Gloobles</th>
      <th scope="col">Za'taak</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">TR-7</th>
      <td>7</td>
      <td>4,569</td>
    </tr>
    <tr>
      <th scope="row">Khiresh Odo</th>
      <td>7</td>
      <td>7,223</td>
    </tr>
    <tr>
      <th scope="row">Mia Oolong</th>
      <td>9</td>
      <td>6,219</td>
    </tr>
  </tbody>
</table>
```

```css interactive-example
th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

th[scope="col"] {
  background-color: #505050;
  color: white;
}

th[scope="row"] {
  background-color: #d6ecd4;
}

td {
  text-align: center;
}

tr:nth-of-type(even) {
  background-color: #eeeeee;
}

table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

caption {
  caption-side: bottom;
  padding: 10px;
}
```

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

### ویژگی‌های منسوخ (Deprecated attributes)

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع به‌روزرسانی کدهای قدیمی و آشنایی تاریخی مستند شده‌اند.

- `align` {{deprecated_inline}}
  - : تراز افقی هر سلول در ردیف را مشخص می‌کند. مقادیر ممکن (شمارشی) عبارتند از `left`, `center`, `right`, `justify`, و `char`. در صورت پشتیبانی، مقدار `char` محتوای متنی را بر اساس کاراکتری که در ویژگی [`char`](#char) تعریف شده و با افستی که [`charoff`](#charoff) مشخص می‌کند، تراز می‌کند. به جای این ویژگی منسوخ از خاصیت CSS {{cssxref("text-align")}} استفاده کنید.

- `bgcolor` {{deprecated_inline}}
  - : رنگ پس‌زمینه هر سلول در ردیف را تعیین می‌کند. مقدار آن یک رنگ HTML است: یا یک [کد RGB هگزادسیمال ۶ رقمی](/en-US/docs/Web/CSS/Reference/Values/hex-color) با پیشوند `#`، یا یک [کلمه کلیدی رنگ](/en-US/docs/Web/CSS/Reference/Values/named-color). سایر مقادیر {{cssxref("&lt;color&gt;")}} در CSS پشتیبانی نمی‌شوند. به جای این ویژگی منسوخ از خاصیت CSS {{cssxref("background-color")}} استفاده کنید.

- `char` {{deprecated_inline}}
  - : تراز محتوای هر سلول در ردیف را نسبت به یک کاراکتر مشخص تعیین می‌کند. معمولاً برای تراز کردن اعداد یا مقادیر پولی از نقطه (`.`) استفاده می‌شود. اگر [`align`](#align) روی `char` تنظیم نشده باشد، این ویژگی نادیده گرفته می‌شود.

- `charoff` {{deprecated_inline}}
  - : تعداد کاراکترهای افست محتوای سلول ردیف را از کاراکتر تراز مشخص‌شده در ویژگی [`char`](#char) تعیین می‌کند.

- `valign` {{deprecated_inline}}
  - : تراز عمودی هر سلول در ردیف را مشخص می‌کند. مقادیر ممکن (شمارشی) عبارتند از `baseline`, `bottom`, `middle`, و `top`. به جای این ویژگی منسوخ از خاصیت CSS {{cssxref("vertical-align")}} استفاده کنید.

## نکات فنی

- عنصر `<tr>` تنها زمانی معتبر است که فرزند مستقیم یکی از عناصر `<thead>`، `<tbody>` یا `<tfoot>` باشد.
- اگر `<tr>` به‌عنوان فرزند مستقیم عنصر `<table>` قرار گیرد، مرورگر به‌طور ضمنی یک `<tbody>` در نظر می‌گیرد و آن را به نشانه‌گذاری (markup) اضافه می‌کند.
- این `<tbody>` ضمنی فقط در صورتی پشتیبانی می‌شود که `<table>` هیچ `<tbody>` فرزند دیگری نداشته باشد و فقط اگر `<tr>` بعد از عناصر `<caption>`، `<colgroup>` و `<thead>` قرار گرفته باشد.
- pseudo-classهای CSS مانند `:nth-of-type`، `:first-of-type` و `:last-of-type` اغلب برای انتخاب ردیف‌ها و سلول‌های داده یا هدر (عناصر `<td>` و `<th>`) مفید هستند.
- وقتی `<tr>` به‌عنوان فرزند مستقیم `<table>` قرار می‌گیرد و مرورگر یک `<tbody>` به نشانه‌گذاری اضافه می‌کند، انتخابگرهای CSS مانند `table > tr` ممکن است همان‌طور که انتظار می‌رود کار نکنند یا اصلاً کار نکنند.

## مثال‌ها

برای مشاهده‌ی یک مثال کامل از جدول با استانداردهای رایج و بهترین روش‌ها، به صفحه‌ی {{HTMLElement("table")}} مراجعه کنید.

### ساختار پایه‌ای ردیف

این مثال یک جدول با چهار ردیف و سه ستون نشان می‌دهد که در آن ستون اول شامل هدرهای ردیف برای سلول‌های داده است.

#### HTML

از چهار عنصر `<tr>` برای ایجاد چهار ردیف جدول استفاده شده است. هر ردیف شامل سه سلول است — یک سلول هدر (`<th>`) و دو سلول داده (`<td>`) — که سه ستون را تشکیل می‌دهند. ویژگی [`scope`](/en-US/docs/Web/HTML/Reference/Elements/th#scope) که روی هر سلول هدر تنظیم شده، مشخص می‌کند این سلول‌ها به کدام سلول‌ها مربوط می‌شوند که در این مثال، همه‌ی سلول‌های داده درون `row` هستند.

```html
<table>
  <tbody>
    <tr>
      <th scope="row">A</th>
      <td>Alfa</td>
      <td>AL fah</td>
    </tr>
    <tr>
      <th scope="row">B</th>
      <td>Bravo</td>
      <td>BRAH voh</td>
    </tr>
    <tr>
      <th scope="row">C</th>
      <td>Charlie</td>
      <td>CHAR lee</td>
    </tr>
    <tr>
      <th scope="row">D</th>
      <td>Delta</td>
      <td>DELL tah</td>
    </tr>
  </tbody>
</table>
```

#### CSS

از pseudo-class `:nth-of-type` در CSS برای انتخاب هر ردیف `odd` (فرد) و تنظیم `background-color` آن‌ها به یک رنگ تیره‌تر استفاده شده است تا اثری به نام «راه راه گورخری» (zebra stripe) ایجاد شود. این رنگ‌آمیزی متناوب، خواندن ردیف‌های داده در جدول را آسان‌تر می‌کند — مخصوصاً وقتی ردیف‌ها و ستون‌های زیادی دارید و می‌خواهید داده‌ای را در یک ردیف خاص پیدا کنید. علاوه بر این، سلول‌های هدر ردیف (عناصر `<th>`) با یک `background-color` متفاوت مشخص شده‌اند تا از سلول‌های داده (عناصر `<td>`) متمایز شوند.

```css
tr:nth-of-type(odd) {
  background-color: #eeeeee;
}

tr th[scope="row"] {
  background-color: #d6ecd4;
}
```

```css hidden
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}
```

#### نتیجه

{{EmbedLiveSample("Basic_row_setup", 650, 140)}}

### ردیف هدر

این مثال جدول پایه‌ای را از [مثال قبلی](#basic_row_setup) با اضافه کردن یک ردیف هدر به‌عنوان اولین ردیف جدول گسترش می‌دهد.

#### HTML

یک ردیف جدول (`<tr>`) اضافی به‌عنوان اولین ردیف جدول اضافه شده است که سلول‌های هدر ستون (`<th>`) را شامل می‌شود و برای هر ستون یک هدر فراهم می‌کند. این ردیف را در یک عنصر گروه‌بندی `<thead>` قرار می‌دهیم تا نشان دهیم این هدر جدول است. ویژگی [`scope`](/en-US/docs/Web/HTML/Reference/Elements/th#scope) به هر سلول هدر (`<th>`) در این ردیف هدر اضافه شده است تا به‌طور صریح مشخص کند که هر سلول هدر به تمام سلول‌های درون ستون خود مربوط است، حتی اگر آن سلول‌ها در `<tbody>` باشند.

```html
<table>
  <thead>
    <tr>
      <th scope="col">Symbol</th>
      <th scope="col">Code word</th>
      <th scope="col">Pronunciation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">A</th>
      <td>Alfa</td>
      <td>AL fah</td>
    </tr>
    <tr>
      <th scope="row">B</th>
      <td>Bravo</td>
      <td>BRAH voh</td>
    </tr>
    <tr>
      <th scope="row">C</th>
      <td>Charlie</td>
      <td>CHAR lee</td>
    </tr>
    <tr>
      <th scope="row">D</th>
      <td>Delta</td>
      <td>DELL tah</td>
    </tr>
  </tbody>
</table>
```

#### CSS

CSS این بخش تقریباً مشابه [مثال قبلی](#basic_row_setup) است، با این تفاوت که استایل‌های اضافه‌ای برای برجسته‌سازی "ردیف هدر" (header row) اضافه شده تا هدر ستون‌ها از سایر سلول‌ها متمایز شود.

```css
tr:nth-of-type(odd) {
  background-color: #eeeeee;
}

tr th[scope="col"] {
  background-color: #505050;
  color: white;
}

tr th[scope="row"] {
  background-color: #d6ecd4;
}
```

```css hidden
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}
```

#### Result

{{EmbedLiveSample("Header_row", 650, 170)}}

### مرتب‌سازی ردیف‌ها (Sorting rows)

برای مرتب‌سازی ردیف‌های (`<tr>` elements) یک {{HTMLElement("table")}} متد بومی وجود ندارد. اما با استفاده از {{jsxref("Array.prototype.sort()")}}، {{domxref("Node.removeChild")}} و {{domxref("Node.appendChild")}} می‌توان یک تابع سفارشی `sort()` در JavaScript پیاده‌سازی کرد تا یک {{domxref("HTMLCollection")}} از `<tr>` elements را مرتب کند.

#### HTML

در این جدول ساده از یک {{HTMLElement("tbody")}} element برای مشخص کردن بخش بدنه جدول استفاده شده و سه ردیف (`<tr>` elements) با داده ({{HTMLElement("td")}} elements) قرار داده شده که یک ستون با اعداد به ترتیب نزولی ایجاد می‌کند.

```html
<table>
  <tbody>
    <tr>
      <td>3</td>
    </tr>
    <tr>
      <td>2</td>
    </tr>
    <tr>
      <td>1</td>
    </tr>
  </tbody>
</table>
```

#### JavaScript

در کد JavaScript زیر، تابع `sort()` ایجاد شده به {{HTMLElement("tbody")}} element متصل می‌شود تا سلول‌های جدول را به ترتیب مقادیر افزایشی مرتب کرده و نمایش را به‌روز کند.

```js
HTMLTableSectionElement.prototype.sort = function (cb) {
  Array.from(this.rows)
    .sort(cb)
    .forEach((e) => this.appendChild(this.removeChild(e)));
};

document
  .querySelector("table")
  .tBodies[0].sort((a, b) => a.textContent.localeCompare(b.textContent));
```

```css hidden
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

td {
  border: 1px solid rgb(160 160 160);
  padding: 4px 8px;
}
```

#### Result

{{EmbedLiveSample('Sorting_rows', '650', '80')}}

### مرتب‌سازی ردیف‌ها با کلیک روی هدر سلول‌ها

این مثال جدول پایه از [مثال قبلی](#sorting_rows) را گسترش می‌دهد و مرتب‌سازی را تعاملی و مستقل برای چندین ستون می‌کند.

#### HTML

یک سلول داده اضافی ({{HTMLElement("td")}} element) به هر ردیف (`<tr>` element) در بدنه جدول ({{HTMLElement("tbody")}} element) اضافه شده تا یک ستون دوم با حروف به ترتیب صعودی ایجاد شود. با استفاده از {{HTMLElement("thead")}} element، یک بخش سربرگ قبل از بدنه اضافه می‌شود تا یک ردیف سربرگ با سلول‌های هدر جدول ({{HTMLElement("th")}} element) معرفی کند. این سلول‌های هدر در کد JavaScript زیر برای کلیک‌پذیر شدن و سپس انجام مرتب‌سازی مربوطه هنگام کلیک استفاده می‌شوند.

```html
<table>
  <thead>
    <tr>
      <th>Numbers</th>
      <th>Letters</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3</td>
      <td>A</td>
    </tr>
    <tr>
      <td>2</td>
      <td>B</td>
    </tr>
    <tr>
      <td>1</td>
      <td>C</td>
    </tr>
  </tbody>
</table>
```

#### JavaScript

یک event handler کلیک به هر سرستون جدول (عنصر `<th>`) از هر `<table>` درون `document` اضافه می‌شود؛ این handler تمام ردیف‌ها (`<tr>`ها) را در `<tbody>` بر اساس محتوای سلول‌های داده (عنصرهای `<td>`) که درون ردیف‌ها هستند مرتب می‌کند.

> [!NOTE]
> این راه‌حل فرض می‌کند که عنصرهای `<td>` فقط با متن خالص پر شده‌اند و هیچ عنصر فرزندی ندارند.

```js
const allTables = document.querySelectorAll("table");

for (const table of allTables) {
  const tBody = table.tBodies[0];
  const rows = Array.from(tBody.rows);
  const headerCells = table.tHead.rows[0].cells;

  for (const th of headerCells) {
    const cellIndex = th.cellIndex;

    th.addEventListener("click", () => {
      rows.sort((tr1, tr2) => {
        const tr1Text = tr1.cells[cellIndex].textContent;
        const tr2Text = tr2.cells[cellIndex].textContent;
        return tr1Text.localeCompare(tr2Text);
      });

      tBody.append(...rows);
    });
  }
}
```

```css hidden
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 4px 8px;
}

th {
  background-color: #505050;
  color: white;
  cursor: pointer;
}
```

> [!NOTE]
> برای استفاده‌پذیری و دسترس‌پذیری، سلول سرستون هر ستون قابل مرتب‌سازی باید به‌عنوان یک دکمه مرتب‌سازی قابل شناسایی باشد و هرکدام باید مشخص کنند که ستون در حال حاضر به‌صورت صعودی یا نزولی مرتب شده است، هم به صورت بصری و هم با ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort). برای اطلاعات بیشتر به [راهنمای شیوه‌های ARIA](https://www.w3.org/WAI/ARIA/apg/) و [نمونه جدول قابل مرتب‌سازی](https://www.w3.org/WAI/ARIA/apg/patterns/table/examples/sortable-table/) مراجعه کنید.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>هیچکدام</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        صفر یا چند عنصر `<td>` و/یا `<th>`؛ عناصر پشتیبان اسکریپت (script-supporting elements) (`<script>` و `<template>`) نیز مجاز هستند.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        تگ شروع اجباری است. اگر عنصر `<tr>` بلافاصله پس از یک `<tr>` دیگر بیاید، یا اگر ردیف آخرین عنصر در گروه جدول والد خود (عنصر `<thead>`، `<tbody>` یا `<tfoot>`) باشد، تگ پایان می‌تواند حذف شود.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        `<table>` (فقط در صورتی که جدول هیچ عنصر فرزند `<tbody>` نداشته باشد، و حتی در آن صورت فقط پس از عناصر `<caption>`، `<colgroup>` و `<thead>`); در غیر این صورت، والد باید یک عنصر `<thead>`، `<tbody>` یا `<tfoot>` باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role">row</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLTableRowElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- [یادگیری: مبانی جدول‌های HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- `<caption>`، `<col>`، `<colgroup>`، `<table>`، `<tbody>`، `<td>`، `<tfoot>`، `<th>`، `<thead>`: سایر عناصر مرتبط با جدول
- `background-color`: ویژگی CSS برای تنظیم رنگ پس‌زمینهٔ سلول‌های هر سطر
- `border`: ویژگی CSS برای کنترل حاشیه‌های سلول‌های سطر
- `text-align`: ویژگی CSS برای ترازبندی افقی محتوای هر سلول سطر
- `vertical-align`: ویژگی CSS برای ترازبندی عمودی محتوای هر سلول سطر
- `:nth-of-type`، `:first-of-type`، `:last-of-type`: شبه‌کلاس‌های CSS برای انتخاب سلول‌های سطر موردنظر