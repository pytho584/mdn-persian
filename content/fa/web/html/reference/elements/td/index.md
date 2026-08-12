---
title: <td> HTML table data cell element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/td
translated_by: n8n + AI
---

# \<td> HTML table data cell element

المان **`<td>`** در HTML، سلولی از جدول را تعریف می‌کند که داده را نگه می‌دارد و می‌تواند به عنوان فرزند المان `<tr>` استفاده شود.

```html
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

```css
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

### ویژگی‌ها

این المان شامل ویژگی‌های سراسری (global attributes) است.

* `colspan`
  * : شامل یک مقدار عددی غیرمنفی است که مشخص می‌کند سلول داده روی چند ستون گسترش می‌یابد. مقدار پیش‌فرض `1` است. مقادیر بیشتر از `1000` به `1000` بریده می‌شوند.
* `headers`
  * : شامل فهرستی از رشته‌ها با جداکنندهٔ فاصله است؛ هر رشته با ویژگی `id` المان‌های `<th>` متناظر است که عنوان این سلول جدول را فراهم می‌کنند.
* `rowspan`
  * : شامل یک مقدار عددی غیرمنفی است که مشخص می‌کند سلول داده روی چند ردیف گسترش می‌یابد. مقدار پیش‌فرض `1` است؛ اگر مقدار `0` تنظیم شود، سلول تا انتهای بخش گروه‌بندی جدول (`<thead>`، `<tbody>`، `<tfoot>`، حتی اگر به‌صورت ضمنی تعریف شده باشد) که به آن تعلق دارد گسترش می‌یابد. مقادیر بیشتر از `65534` به `65534` بریده می‌شوند.

#### ویژگی‌های منسوخ‌شده

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. این‌ها فقط برای مرجع هنگام به‌روزرسانی کدهای موجود و نیز به دلیل اهمیت تاریخی مستند شده‌اند.

* `abbr`
  * : شامل توضیح کوتاه و خلاصه‌ای از محتوای سلول داده است. برخی user-agentها، مانند screen readerها، ممکن است این توضیح را قبل از خود محتوا ارائه کنند. محتوای خلاصه‌شده را داخل سلول قرار دهید و توضیح طولانی‌تر را در ویژگی `title` بگذارید، زیرا این ویژگی منسوخ شده است. یا ترجیحاً، محتوا را داخل سلول داده قرار دهید و با CSS از [visually clip overflowing text](../../../../../../../en-US/docs/Web/CSS/Reference/Properties/text-overflow/) استفاده کنید.
* `align`
  * : تراز افقی سلول داده را مشخص می‌کند. مقادیر ممکن (enumerated) عبارت‌اند از: `left`, `center`, `right`, `justify` و `char`. در صورت پشتیبانی، مقدار `char` محتوای متنی را بر اساس کاراکتری که در ویژگی `char` تعریف شده و با افستی که در ویژگی `charoff` تعیین شده تراز می‌کند. به جای این ویژگی منسوخ‌شده، از ویژگی CSS `text-align` استفاده کنید.
* `axis`
  * : شامل فهرستی از رشته‌ها با جداکنندهٔ فاصله است؛ هر رشته با ویژگی `id` گروهی از سلول‌ها متناظر است که سلول داده به آن‌ها اعمال می‌شود.
* `bgcolor` (منسوخ)
  * : رنگ پس‌زمینهٔ سلول داده را مشخص می‌کند. مقدار آن یک رنگ HTML است: یا یک [کد RGB هگزادسیمال شش‌رقمی](../../../../../../../en-US/docs/Web/CSS/Reference/Values/hex-color/) که با `#` شروع می‌شود، یا یک [کلیدواژهٔ رنگ](../../../../../../../en-US/docs/Web/CSS/Reference/Values/named-color/). سایر مقادیر CSS از نوع `<color>` پشتیبانی نمی‌شوند. به‌جای این attribute از ویژگی CSS `background-color` استفاده کنید، چون این attribute منسوخ شده است.
