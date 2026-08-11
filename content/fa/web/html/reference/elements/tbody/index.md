---
title: "<tbody> HTML table body element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/tbody"
translated_by: "n8n + AI"
---

المان `<tbody>` یک [element](/en-US/docs/Web/HTML) در HTML است که مجموعه‌ای از ردیف‌های جدول (المان‌های `<tr>`) را در بر می‌گیرد و نشان می‌دهد که این ردیف‌ها بدنهٔ داده‌های اصلی جدول را تشکیل می‌دهند.

```html interactive-example
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

## Attributes

این المان شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

### Attributes منسوخ‌شده

attributeهای زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع هنگام به‌روزرسانی کدهای قدیمی و از نظر تاریخی ثبت شده‌اند.

- `align` {{deprecated_inline}}
  - : تراز افقی هر سلول بدنه را مشخص می‌کند. مقادیر ممکن {{Glossary("enumerated")}} عبارتند از `left`، `center`، `right`، `justify` و `char`. در صورت پشتیبانی، مقدار `char` محتوای متنی را بر اساس کاراکتر مشخص‌شده در attribute [`char`](#char) و offset تعریف‌شده توسط attribute [`charoff`](#charoff) تراز می‌کند. به جای این attribute از خاصیت CSS {{cssxref("text-align")}} استفاده کنید.

- `bgcolor` {{deprecated_inline}} {{non-standard_inline}}
  - : رنگ پس‌زمینهٔ هر سلول بدنه را تعریف می‌کند. مقدار آن یک رنگ HTML است: یا یک کد RGB هگزادسیمال ۶ رقمی ([6-digit hexadecimal RGB code](/en-US/docs/Web/CSS/Reference/Values/hex-color)) با پیشوند `#`، یا یک کلیدواژهٔ رنگ ([color keyword](/en-US/docs/Web/CSS/Reference/Values/named-color)). سایر مقادیر CSS {{cssxref("&lt;color&gt;")}} پشتیبانی نمی‌شوند. به جای این attribute از خاصیت CSS {{cssxref("background-color")}} استفاده کنید.

