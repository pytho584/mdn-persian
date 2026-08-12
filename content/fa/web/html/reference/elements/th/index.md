---
title: <th> HTML table header element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/th
translated_by: n8n + AI
---

# \<th> HTML table header element

المان `<th>` (سربرگ جدول) در HTML یک سلول را به‌عنوان سربرگ گروهی از سلول‌های جدول تعریف می‌کند و می‌تواند به‌عنوان فرزند المان `<tr>` استفاده شود. ماهیت دقیق این گروه توسط ویژگی‌های `scope` و `headers` مشخص می‌شود.

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

### ویژگی‌ها (Attributes)

این المان شامل [ویژگی‌های سراسری](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) است.

* `abbr`
  * : توضیح کوتاه و خلاصه‌ای از محتوای سلول سربرگ که به‌عنوان یک برچسب جایگزین برای ارجاع به سلول سربرگ در سایر زمینه‌ها استفاده می‌شود. برخی user-agent ها، مانند screen reader ها، ممکن است این توضیح را قبل از خود محتوا نمایش دهند.
* `colspan`
  * : یک مقدار عدد صحیح غیرمنفی که نشان می‌دهد سلول سربرگ روی چند ستون کشیده می‌شود. مقدار پیش‌فرض `1` است. مقادیر بیشتر از `1000` به `1000` محدود می‌شوند.
* `headers`
  * : فهرستی از رشته‌ها با جداکننده فاصله که با ویژگی `id` المان‌های `<th>` که سربرگ‌های این سلول سربرگ را تأمین می‌کنند، متناظر است.
* `rowspan`
  * : یک مقدار عدد صحیح غیرمنفی که نشان می‌دهد سلول سربرگ روی چند ردیف کشیده می‌شود. مقدار پیش‌فرض `1` است؛ اگر مقدار آن `0` باشد، سلول سربرگ تا انتهای بخش گروه‌بندی جدول (شامل `thead`، `tbody`، `tfoot`، حتی اگر به‌صورت ضمنی تعریف شده باشد) که `<th>` به آن تعلق دارد کشیده خواهد شد. مقادیر بیشتر از `65534` در `65534` محدود می‌شوند.
* `scope`
  *   : سلول‌هایی را تعریف می‌کند که سربرگ تعریف‌شده در `<th>` با آن‌ها مرتبط است. مقادیر ممکن (enumerated) عبارتند از:

      * `row`: سربرگ با تمام سلول‌های ردیفی که در آن قرار دارد مرتبط است؛
      * `col`: سربرگ با تمام سلول‌های ستونی که در آن قرار دارد مرتبط است؛
      * `rowgroup`: سربرگ متعلق به یک گروه ردیفی (rowgroup) است و با تمام سلول‌های آن مرتبط است؛
      * `colgroup`: سربرگ متعلق به یک گروه ستونی (colgroup) است و با تمام سلول‌های آن مرتبط است.

      اگر ویژگی `scope` مشخص نشده باشد، یا مقدار آن یکی از `row`، `col`، `rowgroup` یا `colgroup` نباشد، مرورگرها به‌طور خودکار مجموعه سلول‌هایی را که سلول سربرگ برای آن‌ها اعمال می‌شود انتخاب می‌کنند.

#### ویژگی‌های منسوخ (Deprecated)

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا برای مرجع هنگام به‌روزرسانی کد موجود و صرفاً به دلیل اهمیت تاریخی مستند شده‌اند.

