---
title: "<colgroup> HTML table column group element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/colgroup"
translated_by: "n8n + AI"
---

عنصر `<colgroup>` یک گروه از ستون‌ها را درون یک جدول تعریف می‌کند.

```html interactive-example
<table>
  <caption>
    Superheros and sidekicks
  </caption>
  <colgroup>
    <col />
    <col span="2" class="batman" />
    <col span="2" class="flash" />
  </colgroup>
  <thead>
    <tr>
      <td></td>
      <th scope="col">Batman</th>
      <th scope="col">Robin</th>
      <th scope="col">The Flash</th>
      <th scope="col">Kid Flash</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Skill</th>
      <td>Smarts, strong</td>
      <td>Dex, acrobat</td>
      <td>Super speed</td>
      <td>Super speed</td>
    </tr>
  </tbody>
</table>
```

```css interactive-example
.batman {
  background-color: #d7d9f2;
}

.flash {
  background-color: #ffe8d4;
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
  padding: 8px 6px;
}

td {
  text-align: center;
}
```

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

- `span`
  - تعداد ستون‌های متوالی که عنصر `<colgroup>` پوشش می‌دهد را مشخص می‌کند. مقدار باید یک عدد صحیح مثبت بزرگتر از صفر باشد. اگر وجود نداشته باشد، مقدار پیش‌فرض `1` است.

    > **نکته:** اگر داخل `<colgroup>` یک یا چند عنصر {{HTMLElement("col")}} وجود داشته باشد، استفاده از ویژگی `span` مجاز نیست.

### ویژگی‌های منسوخ

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع هنگام به‌روزرسانی کد موجود و علاقه‌مندی تاریخی مستند شده‌اند.