- `char` {{deprecated_inline}}
  - : تراز محتوای هر سلول بدنه را نسبت به یک کاراکتر مشخص می‌کند. برای مثال، هنگام تراز اعداد یا مقادیر پولی از نقطه (`.`) استفاده می‌شود. اگر [`align`](#align) روی `char` تنظیم نشده باشد، این attribute نادیده گرفته می‌شود.

- `charoff` {{deprecated_inline}}
  - : تعداد کاراکترهای offset محتوای سلول بدنه از کاراکتر تراز مشخص‌شده توسط attribute [`char`](#char) را تعیین می‌کند.

- `valign` {{deprecated_inline}}
  - : تراز عمودی هر سلول بدنه را مشخص می‌کند. مقادیر ممکن {{Glossary("enumerated")}} عبارتند از `baseline`، `bottom`، `middle` و `top`. به جای این attribute از خاصیت CSS {{cssxref("vertical-align")}} استفاده کنید.

## نکات استفاده

(بخش "Usage notes" در متن ورودی وجود ندارد، بنابراین نیازی به ترجمه نیست)

- عنصر `<tbody>` بعد از {{HTMLElement("caption")}}، {{HTMLElement("colgroup")}} و {{HTMLElement("thead")}} قرار می‌گیرد.
- اگر عناصر {{HTMLElement("tr")}} به‌عنوان فرزند مستقیم {{HTMLElement("table")}} مشخص شده باشند (برای توضیح شرایط معتبر بودن این کار به [خلاصه فنی](#technical_summary) مراجعه کنید)، مرورگر یک عنصر `<tbody>` می‌سازد که آن‌ها را در بر می‌گیرد. در نتیجه، انتخاب‌گرهای CSS مثل `table > tr` این عناصر را انتخاب نمی‌کنند. برای مثال به [مشخص نکردن body](#not_specifying_a_body) مراجعه کنید.
- استفاده از بیش از یک `<tbody>` در هر جدول مجاز است، به شرطی که همه آن‌ها پشت سر هم قرار بگیرند. این کار امکان تقسیم سطرها (عناصر {{HTMLElement("tr")}}) در جدول‌های بزرگ به بخش‌هایی را فراهم می‌کند که هر کدام را می‌توان به‌صورت جداگانه قالب‌بندی کرد. اگر به‌صورت عناصر پشت‌سر هم نشانه‌گذاری نشده باشند، مرورگر این خطای نویسنده را تصحیح می‌کند و اطمینان حاصل می‌کند که عناصر {{HTMLElement("thead")}} و {{HTMLElement("tfoot")}} به‌ترتیب اولین و آخرین عناصر جدول رندر می‌شوند.
- عنصر `<tbody>` به همراه عناصر مرتبط {{HTMLElement("thead")}} و {{HTMLElement("tfoot")}} اطلاعات معنایی (semantic) مفیدی ارائه می‌دهد و می‌تواند هنگام رندر برای صفحه‌نمایش یا چاپ استفاده شود. مشخص کردن چنین گروه‌های محتوایی برای جدول، اطلاعات زمینه‌ای ارزشمندی برای فناوری‌های کمکی از جمله صفحه‌خوان‌ها و موتورهای جست‌وجو فراهم می‌کند.
- هنگام چاپ یک سند، در صورت وجود جدول چندصفحه‌ای، عناصر {{HTMLElement("thead")}} و {{HTMLElement("tfoot")}} معمولاً اطلاعاتی را مشخص می‌کنند که در هر صفحه ثابت (یا حداقل بسیار مشابه) باقی می‌ماند، در حالی که محتوای عنصر `<tbody>` معمولاً از صفحه‌ای به صفحه دیگر متفاوت است.
- وقتی جدولی در زمینه‌ای صفحه‌نمایش (مثل یک پنجره) نمایش داده می‌شود که به اندازه کافی بزرگ نیست تا کل جدول را نشان دهد، عامل کاربر (user agent) ممکن است به کاربر اجازه دهد محتوای بلوک‌های {{HTMLElement("thead")}}، `<tbody>`، {{HTMLElement("tfoot")}} و {{HTMLElement("caption")}} را به‌صورت جداگانه از یکدیگر برای همان {{HTMLElement("table")}} والد اسکرول کند.

## مثال‌ها

برای یک مثال کامل از جدول که استانداردها و بهترین روش‌های رایج را معرفی می‌کند، به {{HTMLElement("table")}} مراجعه کنید.

### مشخص نکردن body

این مثال نشان می‌دهد که اگر سطرها درون یک عنصر گروه‌بندی جدول (`<tbody>`، `<tfoot>` یا `<thead>`) قرار نگیرند و به‌عنوان فرزند مستقیم عنصر {{HTMLElement("table")}} باشند (مانند این مثال)، مرورگر به‌طور خودکار عناصر {{HTMLElement("tr")}} را درون یک `<tbody>` قرار می‌دهد.

#### HTML

در اینجا یک جدول بسیار ساده با چند سطر جدول (عناصر {{HTMLElement("tr")}}) که شامل داده‌هایی (عناصر {{HTMLElement("td")}}) درباره دانشجویان است، ساخته شده است.

```html
<table>
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
</table>
```

#### CSS

به CSS این مثال توجه کنید که در آن یک {{cssxref("background-color")}} برای عنصر `<tbody>` مشخص شده و `tbody` به‌عنوان بخشی از یک {{Glossary("css_selector", "CSS selector")}} اضافی استفاده شده است. همچنین می‌توانید از {{Glossary("developer_tools", "ابزارهای توسعه مرورگر")}} برای بررسی وجود عنصر `<tbody>` در {{Glossary("dom", "DOM")}} استفاده کنید.

```css
tbody {
  background-color: #e4f0f5;
}

tbody > tr > td:last-of-type {
  width: 60px;
  text-align: center;
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

td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}
```

#### نتیجه

(خروجی تعاملی در اینجا نمایش داده می‌شود)

### ساختار پایه body

(در اینجا محتوای بخش "Basic body structure" وجود ندارد، اما در صورت وجود، مشابه بازنویسی می‌شد.)

### بدنهٔ اصلی (Basic body structure)

این مثال، جدول ساده‌ای را که در [مثال قبلی](#not_specifying_a_body) معرفی شد، گسترش و بهبود می‌دهد.

#### HTML

در اینجا از یک سرجدول (عنصر `<thead>`) استفاده می‌کنیم و یک `<tbody>` را به‌صورت صریح تعریف می‌کنیم تا جدول را به بخش‌های معنایی (semantic) تقسیم کنیم. سرجدول شامل سرستون‌ها (عناصر `<th>`) است. عنصر `<tbody>` بخش بدنهٔ جدول را نشان می‌دهد که شامل چندین ردیف (عناصر `<tr>`) با داده‌های اصلی جدول است – در اینجا اطلاعات هر دانشجو.

استفاده از این گروه‌های محتوایی جدول و نشانه‌گذاری semantic نه‌تنها برای نمایش بصری (از طریق استایل‌دهی CSS) و ارائهٔ اطلاعات زمینه‌ای به فناوری‌های کمکی مفید است، بلکه تعریف صریح `<tbody>` به مرورگر کمک می‌کند ساختار مورد نظر جدول را ایجاد کند و از نتایج ناخواسته جلوگیری نماید.

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

#### CSS

استایل CSS تقریباً مشابه [مثال قبلی](#not_specifying_a_body) است، با این تفاوت که اندکی استایل پایه برای برجسته‌سازی سرجدول اضافه شده تا سرستون‌ها از داده‌های بدنه متمایز شوند. مانند [مثال بالا](#not_specifying_a_body)، از [type selector](/en-US/docs/Web/CSS/Reference/Selectors/Type_selectors) `tbody` برای استایل‌دهی به سلول‌های بدنه استفاده شده است.

```css
tbody {
  background-color: #e4f0f5;
}

tbody > tr > td:last-of-type {
  text-align: center;
}

thead {
  border-bottom: 2px solid rgb(160 160 160);
  background-color: #2c5e77;
  color: white;
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

{{EmbedLiveSample("Basic_body_structure", 650, 140)}}

### چند بدنه (Multiple bodies)

این مثال، جدول [مثال بالا](#basic_body_structure) را بیشتر گسترش می‌دهد و با معرفی چندین بخش بدنه، آن را بهبود می‌بخشد.

استفاده از چندین عنصر `<tbody>` امکان ایجاد گروه‌بندی ردیف‌ها را در یک جدول فراهم می‌کند. هر بدنهٔ جدول می‌تواند یک یا چند ردیف سرصفحهٔ مخصوص خود داشته باشد؛ اما **در هر جدول تنها یک عنصر `<thead>` مجاز است**. به همین دلیل، می‌توان از عناصر `<tr>` حاوی `<th>` برای ایجاد سرصفحه‌های درون هر `<tbody>` استفاده کرد.

#### HTML

بر اساس جدول [مثال پایهٔ قبلی](#basic_body_structure)، دانشجویان بیشتری اضافه شده و به‌جای ذکر رشتهٔ هر دانشجو در هر ردیف، دانشجویان بر اساس رشته گروه‌بندی شده‌اند. هر رشته درون یک بلوک `<tbody>` مجزا قرار گرفته است. اولین ردیف (عنصر `<tr>`) هر بلوک به عنوان سرصفحهٔ آن بلوک عمل می‌کند و عنوان رشته را درون یک عنصر `<th>` که با ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/th#colspan) در هر سه ستون جدول گسترش یافته، نمایش می‌دهد. هر ردیف باقی‌مانده درون هر `<tbody>` یک دانشجو را نشان می‌دهد.

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
      <th colspan="4">Computer Science</th>
    </tr>
    <tr>
      <td>3741255</td>
      <td>Jones, Martha</td>
      <td>Computer Science</td>
      <td>240</td>
    </tr>
    <tr>
      <td>4077830</td>
      <td>Pierce, Benjamin</td>
      <td>Computer Science</td>
      <td>200</td>
    </tr>
    <tr>
      <td>5151701</td>
      <td>Kirk, James</td>
      <td>Computer Science</td>
      <td>190</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <th colspan="4">Russian Literature</th>
    </tr>
    <tr>
      <td>3971244</td>
      <td>Nim, Victor</td>
      <td>Russian Literature</td>
      <td>220</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <th colspan="4">Astrophysics</th>
    </tr>
    <tr>
      <td>4100332</td>
      <td>Petrov, Alexandra</td>
      <td>Astrophysics</td>
      <td>260</td>
    </tr>
    <tr>
      <td>8892377</td>
      <td>Toyota, Hiroko</td>
      <td>Astrophysics</td>
      <td>210</td>
    </tr>
  </tbody>
</table>
```

#### CSS

استایل CSS مشابه مثال قبلی است، با این تفاوت که برای تأکید بر سرصفحه‌های هر بدنه (که با `<th>` مشخص شده‌اند) یک استایل متمایز اضافه شده است.

```css
tbody {
  background-color: #e4f0f5;
}

tbody > tr > th {
  background-color: #2c5e77;
  color: white;
  text-align: left;
}

tbody > tr > td:last-of-type {
  text-align: center;
}

thead {
  border-bottom: 2px solid rgb(160 160 160);
  background-color: #2c5e77;
  color: white;
}

tbody + tbody {
  border-top: 2px solid rgb(160 160 160);
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

{{EmbedLiveSample("Multiple_bodies", 650, 250)}}

```html
<table>
  <thead>
    <tr>
      <th>Student ID</th>
      <th>Name</th>
      <th>Credits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th colspan="3">Computer Science</th>
    </tr>
    <tr>
      <td>3741255</td>
      <td>Jones, Martha</td>
      <td>240</td>
    </tr>
    <tr>
      <td>4077830</td>
      <td>Pierce, Benjamin</td>
      <td>200</td>
    </tr>
    <tr>
      <td>5151701</td>
      <td>Kirk, James</td>
      <td>230</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <th colspan="3">Russian Literature</th>
    </tr>
    <tr>
      <td>3971244</td>
      <td>Nim, Victor</td>
      <td>220</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <th colspan="3">Astrophysics</th>
    </tr>
    <tr>
      <td>4100332</td>
      <td>Petrov, Alexandra</td>
      <td>260</td>
    </tr>
    <tr>
      <td>8892377</td>
      <td>Toyota, Hiroko</td>
      <td>240</td>
    </tr>
  </tbody>
</table>
```

#### CSS

بیشتر CSS دست‌نخورده باقی مانده است. با این حال، یک استایل کمی ظریف‌تر برای سلول‌های header (عنوان ستون) که مستقیماً داخل `<tbody>` قرار دارند (در مقابل آن‌هایی که در `<thead>` هستند) اضافه شده است. از این استایل برای headerهایی استفاده می‌شود که نشان‌دهندهٔ رشتهٔ مربوط به هر بخش جدول هستند.

```css
tbody > tr > th {
  border-top: 2px solid rgb(160 160 160);
  border-bottom: 1px solid rgb(140 140 140);
  background-color: #e4f0f5;
  font-weight: normal;
}

tbody {
  background-color: whitesmoke;
}

thead {
  background-color: #2c5e77;
  color: white;
}
```

#### Result

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>None.</td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>Zero or more {{ HTMLElement("tr") }} elements.</td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>
        A <code>&lt;tbody&gt;</code> element's start tag can be omitted if the first thing inside the <code>&lt;tbody&gt;</code> element is a {{HTMLElement("tr")}} element, and if the element is not immediately preceded by a <code>&lt;tbody&gt;</code>, {{HTMLElement("thead")}}, or {{HTMLElement("tfoot")}} element whose end tag has been omitted. (It can't be omitted if the element is empty.)
        A <code>&lt;tbody&gt;</code> element's end tag can be omitted if the <code>&lt;tbody&gt;</code> element is immediately followed by a <code>&lt;tbody&gt;</code> or {{HTMLElement("tfoot")}} element, or if there is no more content in the parent element.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        Within the required parent {{ HTMLElement("table") }} element,
        the <code>&lt;tbody&gt;</code> element can be added after any
        {{ HTMLElement("caption") }}, {{HTMLElement("colgroup") }},
        and {{ HTMLElement("thead") }} elements.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role"
            >rowgroup</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>Any</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLTableSectionElement")}}</td>
    </tr>
  </tbody>
</table>
```

- [Learn: HTML table basics](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- `<caption>`, `<col>`, `<colgroup>`, `<table>`, `<td>`, `<tfoot>`, `<th>`, `<thead>`, `<tr>`: سایر عناصر مرتبط با جدول
- `background-color`: خاصیت CSS برای تنظیم رنگ پس‌زمینهٔ هر سلول بدنه
- `border`: خاصیت CSS برای کنترل حاشیه‌های سلول‌های بدنه
- `text-align`: خاصیت CSS برای تراز افقی محتوای هر سلول بدنه
- `vertical-align`: خاصیت CSS برای تراز عمودی محتوای هر سلول بدنه