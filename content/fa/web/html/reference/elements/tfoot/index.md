---
title: "<tfoot> HTML table foot element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/tfoot"
translated_by: "n8n + AI"
---

## عنصر `<tfoot>` HTML (پای جدول)

عنصر **`<tfoot>`** [HTML](/en-US/docs/Web/HTML) مجموعه‌ای از ردیف‌های جدول (عناصر `<tr>`) را در بر می‌گیرد و نشان می‌دهد که این ردیف‌ها پای جدول را تشکیل می‌دهند. این بخش معمولاً شامل خلاصه‌ای از اطلاعات ستون‌ها است، مانند مجموع اعداد یک ستون.

```html interactive-example
<table>
  <caption>
    بودجه شورای شهر (به پوند) ۲۰۱۸
  </caption>
  <thead>
    <tr>
      <th scope="col">مورد</th>
      <th scope="col">هزینه</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">دونات</th>
      <td>۳٬۰۰۰</td>
    </tr>
    <tr>
      <th scope="row">لوازم التحریر</th>
      <td>۱۸٬۰۰۰</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row">جمع کل</th>
      <td>۲۱٬۰۰۰</td>
    </tr>
  </tfoot>
</table>
```

```css interactive-example
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

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

### ویژگی‌های منسوخ (Deprecated attributes)

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در زیر فقط برای مرجع هنگام به‌روزرسانی کدهای قدیمی و علاقه‌مندی تاریخی مستند شده‌اند.

- **`align`** {{deprecated_inline}}
  - : تراز افقی هر سلول پای جدول را مشخص می‌کند. مقادیر شمارشی (enumerated) ممکن عبارتند از `left`، `center`، `right`، `justify` و `char`. در صورت پشتیبانی، مقدار `char` محتوای متنی را روی کاراکتری که در ویژگی [`char`](#char) تعیین شده و با افستی که توسط [`charoff`](#charoff) مشخص شده تراز می‌کند. به جای این ویژگی منسوخ، از ویژگی CSS {{cssxref("text-align")}} استفاده کنید.

- **`bgcolor`** {{deprecated_inline}} {{non-standard_inline}}
  - : رنگ پس‌زمینه هر سلول پای جدول را تعریف می‌کند. مقدار یک رنگ HTML است: یا یک [کد RGB هگزادسیمال ۶ رقمی](/en-US/docs/Web/CSS/Reference/Values/hex-color) با پیشوند `#`، یا یک [کلمه کلیدی رنگ](/en-US/docs/Web/CSS/Reference/Values/named-color). سایر مقادیر CSS {{cssxref("&lt;color&gt;")}} پشتیبانی نمی‌شوند. به جای این ویژگی منسوخ، از ویژگی CSS {{cssxref("background-color")}} استفاده کنید.