* `align` (منسوخ شده)
  * : تراز افقی سلول سربرگ را مشخص می‌کند. مقادیر شمارشی (enumerated) ممکن عبارت‌اند از `left`، `center`، `right`، `justify` و `char`. در صورت پشتیبانی، مقدار `char` محتوای متنی را بر اساس کاراکتری که در ویژگی [`char`](index.md#char) تعریف شده و انحراف (offset) مشخص‌شده توسط ویژگی [`charoff`](index.md#charoff) تراز می‌کند. به‌جای این ویژگی (که منسوخ شده) از ویژگی CSS `text-align` استفاده کنید.
* `axis` (منسوخ شده)
  * : شامل فهرستی از رشته‌ها با جداکننده فاصله است که هر کدام با ویژگی `id` گروهی از سلول‌ها مطابقت دارد که سلول سربرگ به آن‌ها اعمال می‌شود. به‌جای این ویژگی (که منسوخ شده) از ویژگی [`scope`](index.md#scope) استفاده کنید.
* `bgcolor` (منسوخ شده)
  * : رنگ پس‌زمینه سلول سربرگ را تعیین می‌کند. مقدار آن یک رنگ HTML است؛ یا [کد RGB هگزادسیمال ۶ رقمی](../../../../../../../en-US/docs/Web/CSS/Reference/Values/hex-color/) که با `#` شروع می‌شود، یا یک [کلیدواژه رنگ](../../../../../../../en-US/docs/Web/CSS/Reference/Values/named-color/). سایر مقادیر CSS از نوع `<color>` پشتیبانی نمی‌شوند. به‌جای این ویژگی (که منسوخ شده) از ویژگی CSS `background-color` استفاده کنید.
* `char` (منسوخ شده)
  * : هیچ کاری انجام نمی‌دهد. در ابتدا برای مشخص کردن تراز محتوا نسبت به یک کاراکتر از سلول سربرگ در نظر گرفته شده بود. مقادیر معمول برای آن شامل نقطه (`.`) است، زمانی که بخواهید اعداد یا مقادیر پولی را تراز کنید. اگر [`align`](index.md#align) روی `char` تنظیم نشده باشد، این ویژگی نادیده گرفته می‌شود.
* `charoff` (منسوخ شده)
  * : هیچ کاری انجام نمی‌دهد. در ابتدا برای مشخص کردن تعداد کاراکترهایی که محتوای سلول سربرگ از کاراکتر تراز (مشخص‌شده توسط ویژگی [`char`](index.md#char)) فاصله بگیرد، در نظر گرفته شده بود.
* `height` (منسوخ شده)
  * : ارتفاع پیشنهادی سلول سربرگ را تعریف می‌کند. به‌جای این ویژگی (که منسوخ شده) از ویژگی CSS `height` استفاده کنید.
* `valign` (منسوخ شده)
  * : تراز عمودی سلول سربرگ را مشخص می‌کند. مقادیر شمارشی (enumerated) ممکن عبارت‌اند از `baseline`، `bottom`، `middle` و `top`. به‌جای این ویژگی (که منسوخ شده) از ویژگی CSS `vertical-align` استفاده کنید.
* `width` (منسوخ شده)
  * : عرض پیشنهادی سلول سربرگ را تعریف می‌کند. به‌جای این ویژگی (که منسوخ شده) از ویژگی CSS `width` استفاده کنید.

### یادداشت‌های استفاده

* عنصر `<th>` فقط می‌تواند داخل یک عنصر `<tr>` استفاده شود.
* در زمینه‌های ساده، استفاده از ویژگی [`scope`](index.md#scope) روی سلول‌های سربرگ (`<th>`) اضافی است؛ زیرا [`scope`](index.md#scope) به‌صورت ضمنی تعیین می‌شود. با این حال، برخی فناوری‌های کمکی ممکن است نتوانند به‌درستی آن را تشخیص دهند، بنابراین مشخص‌کردن scope برای سربرگ می‌تواند تجربه کاربری را بهبود بخشد.
*   هنگام استفاده از ویژگی‌های [`colspan`](index.md#colspan) و [`rowspan`](index.md#rowspan) برای گسترش سلول‌های سربرگ در چند ستون و ردیف، سلول‌هایی که این ویژگی‌ها برای آن‌ها تعریف نشده است (با مقدار پیش‌فرض `1`)، به‌طور خودکار در فضاهای خالی موجود در ساختار جدول که سلول‌های 1×1 را پوشش می‌دهند جای می‌گیرند؛ همان‌طور که در تصویر زیر نشان داده شده است:

    > \[!NOTE] از این ویژگی‌ها نباید برای همپوشانی سلول‌ها استفاده شود.

### مثال‌ها

برای یک مثال کامل جدول که استانداردهای رایج و بهترین روش‌ها را معرفی می‌کند، به عنصر `<table>` مراجعه کنید.

#### سربرگ‌های پایه ستون و ردیف

این مثال از عناصر `<th>` برای معرفی سربرگ‌های ستون و ردیف در یک ساختار جدول پایه استفاده می‌کند.

**HTML**

ردیف اول (عنصر `<tr>`) شامل سرستون‌ها (عناصر `<th>`) است که به عنوان «عنوان» ستون‌ها عمل می‌کنند تا درک اطلاعات هر ستون و شناسایی داده‌ها آسان‌تر شود. برای مشخص کردن اینکه هر سرستون به تمام سلول‌های ستون مربوطه ارتباط دارد، ویژگی [`scope`](index.md#scope) روی `col` (ستون) تنظیم شده است.

ردیف‌های باقی‌مانده حاوی داده‌های اصلی جدول هستند. هر یک از این ردیف‌ها یک سرسطر (عنصر `<th>`) دارد که به عنوان اولین سلول قرار می‌گیرد. این کار یک ستون از سرسطرها را به عنوان اولین ستون جدول ایجاد می‌کند. مشابه سرستون‌ها، ویژگی [`scope`](index.md#scope) روی `row` تنظیم می‌شود تا مشخص کند هر سرسطر به کدام سلول‌ها مربوط است؛ که در مثال زیر، تمام سلول‌های داده (عناصر `<td>`) در هر ردیف هستند.

> **نکته:** معمولاً از عناصر گروه‌بندی `<thead>` و `<tbody>` برای دسته‌بندی ردیف‌های دارای header در بخش‌های head و body جدول استفاده می‌شود. این عناصر در این مثال برای کاهش پیچیدگی و تمرکز روی استفاده از سلول‌های header حذف شده‌اند.

```html
<table>
  <tr>
    <th scope="col">Symbol</th>
    <th scope="col">Code word</th>
    <th scope="col">Pronunciation</th>
  </tr>
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
```

**CSS**

برای استایل‌دهی جدول و سلول‌های آن از CSS پایه استفاده شده است. از [attribute selector](../../../../../../../en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors/)های CSS برای هدف قرار دادن سلول‌های header بر اساس مقدار ویژگی [`scope`](index.md#scope) استفاده می‌کنیم، تا سرستون‌ها و سرسطرها (عناصر `<th>`) برجسته شوند و از یکدیگر و از سلول‌های داده (عناصر `<td>`) متمایز گردند.

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

tr:nth-of-type(odd) td {
  background-color: #eeeeee;
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

#### ادغام ستون و ردیف

این مثال جدول پایه‌ای از [مثال قبلی](index.md#basic_column_and_row_headers) را با افزودن یک ردیف دوم برای سرستون‌های اضافی گسترش و بهبود می‌بخشد.

**HTML**

یک ردیف جدول اضافی (عنصر `<tr>`) به عنوان دومین ردیف header جدول به همراه دو سرستون اضافی (عناصر `<th>`) اضافه شده است. به این ترتیب، ستون «Pronunciation» به دو ستون تقسیم می‌شود: یکی برای نماد IPA (الفبای آوایی بین‌المللی) و دیگری برای بازنویسی تلفظ (ستون اصلی تلفظ). سلول‌های داده‌ای متناظر (عناصر `<td>`) به هر ردیف بعدی اضافه می‌شوند.

همان‌طور که در [یادداشت‌های استفاده](index.md#usage_notes) نشان داده شده، ویژگی‌های [`colspan`](index.md#colspan) و [`rowspan`](index.md#rowspan) را می‌توان برای عناصر `<th>` به کار برد تا سلول‌های header را به ستون‌ها و ردیف‌های درست اختصاص دهند. برای ایجاد یک header «دو ردیفی» در ساختار جدول، دو سلول header اول در اولین عنصر `<tr>` در دو ردیف ادغام می‌شوند. سومین سلول header در دو ستون گسترش می‌یابد (در همان ردیف اول باقی می‌ماند). این تنظیم دو ناحیه خالی در ستون‌های سوم و چهارم در ردیف دوم ایجاد می‌کند، جایی که دو header درون دومین عنصر `<tr>` به طور خودکار قرار می‌گیرند، با مقدار پیش‌فرض `1` برای ویژگی‌های [`colspan`](index.md#colspan) و [`rowspan`](index.md#rowspan).

> \[!NOTE] معمولاً از عناصر `<thead>` و `<tbody>` برای گروه‌بندی سطرهایی که شامل هدر هستند به بخش‌های سربرگ و بدنهٔ جدول استفاده می‌شود. در این مثال، برای تمرکز روی هدرها و ادغام سلول‌ها و کاهش پیچیدگی، از این عناصر استفاده نشده است.

```html
<table>
  <tr>
    <th scope="col" rowspan="2">Symbol</th>
    <th scope="col" rowspan="2">Code word</th>
    <th scope="col" colspan="2">Pronunciation</th>
  </tr>
  <tr>
    <th scope="col">IPA</th>
    <th scope="col">Respelling</th>
  </tr>
  <tr>
    <th scope="row">A</th>
    <td>Alfa</td>
    <td>ˈælfa</td>
    <td>AL fah</td>
  </tr>
  <tr>
    <th scope="row">B</th>
    <td>Bravo</td>
    <td>ˈbraːˈvo</td>
    <td>BRAH voh</td>
  </tr>
  <tr>
    <th scope="row">C</th>
    <td>Charlie</td>
    <td>ˈtʃɑːli</td>
    <td>CHAR lee</td>
  </tr>
  <tr>
    <th scope="row">D</th>
    <td>Delta</td>
    <td>ˈdeltɑ</td>
    <td>DELL tah</td>
  </tr>
</table>
```

**CSS**

CSS این مثال بدون تغییر از [مثال قبلی](index.md#basic_column_and_row_headers) باقی مانده است.

```css
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

th[scope="col"] {
  background-color: #505050;
  color: white;
}

th[scope="row"] {
  background-color: #d6ecd4;
}

tr:nth-of-type(odd) td {
  background-color: #eeeeee;
}
```

**نتیجه**

#### ارتباط سلول‌های هدر با سلول‌های هدر دیگر

برای روابط پیچیده‌تر بین سلول‌های هدر، استفاده از عناصر `th` تنها با ویژگی [`scope`](index.md#scope) ممکن است برای فناوری‌های کمکی، به‌ویژه صفحه‌خوان‌ها، کافی نباشد.

**HTML**

برای بهبود دسترس‌پذیری (accessibility) [مثال قبلی](index.md#column_and_row_spanning) و همچنین امکان بیان هدرهای مرتبط با هر سلول هدر توسط صفحه‌خوان‌ها، می‌توان از ویژگی [`headers`](index.md#headers) به همراه ویژگی‌های [`id`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/id/) استفاده کرد. در این مثال، چون ستون «Pronunciation» به دو ستون تقسیم شده و یک هدر دو ردیفه ایجاد شده، فناوری‌های کمکی مانند صفحه‌خوان‌ها ممکن است نتوانند تشخیص دهند که سلول هدر «Pronunciation» با کدام سلول‌های هدر دیگر در ارتباط است و برعکس. بنابراین، ویژگی [`headers`](index.md#headers) روی سلول‌های هدر «Pronunciation»، «IPA» و «Respelling» استفاده شده است تا این سلول‌ها بر اساس مقادیر شناسه‌های یکتای موجود در ویژگی‌های [`id`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/id/) — که به صورت فهرستی با جداکنندهٔ فاصله نوشته می‌شوند — به یکدیگر مرتبط شوند.

> \[!NOTE] توصیه می‌شود برای ویژگی [`id`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/id/) از مقادیر توصیفی‌تر و کاربردی‌تر استفاده کنید. هر `id` در یک سند باید برای همان سند یکتا باشد. در این مثال، مقادیر `id` به‌صورت کاراکترهای تکی هستند تا تمرکز روی مفهوم ویژگی [`headers`](index.md#headers) حفظ شود.

```html
<table>
  <tr>
    <th scope="col" rowspan="2">Symbol</th>
    <th scope="col" rowspan="2">Code word</th>
    <th scope="col" colspan="2" id="p" headers="i r">Pronunciation</th>
  </tr>
  <tr>
    <th scope="col" id="i" headers="p">IPA</th>
    <th scope="col" id="r" headers="p">Respelling</th>
  </tr>
  <tr>
    <th scope="row">A</th>
    <td>Alfa</td>
    <td>ˈælfa</td>
    <td>AL fah</td>
  </tr>
  <tr>
    <th scope="row">B</th>
    <td>Bravo</td>
    <td>ˈbraːˈvo</td>
    <td>BRAH voh</td>
  </tr>
  <tr>
    <th scope="row">C</th>
    <td>Charlie</td>
    <td>ˈtʃɑːli</td>
    <td>CHAR lee</td>
  </tr>
  <tr>
    <th scope="row">D</th>
    <td>Delta</td>
    <td>ˈdeltɑ</td>
    <td>DELL tah</td>
  </tr>
</table>
```

**نتیجه**

[نتیجهٔ بصری](index.md#result_2) نسبت به [جدول مثال قبلی](index.md#column_and_row_spanning) تغییری نکرده است.

### خلاصه فنی

| [دسته‌بندی محتوا](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | هیچ‌کدام                                                                                                                                                                                                             |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| محتوای مجاز                                                                            | [محتواهای جریانی](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content)، به شرطی که هیچ فرزند header، footer، محتوای بخش‌بندی یا محتوای عنوان‌دار نداشته باشد.                           |
| حذف تگ                                                                                 | <p>تگ شروع اجباری است.<br>تگ پایان را می‌توان حذف کرد، اگر بلافاصله بعد از آن یک عنصر <code>&#x3C;th></code> یا <code>&#x3C;td></code> بیاید، یا اگر داده‌ی دیگری در عنصر والد وجود نداشته باشد.</p>                 |
| والدین مجاز                                                                            | یک عنصر `<tr>`                                                                                                                                                                                                       |
| نقش ARIA ضمنی                                                                          | [`columnheader`](../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role/) یا [`rowheader`](../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role/) |
| نقش‌های ARIA مجاز                                                                      | هر نقشی                                                                                                                                                                                                              |
| رابط DOM                                                                               | `HTMLTableCellElement`                                                                                                                                                                                               |

### مشخصات

### سازگاری با مرورگرها

### همچنین ببینید

* [یادگیری: مبانی جدول‌های HTML](../../../../../../../en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics/)
* عناصر دیگر مرتبط با جدول: \{{HTMLElement("caption")\}}، \{{HTMLElement("col")\}}، \{{HTMLElement("colgroup")\}}، \{{HTMLElement("table")\}}، \{{HTMLElement("tbody")\}}، \{{HTMLElement("td")\}}، \{{HTMLElement("tfoot")\}}، \{{HTMLElement("thead")\}}، \{{HTMLElement("tr")\}}
* \{{cssxref("background-color")\}}: ویژگی CSS برای تنظیم رنگ پس‌زمینه‌ی هر سلول header
* \{{cssxref("border")\}}: ویژگی CSS برای کنترل حاشیه‌های سلول‌های header
* \{{cssxref("height")\}}: ویژگی CSS برای کنترل ارتفاع پیشنهادی سلول header
* \{{cssxref("text-align")\}}: ویژگی CSS برای تراز افقی محتوای هر سلول header
* \{{cssxref("vertical-align")\}}: ویژگی CSS برای تراز عمودی محتوای هر سلول header
* \{{cssxref("width")\}}: ویژگی CSS برای کنترل عرض پیشنهادی سلول header
* \{{cssxref(":nth-of-type")\}}، \{{cssxref(":first-of-type")\}}، \{{cssxref(":last-of-type")\}}: شبه-کلاس‌های CSS برای انتخاب سلول‌های header مورد نظر
