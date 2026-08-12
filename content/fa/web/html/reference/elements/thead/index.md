---
title: <thead> HTML table head element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/thead
translated_by: n8n + AI
---

# \<thead> HTML table head element

عنصر `<thead>` در HTML مجموعه‌ای از ردیف‌های جدول (عناصر `<tr>`) را در بر می‌گیرد و نشان می‌دهد که این ردیف‌ها سرِ جدول را تشکیل می‌دهند و معمولاً اطلاعاتی درباره ستون‌های جدول (مانند عنوان‌ستون‌ها با `<th>`) دارند.

```html
<table>
  <caption>
    Council budget (in £) 2018
  </caption>
  <thead>
    <tr>
      <th scope="col">Items</th>
      <th scope="col">Expenditure</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Donuts</th>
      <td>3,000</td>
    </tr>
    <tr>
      <th scope="row">Stationery</th>
      <td>18,000</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row">Totals</th>
      <td>21,000</td>
    </tr>
  </tfoot>
</table>
```

```css
thead,
tfoot {
  background-color: #2c5e77;
  color: white;
}

tbody {
  background-color: #e4f0f5;
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

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

td {
  text-align: center;
}
```

### Attributes

این عنصر از [ویژگی‌های سراسری (global attributes)](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) پشتیبانی می‌کند.

#### ویژگی‌های منسوخ شده

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع (وقتی کد قدیمی را به‌روز می‌کنید) و برای آشنایی تاریخی ذکر شده‌اند.