- **`char`** {{deprecated_inline}}
  - : هیچ کاری انجام نمی‌دهد. در اصل برای مشخص کردن تراز محتوا نسبت به یک کاراکتر خاص در هر سلول پای جدول طراحی شده بود. مقادیر معمول شامل نقطه (`.`) برای تراز اعداد یا مقادیر پولی است. اگر [`align`](#align) روی `char` تنظیم نشده باشد، این ویژگی نادیده گرفته می‌شود.

- **`charoff`** {{deprecated_inline}}
  - : هیچ کاری انجام نمی‌دهد. در اصل برای تعیین تعداد کاراکترهای افست محتوای سلول پای جدول از کاراکتر تراز تعیین شده توسط ویژگی [`char`](#char) طراحی شده بود.

- **`valign`** {{deprecated_inline}}
  - : تراز عمودی هر سلول پای جدول را مشخص می‌کند. مقادیر شمارشی ممکن عبارتند از `baseline`، `bottom`، `middle` و `top`. به جای این ویژگی منسوخ، از ویژگی CSS {{cssxref("vertical-align")}} استفاده کنید.

## نکات استفاده

(در صورت وجود نکات اضافی، این بخش ادامه می‌یابد. اما در متن اصلی چیزی بعد از ویژگی‌ها نیامده است.)

- عنصر `<tfoot>` بعد از هر یک از عناصر `<caption>`، `<colgroup>`، `<thead>`، `<tbody>` و `<tr>` قرار می‌گیرد.
- عنصر `<tfoot>` همراه با عناصر مرتبط `<thead>` و `<tbody>` اطلاعات معنایی (semantic) مفیدی فراهم می‌کند و می‌توان از آن در رندر کردن برای صفحه نمایش یا چاپ استفاده کرد. مشخص کردن چنین گروه‌های محتوایی در جدول، اطلاعات زمینه‌ای ارزشمندی نیز برای فناوری‌های کمکی، از جمله صفحه‌خوان‌ها و موتورهای جستجو فراهم می‌کند.
- هنگام چاپ یک سند، اگر جدول چند صفحه‌ای باشد، بخش پایی جدول معمولاً اطلاعاتی را مشخص می‌کند که به‌صورت خلاصه میانی در هر صفحه خروجی داده می‌شود.

## مثال

برای مشاهده یک مثال کامل از جدول که استانداردهای رایج و بهترین روش‌ها را معرفی می‌کند، به عنصر `<table>` مراجعه کنید.

### جدول با footer

این مثال جدولی را نشان می‌دهد که به یک بخش سربرگ با عنوان ستون‌ها، یک بخش بدنه با داده‌های اصلی جدول، و یک بخش پایی که داده‌های یکی از ستون‌ها را خلاصه می‌کند، تقسیم شده است.

#### HTML

عناصر `<thead>`، `<tbody>` و `<tfoot>` برای ساختاربندی یک جدول ساده به بخش‌های معنایی (semantic) استفاده می‌شوند. عنصر `<tfoot>` نمایانگر بخش پایی جدول است که شامل یک ردیف (`<tr>`) است و میانگین محاسبه‌شده مقادیر ستون «Credits» را نشان می‌دهد.

برای اختصاص سلول‌های بخش پایی به ستون‌های درست، از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/th#colspan) روی عنصر `<th>` استفاده می‌شود تا سلول سربرگ سطر روی سه ستون اول جدول کشیده شود. تنها سلول داده (`<td>`) در بخش پایی به‌صورت خودکار در مکان درست، یعنی ستون چهارم، قرار می‌گیرد و مقدار پیش‌فرض ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) که ذکر نشده، برابر با `1` است. علاوه بر این، ویژگی [`scope`](/en-US/docs/Web/HTML/Reference/Elements/th#scope) روی سلول سربرگ (`<th>`) در بخش پایی به مقدار `row` تنظیم می‌شود تا به‌صراحت مشخص کند که این سلول سربرگ به سلول‌های جدول در همان سطر مربوط است؛ در مثال ما همان سلول داده‌ای است که میانگین محاسبه‌شده را در سطر پایی نشان می‌دهد.

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
  <tfoot>
    <tr>
      <th colspan="3" scope="row">Average Credits</th>
      <td>240</td>
    </tr>
  </tfoot>
</table>
```

#### CSS

برای استایل‌دهی و برجسته‌کردن بخش پایی جدول، از چند CSS ساده استفاده شده است تا سلول‌های این بخش نسبت به داده‌های بدنه جدول متمایز شوند.

```css
tfoot {
  border-top: 3px dotted rgb(160 160 160);
  background-color: #2c5e77;
  color: white;
}

tfoot th {
  text-align: right;
}

tfoot td {
  font-weight: bold;
}

thead {
  border-bottom: 2px solid rgb(160 160 160);
  background-color: #2c5e77;
  color: white;
}

tbody {
  background-color: #e4f0f5;
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

tr > td:last-of-type {
  text-align: center;
}
```

#### نتیجه

## خلاصه فنی

## ویژگی‌ها

| ویژگی | مقدار |
|---|---|
| دسته‌بندی محتوا | هیچ. |
| محتوای مجاز | صفر یا بیشتر عنصر `<tr>`. |
| حذف تگ | تگ شروع اجباری است. اگر در عنصر والد `<table>` محتوای دیگری وجود نداشته باشد، می‌توان تگ پایانی را حذف کرد. |
| والدین مجاز | یک عنصر `<table>`. عنصر `<tfoot>` باید بعد از هر عنصر `<caption>`، `<colgroup>`، `<thead>`، `<tbody>` و `<tr>` بیاید. توجه داشته باشید که این الزام در HTML است. در HTML4، برعکس این بود: عنصر `<tfoot>` نمی‌توانست بعد از عناصر `<tbody>` و `<tr>` قرار بگیرد. |
| نقش ARIA ضمنی | <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role">rowgroup</a> |
| نقش‌های ARIA مجاز | هر نقشی |
| رابط DOM | `HTMLTableSectionElement` |

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- [یادگیری: مبانی جدول HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- سایر عناصر مرتبط با جدول: `<caption>`، `<col>`، `<colgroup>`، `<table>`، `<tbody>`، `<td>`، `<th>`، `<thead>`، `<tr>`
- `background-color`: ویژگی CSS برای تنظیم رنگ پس‌زمینه هر سلول پاورقی
- `border`: ویژگی CSS برای کنترل حاشیه‌های سلول‌های پاورقی
- `text-align`: ویژگی CSS برای تراز افقی محتوای هر سلول پاورقی
- `vertical-align`: ویژگی CSS برای تراز عمودی محتوای هر سلول پاورقی