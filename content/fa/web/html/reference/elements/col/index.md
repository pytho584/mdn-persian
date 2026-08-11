---
title: "<col> HTML table column element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/col"
translated_by: "n8n + AI"
---

# `<col>` : عنصر ستون جدول HTML

عنصر **`<col>`** در HTML یک یا چند ستون را در یک گروه ستونی (column group) که توسط عنصر والد {{HTMLElement("colgroup")}} نمایش داده می‌شود، تعریف می‌کند. عنصر `<col>` فقط به عنوان فرزند یک عنصر `<colgroup>` معتبر است که ویژگی [`span`](/en-US/docs/Web/HTML/Reference/Elements/colgroup#span) در آن تعریف نشده باشد.

{{InteractiveExample("HTML Demo: &lt;col&gt;", "tabbed-taller")}}

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

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- **`span`**
  - تعداد ستون‌های متوالی که عنصر `<col>` پوشش می‌دهد را مشخص می‌کند. مقدار باید یک عدد صحیح مثبت بزرگتر از صفر باشد. اگر وجود نداشته باشد، مقدار پیش‌فرض آن `1` است.

### ویژگی‌های منسوخ (Deprecated attributes)

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع هنگام به‌روزرسانی کدهای قدیمی و علاقه‌مندی تاریخی مستند شده‌اند.

- **`align`** {{deprecated_inline}}
  - تراز افقی سلول‌های هر ستون را مشخص می‌کند. مقادیر ممکن ({{Glossary("enumerated")}}) عبارتند از `left`، `center`، `right`، `justify` و `char`. در صورت پشتیبانی، مقدار `char` محتوای متنی را بر اساس کاراکتری که در ویژگی [`char`](#char) تعریف شده و با افست مشخص‌شده توسط ویژگی [`charoff`](#charoff) تراز می‌کند. توجه داشته باشید که این ویژگی مقدار [`align`](/en-US/docs/Web/HTML/Reference/Elements/colgroup#align) تعریف‌شده در عنصر والد {{HTMLElement("colgroup")}} را بازنویسی می‌کند. به جای آن از ویژگی CSS {{cssxref("text-align")}} روی عناصر {{htmlelement("td")}} و {{htmlelement("th")}} استفاده کنید، زیرا این ویژگی منسوخ شده است.

    > [!NOTE]
    > تنظیم `text-align` روی عنصر `<col>` تأثیری ندارد، زیرا `<col>` فرزندی ندارد و بنابراین هیچ عنصری از آن ارث‌بری نمی‌کند.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده نمی‌کند، از انتخابگر CSS `td:nth-of-type(an+b)` استفاده کنید. `a` را صفر و `b` را موقعیت ستون در جدول قرار دهید. مثلاً `td:nth-of-type(2) { text-align: right; }` برای راست‌چین کردن سلول‌های ستون دوم.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده می‌کند، می‌توان با ترکیب انتخابگرهای ویژگی مناسب CSS مانند `[colspan=n]` به نتیجه مشابهی رسید، هرچند این کار ساده نیست.

- **`bgcolor`** {{deprecated_inline}}
  - رنگ پس‌زمینه هر سلول ستون را تعیین می‌کند. مقدار آن یک رنگ HTML است: یا یک [کد RGB هگزادسیمال ۶ رقمی](/en-US/docs/Web/CSS/Reference/Values/hex-color) که با `#` شروع می‌شود، یا یک [کلیدواژه رنگ](/en-US/docs/Web/CSS/Reference/Values/named-color). سایر مقادیر CSS {{cssxref("&lt;color&gt;")}} پشتیبانی نمی‌شوند. به جای آن از ویژگی CSS {{cssxref("background-color")}} استفاده کنید، زیرا این ویژگی منسوخ شده است.

- `char` — منسوخ
  - : هیچ کاری انجام نمی‌دهد. در اصل برای مشخص کردن ترازبندی محتوای سلول‌ها نسبت به یک کاراکتر خاص در هر ستون طراحی شده بود. معمولاً برای تراز کردن اعداد یا مقادیر پولی از نقطه (`.`) استفاده می‌شد. اگر [`align`](#align) روی `char` تنظیم نشده باشد، این ویژگی نادیده گرفته می‌شود؛ با این حال همچنان مقدار [`char`](/en-US/docs/Web/HTML/Reference/Elements/colgroup#char) مشخص‌شده روی عنصر والد `<colgroup>` را override می‌کند.

- `charoff` — منسوخ
  - : هیچ کاری انجام نمی‌دهد. در اصل برای تعیین تعداد کاراکترهای جابجایی محتوای سلول‌های ستون نسبت به کاراکتر ترازبندی مشخص‌شده در ویژگی [`char`](#char) در نظر گرفته شده بود.

- `valign` — منسوخ
  - : تراز عمودی سلول‌های هر ستون را مشخص می‌کند. مقادیر شمارشی (enumerated) ممکن عبارتند از `baseline`، `bottom`، `middle` و `top`. توجه داشته باشید که این ویژگی، [`valign`](/en-US/docs/Web/HTML/Reference/Elements/colgroup#valign) مشخص‌شده روی عنصر والد `<colgroup>` را override می‌کند. به‌جای این ویژگی منسوخ، از خاصیت CSS `vertical-align` روی عناصر `<td>` و `<th>` استفاده کنید.

    > [!NOTE]
    > تنظیم `vertical-align` روی عنصر `<col>` اثری ندارد، زیرا `<col>` هیچ فرزندی ندارد و بنابراین هیچ عنصری از آن ارث نمی‌برد.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده نمی‌کند، از سلکتور CSS `td:nth-of-type(an+b)` استفاده کنید. مقدار `a` را صفر و `b` را موقعیت ستون در جدول قرار دهید، مثلاً `td:nth-of-type(2) { vertical-align: middle; }` برای تراز عمودی وسط سلول‌های ستون دوم.
    >
    > اگر جدول از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) استفاده می‌کند، می‌توان با ترکیب سلکتورهای ویژگی CSS مناسب مانند `[colspan=n]` به این اثر رسید، هرچند این کار ساده نیست.

- `width` — منسوخ
  - : عرض پیش‌فرض هر ستون را مشخص می‌کند. علاوه بر مقادیر استاندارد پیکسلی و درصدی، این ویژگی می‌تواند شکل خاص `0*` را بگیرد که یعنی عرض هر ستون پوشش‌داده‌شده باید حداقل عرض لازم برای نگه‌داشتن محتوای ستون باشد. عرض‌های نسبی مانند `5*` نیز قابل استفاده هستند. توجه داشته باشید که این ویژگی، [`width`](/en-US/docs/Web/HTML/Reference/Elements/colgroup#width) مشخص‌شده روی عنصر والد `<colgroup>` را override می‌کند. به‌جای این ویژگی منسوخ، از خاصیت CSS `width` استفاده کنید.

- عنصر `<col>` درون یک عنصر {{HTMLElement("colgroup")}} استفاده می‌شود که خودش attribute ای به نام `span` ندارد.
- عناصر `<col>` ستون‌ها را به صورت ساختاری گروه‌بندی نمی‌کنند. این وظیفهٔ عنصر {{HTMLElement("colgroup")}} است.
- فقط تعداد محدودی از ویژگی‌های CSS بر `<col>` تأثیر می‌گذارند:
  - {{cssxref("background")}}: ویژگی‌های مختلف `background` پس‌زمینهٔ سلول‌های داخل ستون را تنظیم می‌کنند. رنگ پس‌زمینهٔ ستون روی لایه‌ای بالاتر از جدول و گروه‌های ستون (`<colgroup>`) اما پایین‌تر از پس‌زمینهٔ گروه‌های ردیف ({{htmlelement("thead")}}، {{htmlelement("tbody")}} و {{htmlelement("tfoot")}})، ردیف‌ها ({{htmlelement("tr")}}) و سلول‌های تکی ({{htmlelement("th")}} و {{htmlelement("td")}}) قرار می‌گیرد. بنابراین پس‌زمینهٔ ستون‌های جدول تنها زمانی دیده می‌شود که تمام لایه‌های بالای آن پس‌زمینه‌ای شفاف داشته باشند.
  - {{cssxref("border")}}: ویژگی‌های مختلف `border` اعمال می‌شوند، اما فقط اگر `<table>` دارای {{cssxref("border-collapse", "border-collapse: collapse")}} تنظیم شده باشد.
  - {{cssxref("visibility")}}: مقدار `collapse` برای یک ستون باعث می‌شود تمام سلول‌های آن ستون نمایش داده نشوند و سلول‌هایی که به ستون‌های دیگر کشیده شده‌اند بریده شوند. فضای این ستون‌ها حذف می‌شود. با این حال، اندازهٔ سایر ستون‌ها همچنان طوری محاسبه می‌شود که گویی سلول‌های ستون(های) جمع‌شده وجود دارند. سایر مقادیر `visibility` تأثیری ندارند.
  - {{cssxref("width")}}: ویژگی `width` حداقل عرض را برای ستون تعریف می‌کند، مانند اینکه {{cssxref("min-width")}} تنظیم شده باشد.

## مثال

برای مشاهدهٔ یک مثال کامل از جدول که استانداردهای رایج و بهترین روش‌ها را معرفی می‌کند، به {{HTMLElement("table")}} مراجعه کنید.

این مثال یک جدول هشت‌ستونی را نشان می‌دهد که به سه عنصر `<col>` تقسیم شده است.

### HTML

یک عنصر {{HTMLElement("colgroup")}} ساختار یک جدول ساده را فراهم می‌کند و یک گروه ستون ضمنی واحد ایجاد می‌کند. سه عنصر `<col>` درون `<colgroup>` قرار گرفته‌اند که سه ستون قابل‌استایل‌دهی ایجاد می‌کنند. attribute [`span`](#span) تعداد ستون‌های جدول را که هر `<col>` باید پوشش دهد مشخص می‌کند (در صورت حذف، مقدار پیش‌فرض `1` است) و باعث می‌شود ویژگی‌ها بین ستون‌های هر `<col>` به اشتراک گذاشته شوند.

```html
<table>
  <caption>
    Personal weekly activities
  </caption>
  <colgroup>
    <col />
    <col span="5" class="weekdays" />
    <col span="2" class="weekend" />
  </colgroup>
  <thead>
    <tr>
      <th>Period</th>
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
      <th>a.m.</th>
      <td>Clean room</td>
      <td>Football training</td>
      <td>Dance Course</td>
      <td>History Class</td>
      <td>Buy drinks</td>
      <td>Study hour</td>
      <td>Free time</td>
    </tr>
    <tr>
      <th>p.m.</th>
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

ما از CSS به جای attributeهای منسوخ HTML برای تعیین رنگ پس‌زمینهٔ ستون‌ها و تراز کردن محتوای سلول‌ها استفاده می‌کنیم:

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

## ویژگی‌ها

| ویژگی | توضیح |
| --- | --- |
| [دسته‌های محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | هیچ‌کدام. |
| محتوای مجاز | هیچ؛ این یک **void element** است. |
| حذف تگ | باید تگ شروع داشته باشد و نباید تگ پایانی داشته باشد. |
| والدین مجاز | فقط {{HTMLElement("colgroup")}}؛ البته می‌تواند به‌صورت ضمنی تعریف شود، چون تگ شروع آن اجباری نیست. والد باید ویژگی [`span`](/en-US/docs/Web/HTML/Reference/Elements/colgroup#span) نداشته باشد. |
| نقش ARIA ضمنی | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role). |
| نقش‌های ARIA مجاز | هیچ `role`ای مجاز نیست. |
| رابط DOM | {{domxref("HTMLTableColElement")}} |

## جستارهای وابسته

- {{HTMLElement("caption")}}، {{HTMLElement("colgroup")}}، {{HTMLElement("table")}}، {{HTMLElement("tbody")}}، {{HTMLElement("td")}}، {{HTMLElement("tfoot")}}، {{HTMLElement("th")}}، {{HTMLElement("thead")}}، {{HTMLElement("tr")}} — سایر عناصر مرتبط با جدول
- {{cssxref("background-color")}} — برای تنظیم رنگ پس‌زمینه سلول‌های هر ستون
- {{cssxref("border")}} — برای کنترل حاشیه سلول‌های ستون
- {{cssxref("text-align")}} — برای تراز افقی محتوای سلول‌های هر ستون
- {{cssxref("vertical-align")}} — برای تراز عمودی محتوای سلول‌های هر ستون
- {{cssxref("visibility")}} — برای مخفی‌کردن سلول‌های یک ستون
- {{cssxref("width")}} — برای تنظیم عرض پیش‌فرض هر ستون
- {{cssxref(":nth-of-type")}}، {{cssxref(":first-of-type")}}، {{cssxref(":last-of-type")}} — شبه‌کلاس‌های CSS برای انتخاب سلول‌های ستون موردنظر