- `align` {{deprecated_inline}}
  - تراز افقی سلول‌های هر گروه ستون را مشخص می‌کند. مقادیر ممکن {{Glossary("enumerated")}} عبارتند از `left`، `center`، `right`، `justify` و `char`. در صورت پشتیبانی، مقدار `char` محتوای متنی را بر اساس کاراکتری که در ویژگی [`char`](#char) تعریف شده و offset مشخص شده توسط [`charoff`](#charoff) تراز می‌کند. توجه کنید که عناصر فرزند {{HTMLElement("col")}} می‌توانند این مقدار را با ویژگی [`align`](/en-US/docs/Web/HTML/Reference/Elements/col#align) خود بازنویسی کنند. به جای این ویژگی منسوخ، از ویژگی CSS {{cssxref("text-align")}} روی عناصر {{htmlelement("td")}} و {{htmlelement("th")}} استفاده کنید.

    > **نکته:** تنظیم `text-align` روی عنصر `<colgroup>` تأثیری ندارد، زیرا عناصر {{HTMLElement("td")}} و {{HTMLElement("th")}} فرزند `<colgroup>` نیستند و بنابراین از آن ارث‌بری نمی‌کنند.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده نمی‌کند، از انتخابگر CSS `td:nth-of-type(an+b)` به ازای هر ستون استفاده کنید، که `a` تعداد کل ستون‌های جدول و `b` موقعیت ترتیبی ستون در جدول است. مثلاً `td:nth-of-type(7n+2) { text-align: right; }` سلول‌های ستون دوم را راست‌چین می‌کند.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده می‌کند، می‌توان با ترکیب انتخابگرهای ویژگی CSS مناسب مانند `[colspan=n]` به نتیجه مشابهی رسید، هرچند این کار ساده نیست.

- `bgcolor` (منسوخ)
  - رنگ پس‌زمینهٔ سلول‌های هر گروه ستون را مشخص می‌کند. مقدار آن یک رنگ HTML است: یا یک [کد هگزادسیمال RGB شش‌رقمی](/en-US/docs/Web/CSS/Reference/Values/hex-color) با پیشوند `#`، یا یک [کلمهٔ کلیدی رنگ](/en-US/docs/Web/CSS/Reference/Values/named-color). سایر مقادیر CSS مانند {{cssxref("&lt;color&gt;")}} پشتیبانی نمی‌شوند. به‌جای این ویژگی، از خصوصیت CSS {{cssxref("background-color")}} استفاده کنید، زیرا این ویژگی منسوخ شده است.

- `char` (منسوخ)
  - هیچ کاری انجام نمی‌دهد. در اصل برای تعیین تراز محتوا نسبت به یک کاراکتر خاص در سلول‌های گروه ستون در نظر گرفته شده بود. مقادیر معمول شامل نقطه (`.`) برای تراز اعداد یا مقادیر پولی است. اگر [`align`](#align) روی `char` تنظیم نشده باشد، این ویژگی نادیده گرفته می‌شود، اما همچنان به عنوان مقدار پیش‌فرض برای [`align`](/en-US/docs/Web/HTML/Reference/Elements/col#align) عناصر {{HTMLElement("col")}} که عضو این گروه ستون هستند استفاده می‌شود.

- `charoff` (منسوخ)
  - هیچ کاری انجام نمی‌دهد. در اصل برای تعیین تعداد کاراکترهای جابجایی محتوای سلول گروه ستون از کاراکتر تراز مشخص‌شده توسط ویژگی [`char`](#char) در نظر گرفته شده بود.

- `valign` (منسوخ)
  - تراز عمودی سلول‌های هر گروه ستون را مشخص می‌کند. مقادیر شمارشی (enumerated) ممکن عبارتند از `baseline`، `bottom`، `middle` و `top`. توجه داشته باشید که عناصر فرزند {{HTMLElement("col")}} ممکن است این مقدار را با ویژگی [`valign`](/en-US/docs/Web/HTML/Reference/Elements/col#valign) خود override کنند. به‌جای این ویژگی، از خصوصیت CSS {{cssxref("vertical-align")}} روی عناصر {{htmlelement("td")}} و {{htmlelement("th")}} استفاده کنید، زیرا این ویژگی منسوخ شده است.

    > **نکته:** تنظیم `vertical-align` روی عنصر `<colgroup>` تأثیری ندارد، زیرا عناصر {{HTMLElement("td")}} و {{HTMLElement("th")}} فرزند `<colgroup>` نیستند و بنابراین از آن ارث‌بری نمی‌کنند.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده نمی‌کند، از انتخابگر CSS [`td:nth-of-type()`](/en-US/docs/Web/CSS/Reference/Selectors/:nth-of-type) برای هر ستون استفاده کنید، مثلاً `td:nth-of-type(2) { vertical-align: middle; }` تا سلول‌های ستون دوم را به‌صورت عمودی وسط‌چین کند.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده می‌کند، می‌توان با ترکیب انتخابگرهای مناسب ویژگی CSS مانند `[colspan=n]` به این اثر دست یافت، هرچند این کار ساده نیست.

- `width` (منسوخ)
  - عرض پیش‌فرض برای هر ستون در گروه ستون فعلی را مشخص می‌کند. علاوه بر مقادیر استاندارد پیکسل و درصد، این ویژگی می‌تواند شکل خاص `0*` را نیز بگیرد، به این معنی که عرض هر ستون باید حداقل عرض لازم برای نگه‌داشتن محتوای آن ستون باشد. عرض‌های نسبی مانند `5*` نیز قابل استفاده هستند. توجه داشته باشید که عناصر فرزند {{HTMLElement("col")}} ممکن است این مقدار را با ویژگی [`width`](/en-US/docs/Web/HTML/Reference/Elements/col#width) خود override کنند. به‌جای این ویژگی، از خصوصیت CSS {{cssxref("width")}} استفاده کنید، زیرا این ویژگی منسوخ شده است.

- تگ `<colgroup>` باید داخل یک `<table>` قرار بگیرد؛ بعد از هر عنصر `<caption>` (در صورت استفاده)، اما قبل از هر یک از عناصر `<thead>`، `<tbody>`، `<tfoot>` و `<tr>`.
- تنها تعداد محدودی از ویژگی‌های CSS روی `<colgroup>` اثر می‌گذارند:
  - `background`: ویژگی‌های مختلف `background` پس‌زمینه سلول‌های داخل گروه ستون را تنظیم می‌کنند. از آنجا که رنگ پس‌زمینه گروه ستون روی جدول کشیده می‌شود، اما زیر پس‌زمینه‌هایی که به ستون‌ها (`<col>`)، گروه ردیف‌ها (`<thead>`، `<tbody>` و `<tfoot>`)، ردیف‌ها (`<tr>`) و سلول‌های تکی (`<th>` و `<td>`) اعمال می‌شود، پس‌زمینهٔ گروه‌های ستون در جدول فقط وقتی دیده می‌شود که همهٔ لایه‌های روی آن پس‌زمینهٔ شفاف داشته باشند.
  - `border`: ویژگی‌های مختلف `border` اعمال می‌شوند، اما فقط اگر روی `<table>` مقدار `border-collapse: collapse` تنظیم شده باشد.
  - `visibility`: مقدار `collapse` برای یک گروه ستون باعث می‌شود همهٔ سلول‌های ستون‌های آن گروه رندر نشوند و سلول‌هایی که به ستون‌های دیگر امتداد دارند بریده شوند. فضایی که این ستون‌ها در گروه ستون اشغال می‌کردند حذف می‌شود. با این حال، اندازهٔ سایر ستون‌ها همچنان طوری محاسبه می‌شود که انگار سلول‌های ستون(های) جمع‌شده در گروه ستون وجود دارند. سایر مقادیر `visibility` هیچ اثری ندارند.
  - `width`: ویژگی `width` یک حداقل عرض برای ستون‌های داخل گروه ستون تعیین می‌کند، انگار که `min-width` تنظیم شده باشد.

## مثال

برای مشاهدهٔ یک مثال کامل از جدول که استانداردهای رایج و بهترین روش‌ها را معرفی می‌کند، به صفحهٔ `<table>` مراجعه کنید.

این مثال یک جدول هفت‌ستونه را نشان می‌دهد که با دو عنصر `<colgroup>` تقسیم شده است و این عناصر چند ستون را پوشش می‌دهند.

### HTML

برای ساختاربندی یک جدول ساده، دو عنصر `<colgroup>` به‌کار رفته‌اند تا گروه‌های ستون ساخته شوند. تعداد ستون‌های هر گروه ستون با ویژگی [`span`](#span) مشخص شده است.

```html
<table>
  <caption>
    Personal weekly activities
  </caption>
  <colgroup span="5" class="weekdays"></colgroup>
  <colgroup span="2" class="weekend"></colgroup>
  <thead>
    <tr>
      <th>Mon</th>
      <th>Tue</th>
      <th>Wed</th>
      <th>Thu</th>
      <th>Fri</th>
      <th>Sat</th>
      <th>Sun</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Clean room</td>
      <td>Football training</td>
      <td>Dance Course</td>
      <td>History Class</td>
      <td>Buy drinks</td>
      <td>Study hour</td>
      <td>Free time</td>
    </tr>
    <tr>
      <td>Yoga</td>
      <td>Chess Club</td>
      <td>Meet friends</td>
      <td>Gymnastics</td>
      <td>Birthday party</td>
      <td>Fishing trip</td>
      <td>Free time</td>
    </tr>
  </tbody>
</table>
```

### CSS

می‌توان از ستون‌های گروه‌بندی‌شده برای برجسته‌سازی بصری ساختار جدول با CSS استفاده کرد:

```css
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
}

caption {
  caption-side: bottom;
  padding: 10px;
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 6px;
  text-align: center;
}

.weekdays {
  background-color: #d7d9f2;
}

.weekend {
  background-color: #ffe8d4;
}
```

```css hidden
table {
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}
```

#### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>هیچکدام.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        اگر ویژگی <code>span</code> وجود داشته باشد: هیچ.<br />اگر ویژگی وجود نداشته باشد: صفر یا بیشتر عنصر <code>&lt;col&gt;</code>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        تگ شروع ممکن است حذف شود، اگر اولین فرزند آن یک عنصر <code>&lt;col&gt;</code> باشد و قبل از آن یک <code>&lt;colgroup&gt;</code> با تگ پایانی حذف‌شده وجود نداشته باشد.<br />تگ پایانی ممکن است حذف شود، اگر بعد از آن فاصله یا کامنت نباشد.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        یک عنصر <code>&lt;table&gt;</code>. <code>&lt;colgroup&gt;</code> باید بعد از هر عنصر <code>&lt;caption&gt;</code> و قبل از هر عنصر <code>&lt;thead&gt;</code>، <code>&lt;tbody&gt;</code>، <code>&lt;tfoot&gt;</code> و <code>&lt;tr&gt;</code> قرار گیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLTableColElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

(حذف شد)

## سازگاری با مرورگرها

(حذف شد)

## همچنین ببینید

- [Learn: HTML table basics](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- عناصر مرتبط با جدول: <code>&lt;caption&gt;</code>، <code>&lt;col&gt;</code>، <code>&lt;table&gt;</code>، <code>&lt;tbody&gt;</code>، <code>&lt;td&gt;</code>، <code>&lt;tfoot&gt;</code>، <code>&lt;th&gt;</code>، <code>&lt;thead&gt;</code>، <code>&lt;tr&gt;</code>
- خصوصیت CSS <code>background-color</code> برای تنظیم رنگ پس‌زمینه سلول‌های گروه ستون
- خصوصیت CSS <code>border</code> برای کنترل حاشیه سلول‌های گروه ستون
- خصوصیت CSS <code>text-align</code> برای تراز افقی محتوای سلول‌های گروه ستون
- خصوصیت CSS <code>vertical-align</code> برای تراز عمودی محتوای سلول‌های گروه ستون
- خصوصیت CSS <code>visibility</code> برای مخفی (یا نمایش) سلول‌های یک گروه ستون
- خصوصیت CSS <code>width</code> برای کنترل عرض پیش‌فرض هر ستون در یک گروه ستون
- شبه‌کلاس‌های CSS <code>:nth-of-type</code>، <code>:first-of-type</code>، <code>:last-of-type</code> برای انتخاب سلول‌های ستون مورد نظر