* `align` \{{deprecated\_inline\}}
  * : تراز افقی هر سلول سر را مشخص می‌کند. مقادیر enumerated ممکن عبارتند از: `left`, `center`, `right`, `justify`, `char`. اگر مرورگر از `char` پشتیبانی کند، محتوای متنی را بر اساس نویسه‌ای که در ویژگی [`char`](index.md#char) تعریف شده و فاصله‌ای که [`charoff`](index.md#charoff) تعیین می‌کند، تراز می‌کند. این ویژگی منسوخ شده است؛ به جای آن از ویژگی CSS \{{cssxref("text-align")\}} استفاده کنید.
* `bgcolor` \{{deprecated\_inline\}} \{{non-standard\_inline\}}
  * : رنگ پس‌زمینه هر سلول سر را تعریف می‌کند. مقدار آن یک رنگ HTML است: یا یک کد RGB هگزادسیمال ۶ رقمی (با پیشوند `#`) یا یک نام رنگ (color keyword). سایر مقادیر CSS \{{cssxref("\<color>")\}} پشتیبانی نمی‌شوند. این ویژگی منسوخ شده است؛ به جای آن از ویژگی CSS \{{cssxref("background-color")\}} استفاده کنید.
* `char` \{{deprecated\_inline\}}
  * : هیچ کاری انجام نمی‌دهد. در اصل برای مشخص کردن نویسه‌ای که محتوای هر سلول سر باید بر اساس آن تراز شود، در نظر گرفته شده بود. اگر [`align`](index.md#align) روی `char` تنظیم نشده باشد، این ویژگی نادیده گرفته می‌شود.
* `charoff` \{{deprecated\_inline\}}
  * : هیچ کاری انجام نمی‌دهد. در اصل برای مشخص کردن تعداد نویسه‌های جابجایی محتوای سلول سر از نویسه تراز تعیین‌شده در [`char`](index.md#char)، در نظر گرفته شده بود.
* `valign` \{{deprecated\_inline\}}
  * : تراز عمودی هر سلول سر را مشخص می‌کند. مقادیر enumerated ممکن عبارتند از: `baseline`, `bottom`, `middle`, `top`. این ویژگی منسوخ شده است؛ به جای آن از ویژگی CSS \{{cssxref("vertical-align")\}} استفاده کنید.
* عنصر `<thead>` بعد از هر عنصر `<caption>` و `<colgroup>` قرار می‌گیرد، اما قبل از هر عنصر `<tbody>`، `<tfoot>` و `<tr>`.
* همراه با عناصر مرتبط `<tbody>` و `<tfoot>`، عنصر `<thead>` اطلاعات semantic مفیدی فراهم می‌کند و می‌تواند هنگام رندر برای صفحه نمایش یا چاپ استفاده شود. مشخص کردن چنین گروه‌های محتوایی جدول، اطلاعات متنی ارزشمندی نیز برای فناوری‌های کمکی، از جمله صفحه‌خوان‌ها و موتورهای جستجو فراهم می‌کند.
* هنگام چاپ یک سند، در مورد جدول چندصفحه‌ای، سربرگ معمولاً اطلاعاتی را مشخص می‌کند که در هر صفحه یکسان باقی می‌ماند.

### مثال‌ها

برای یک مثال کامل از جدول که استانداردها و بهترین روش‌های رایج را معرفی می‌کند، به عنصر `<table>` مراجعه کنید.

#### ساختار پایه سربرگ

این مثال جدولی را نشان می‌دهد که به یک بخش سربرگ با عنوان ستون‌ها و یک بخش بدنه با داده‌های اصلی جدول تقسیم شده است.

**HTML**

عناصر `<thead>` و `<tbody>` برای سازماندهی ردیف‌های جدول به بخش‌های معنایی (semantic) استفاده می‌شوند. عنصر `<thead>` بخش سربرگ جدول را نشان می‌دهد که شامل یک ردیف (`<tr>`) از سلول‌های عنوان ستون (`<th>`) است.

```html
<table>
  <thead>
    <tr>
      <th>Student ID</th>
      <th>Name</th>
      <th>Major</th>
      <th>Credits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3741255</td>
      <td>Jones, Martha</td>
      <td>Computer Science</td>
      <td>240</td>
    </tr>
    <tr>
      <td>3971244</td>
      <td>Nim, Victor</td>
      <td>Russian Literature</td>
      <td>220</td>
    </tr>
    <tr>
      <td>4100332</td>
      <td>Petrov, Alexandra</td>
      <td>Astrophysics</td>
      <td>260</td>
    </tr>
  </tbody>
</table>
```

**CSS**

برخی CSS پایه برای استایل‌دهی و برجسته‌کردن سربرگ جدول استفاده می‌شود تا عنوان ستون‌ها از داده‌های بدنه جدول متمایز شوند.

```css
thead {
  border-bottom: 2px solid rgb(160 160 160);
  text-align: center;
  background-color: #2c5e77;
  color: white;
}

tbody {
  background-color: #e4f0f5;
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

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

tbody > tr > td:last-of-type {
  text-align: center;
}
```

**نتیجه**

#### سربرگ با چند ردیف

این مثال بخش سربرگ جدولی با دو ردیف را نشان می‌دهد.

**HTML**

در این مثال، مارکاپ جدول را از [مثال پایه](index.md#basic_head_structure) گسترش می‌دهیم و دو ردیف (`<tr>`) را داخل عنصر `<thead>` قرار می‌دهیم تا یک سربرگ چندردیفی ایجاد کنیم. همچنین یک ستون اضافه کرده‌ایم و نام دانش‌آموزان را به نام و نام خانوادگی تقسیم کرده‌ایم.

```html
<table>
  <thead>
    <tr>
      <th rowspan="2">Student ID</th>
      <th colspan="2">Student</th>
      <th rowspan="2">Major</th>
      <th rowspan="2">Credits</th>
    </tr>
    <tr>
      <th>First name</th>
      <th>Last name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3741255</td>
      <td>Martha</td>
      <td>Jones</td>
      <td>Computer Science</td>
      <td>240</td>
    </tr>
    <tr>
      <td>3971244</td>
      <td>Victor</td>
      <td>Nim</td>
      <td>Russian Literature</td>
      <td>220</td>
    </tr>
    <tr>
      <td>4100332</td>
      <td>Alexandra</td>
      <td>Petrov</td>
      <td>Astrophysics</td>
      <td>260</td>
    </tr>
  </tbody>
</table>
```

**گسترش سلول**

برای اینکه سلول‌های سرستون با ستون‌ها و ردیف‌های درست تراز شوند، از ویژگی‌های [`colspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/th/#colspan) و [`rowspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/th/#rowspan) روی عناصر `<th>` استفاده می‌شود. مقادیر این ویژگی‌ها مشخص می‌کنند که هر سلول سرستون (`<th>`) چند سلول را پوشش دهد. با توجه به نحوه تنظیم این ویژگی‌ها، دو سلول سرستونِ ردیف دوم با ستون‌های مربوطه تراز می‌شوند. هرکدام از این سلول‌ها به‌طور پیش‌فرض یک ردیف و یک ستون را پوشش می‌دهند، چون مقدار پیش‌فرض `colspan` و `rowspan` برابر `1` است.

در شکل زیر، نحوه پوشش ستون‌ها و ردیف‌ها در سلول‌های جدول نشان داده شده است:

**CSS**

استایل CSS مانند [مثال قبلی](index.md#basic_head_structure) بدون تغییر است.

```css
thead {
  border-bottom: 2px solid rgb(160 160 160);
  background-color: #2c5e77;
  color: white;
}

table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

tbody {
  background-color: #e4f0f5;
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

tbody > tr > td:last-of-type {
  text-align: center;
}
```

**نتیجه**

### خلاصه فنی

| [دسته‌های محتوا](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | هیچ‌کدام.                                                                                                                                                                        |
| ------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| محتوای مجاز                                                                           | صفر یا چند عنصر `<tr>`.                                                                                                                                                          |
| حذف تگ                                                                                | تگ شروع اجباری است. تگ پایان را می‌توان حذف کرد اگر عنصر `<thead>` بلافاصله بعد از آن یک عنصر `<tbody>` یا `<tfoot>` بیاید.                                                      |
| والدین مجاز                                                                           | یک عنصر `<table>`. عنصر `<thead>` باید بعد از هر عنصر `<caption>` و `<colgroup>` (حتی اگر به‌صورت ضمنی تعریف شده باشند) بیاید، اما قبل از هر عنصر `<tbody>`، `<tfoot>` و `<tr>`. |
| نقش ARIA ضمنی                                                                         | [`rowgroup`](../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role/)                                                                              |
| نقش‌های ARIA مجاز                                                                     | هر نقشی                                                                                                                                                                          |
| رابط DOM                                                                              | `HTMLTableSectionElement`                                                                                                                                                        |

### Specifications

### Browser compatibility

### See also

* [یادگیری: مبانی جدول‌های HTML](../../../../../../../en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics/)
* `caption`، `col`، `colgroup`، `table`، `tbody`، `td`، `tfoot`، `th`، `tr`: سایر عناصر مرتبط با جدول
* `background-color`: ویژگی CSS برای تنظیم رنگ پس‌زمینهٔ هر سلول سربرگ
* `border`: ویژگی CSS برای کنترل حاشیهٔ سلول‌های سربرگ
* `text-align`: ویژگی CSS برای تراز افقی محتوای هر سلول سربرگ
* `vertical-align`: ویژگی CSS برای تراز عمودی محتوای هر سلول سربرگ