* `char` (منسوخ)
  * : کار خاصی انجام نمی‌دهد. در اصل برای تعیین ترازبندی محتوای سلول نسبت به یک نویسهٔ خاص در نظر گرفته شده بود. مقادیر معمول شامل نقطه (`.`) برای تراز کردن اعداد یا مقادیر پولی است. اگر [`align`](index.md#align) روی `char` تنظیم نشده باشد، این attribute نادیده گرفته می‌شود.
* `charoff` (منسوخ)
  * : کار خاصی انجام نمی‌دهد. در اصل برای تعیین تعداد کاراکترهایی بود که محتوای سلول از نویسهٔ تراز (مشخص‌شده توسط attribute [`char`](index.md#char)) جابه‌جا شود.
* `height` (منسوخ)
  * : یک ارتفاع پیشنهادی برای سلول داده تعیین می‌کند. به‌جای این attribute از ویژگی CSS `height` استفاده کنید، چون این attribute منسوخ شده است.
* `scope` (منسوخ)
  * : مشخص می‌کند عنوان (که در عنصر `<th>` تعریف می‌شود) با کدام سلول‌ها مرتبط است. مقادیر شمارشی (enumerated) ممکن عبارت‌اند از `row`، `col`، `rowgroup` و `colgroup`. این attribute را فقط با عنصر `<th>` استفاده کنید تا مشخص شود سطر یا ستونی که عنوان آن است، زیرا این attribute برای عنصر `<td>` منسوخ شده است.
* `valign` (منسوخ)
  * : تراز عمودی سلول داده را مشخص می‌کند. مقادیر شمارشی (enumerated) ممکن عبارت‌اند از `baseline`، `bottom`، `middle` و `top`. به‌جای آن از ویژگی CSS `vertical-align` استفاده کنید، چون این attribute منسوخ شده است.
* `width` (منسوخ)
  * : یک عرض پیشنهادی برای سلول داده تعیین می‌کند. به‌جای این attribute از ویژگی CSS `width` استفاده کنید، چون این attribute منسوخ شده است.

### نکات استفاده

* `<td>` فقط باید درون عنصر `<tr>` استفاده شود.
*   هنگام استفاده از attributeهای [`colspan`](index.md#colspan) و [`rowspan`](index.md#rowspan) برای گسترش سلول‌های داده در چند ستون و سطر، سلول‌هایی که این attributeها را ندارند (با مقدار پیش‌فرض `1`) به‌طور خودکار در فضاهای خالی باقی‌مانده در ساختار جدول قرار می‌گیرند؛ این سلول‌ها یک سلول 1×1 را اشغال می‌کنند، همان‌طور که در شکل زیر نشان داده شده است:

    > \[!NOTE] این attributeها نباید برای همپوشانی سلول‌ها استفاده شوند.

### مثال‌ها

برای یک مثال کامل از جدول که استانداردهای رایج و بهترین روش‌ها را معرفی می‌کند، به `<table>` مراجعه کنید.

#### سلول‌های دادهٔ پایه

این مثال از عناصر `<td>` به‌همراه سایر عناصر مرتبط با جدول استفاده می‌کند تا یک جدول پایه با داده‌های مربوط به الفبای آوایی معرفی شود.

**HTML**

بعضی از سطرهای جدول (عناصر `<tr>`) هم سلول‌های سربرگ (عناصر `<th>`) و هم سلول‌های داده `<td>` دارند. عنصر `<th>` که فرزند اول هر سطر است، ستون اول جدول را می‌سازد و هر `<th>` به‌عنوان سربرگ سطر برای سلول‌های داده در آن سطر عمل می‌کند. هر عنصر `<td>` متناظر نیز داده‌هایی را نگه می‌دارد که با ستون و سطر سربرگ مربوطه هم‌تراز است.

> \[!NOTE] به‌طور معمول، یک گروه سربرگ جدول با سربرگ‌های ستون برای درک بهتر اطلاعات هر ستون پیاده‌سازی می‌شود. عناصر `<thead>` و `<tbody>` برای گروه‌بندی این سطرهای سربرگ‌ها و داده‌ها در بخش‌های سربرگ و بدنهٔ جدول استفاده می‌شوند. این کار در این مثال انجام نشده است تا تمرکز روی سلول‌های داده باشد و پیچیدگی مثال کمتر شود.

````markdown
```html
<table>
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
</table>
````

**CSS**

برای استایل‌دهی به جدول و سلول‌های آن از چند CSS ساده استفاده شده است. برای اینکه اطلاعات جدول راحت‌تر قابل درک و تشخیص باشند، با استفاده از [انتخاب‌گرهای ویژگی](../../../../../../../en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors/) و شبه‌کلاس `:nth-of-type` ظاهر سلول‌ها به‌صورت یک‌درمیان تغییر می‌کند.

```css
td,
th {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

tr:nth-of-type(odd) td {
  background-color: #eeeeee;
}

tr th[scope="row"] {
  background-color: #d6ecd4;
}
```

```css
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}
```

**نتیجه**

#### ستون‌ها و ردیف‌های ترکیبی

این مثال، جدول پایه را از [مثال قبلی](index.md#basic_data_cells) گسترش می‌دهد و یک سلول اضافی «ABC» به آن اضافه می‌کند.

**HTML**

یک سلول داده‌ای اضافی (عنصر `<td>`) درون اولین ردیف (عنصر `<tr>`) قرار داده شده است. این کار یک ستون چهارم در جدول ایجاد می‌کند.

با استفاده از ویژگی `rowspan`، سلول «ABC» روی سه ردیف اول جدول کشیده می‌شود. آخرین سلول‌های داده‌ای ردیف‌های بعدی هرکدام دو ستون را می‌پوشانند. این کار با ویژگی `colspan` انجام شده است تا آن‌ها به‌درستی در ساختار جدول تراز شوند. توجه کنید که یک ردیف اضافی (عنصر `<tr>`) برای نمایش این موضوع به جدول اضافه شده است.

```html
<table>
  <tr>
    <th scope="row">A</th>
    <td>Alfa</td>
    <td>AL fah</td>
    <td rowspan="3">ABC</td>
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
    <td colspan="2">DELL tah</td>
  </tr>
  <tr>
    <th scope="row">E</th>
    <td>Echo</td>
    <td colspan="2">ECK oh</td>
  </tr>
</table>
```

**CSS**

در CSS از شبه‌کلاس‌های `:first-of-type` و `:last-of-type` برای انتخاب و استایل‌دهی به سلول داده‌ای «ABC» اضافه‌شده استفاده شده است.

```css
tr:first-of-type td:last-of-type {
  width: 60px;
  background-color: #505050;
  color: white;
  font-weight: bold;
  text-align: center;
}

td,
th {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

tr:nth-of-type(odd) td {
  background-color: #eeeeee;
}

tr th[scope="row"] {
  background-color: #d6ecd4;
}
```

```css
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}
```

**نتیجه**

#### مرتبط‌سازی سلول‌های داده‌ای با سلول‌های سربرگ

برای روابط پیچیده‌تر بین سلول‌های داده‌ای (عناصر `<td>`) و سلول‌های سربرگ (عناصر `<th>`)، استفاده از عناصر `<th>` به‌تنهایی و با ویژگی [`scope`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/th/#scope) ممکن است برای فناوری‌های کمکی، به‌ویژه صفحه‌خوان‌ها، کافی نباشد.

**HTML**

````

برای بهبود دسترسی‌پذیری (accessibility) در [مثال قبلی](#column_and_row_spanning) و اینکه screen readerها بتوانند سرستون‌های مربوط به هر سلول داده را اعلام کنند، می‌توان از ویژگی [`headers`](#headers) به همراه [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) استفاده کرد. به هر سلول سرستون ردیف (عنصر `<th>`) که با سلول داده "ABC" مرتبط است – یعنی حروف "A" و "B" و "C" – یک شناسه یکتا با [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) داده می‌شود. سپس سلول داده "ABC" (عنصر `<td>`) این مقادیر `id` را در یک لیست جداشده با فاصله برای ویژگی [`headers`](#headers) به کار می‌برد.

> [!NOTE]
> توصیه می‌شود برای ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) از مقادیر توصیفی‌تر و مفیدتری استفاده کنید. هر `id` در یک سند باید منحصربه‌فرد باشد. در این مثال، مقدار `id`ها حروف تکی هستند تا تمرکز روی مفهوم ویژگی [`headers`](#headers) باقی بماند.

```html
<table>
  <tr>
    <th id="a" scope="row">A</th>
    <td>Alfa</td>
    <td>AL fah</td>
    <td headers="a b c" rowspan="3">ABC</td>
  </tr>
  <tr>
    <th id="b" scope="row">B</th>
    <td>Bravo</td>
    <td>BRAH voh</td>
  </tr>
  <tr>
    <th id="c" scope="row">C</th>
    <td>Charlie</td>
    <td>CHAR lee</td>
  </tr>
  <tr>
    <th scope="row">D</th>
    <td>Delta</td>
    <td colspan="2">DELL tah</td>
  </tr>
  <tr>
    <th scope="row">E</th>
    <td>Echo</td>
    <td colspan="2">ECK oh</td>
  </tr>
</table>
````

**نتیجه**

اگرچه [نمایش بصری](index.md#result_2) نسبت به [جدول مثال قبلی](index.md#column_and_row_spanning) تغییری نکرده، اما اکنون هر سلول داده (`<td>`) به‌طور صریح با سلول سرستون ردیف خود (`<th>`) مرتبط شده است.

### خلاصه فنی

| ویژگی                                                                                  | مقدار                                                                                                                                           |
| -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| [دسته‌بندی محتوا](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | Sectioning root (ریشهٔ بخش‌بندی)                                                                                                                |
| محتوای مجاز                                                                            | [محتوای جریانی (Flow content)](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content)                                |
| حذف تگ                                                                                 | تگ شروع الزامی است. تگ پایان را می‌توان حذف کرد اگر بلافاصله بعد از آن یک عنصر `<th>` یا `<td>` بیاید یا داده‌ای در عنصر والد باقی نمانده باشد. |
| والدین مجاز                                                                            | یک عنصر `<tr>`                                                                                                                                  |
| نقش ARIA ضمنی                                                                          | اگر فرزند یک عنصر `<table>` باشد، نقش `cell`؛ اگر فرزند عنصری با نقش `grid` باشد، نقش `gridcell`                                                |
| نقش‌های ARIA مجاز                                                                      | هر کدام                                                                                                                                         |
| رابط DOM                                                                               | `HTMLTableCellElement`                                                                                                                          |

* [مبانی جدول‌های HTML](../../../../../../../en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics/)
* `<caption>`، `<col>`، `<colgroup>`، `<table>`، `<tbody>`، `<tfoot>`، `<th>`، `<thead>`، `<tr>`: سایر عناصر مرتبط با جدول
* `background-color`: ویژگی CSS برای تنظیم رنگ پس‌زمینهٔ هر سلول داده
* `border`: ویژگی CSS برای کنترل حاشیه‌های سلول‌های داده
* `height`: ویژگی CSS برای کنترل ارتفاع پیشنهادی سلول داده
* `text-align`: ویژگی CSS برای تراز افقی محتوای هر سلول داده
* `vertical-align`: ویژگی CSS برای تراز عمودی محتوای هر سلول داده
* `width`: ویژگی CSS برای کنترل عرض پیشنهادی سلول داده
* `:nth-of-type`، `:first-of-type`، `:last-of-type`: شبه‌کلاس‌های CSS برای انتخاب سلول‌های دادهٔ دلخواه
