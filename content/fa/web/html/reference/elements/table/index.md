---
title: "<table> HTML table element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/table"
translated_by: "n8n + AI"
---

# `<table>`: عنصر جدول HTML

عنصر **`<table>`** در HTML برای نمایش داده‌های جدولی به کار می‌رود. این داده‌ها در یک جدول دو بعدی شامل سطرها و ستون‌هایی از سلول‌ها قرار می‌گیرند.

```html interactive-example
<table>
  <caption>
    Front-end web developer course 2021
  </caption>
  <thead>
    <tr>
      <th scope="col">Person</th>
      <th scope="col">Most interest in</th>
      <th scope="col">Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Chris</th>
      <td>HTML tables</td>
      <td>22</td>
    </tr>
    <tr>
      <th scope="row">Dennis</th>
      <td>Web accessibility</td>
      <td>45</td>
    </tr>
    <tr>
      <th scope="row">Sarah</th>
      <td>JavaScript frameworks</td>
      <td>29</td>
    </tr>
    <tr>
      <th scope="row">Karen</th>
      <td>Web performance</td>
      <td>36</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row" colspan="2">Average age</th>
      <td>33</td>
    </tr>
  </tfoot>
</table>
```

```css interactive-example
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
  font-weight: bold;
}

thead,
tfoot {
  background-color: rgb(228 240 245);
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

td:last-of-type {
  text-align: center;
}

tbody > tr:nth-of-type(even) {
  background-color: rgb(237 238 242);
}

tfoot th {
  text-align: right;
}

tfoot td {
  font-weight: bold;
}
```

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

### ویژگی‌های منسوخ شده

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع در هنگام به‌روزرسانی کدهای قدیمی و آشنایی تاریخی مستند شده‌اند.

- `align` {{deprecated_inline}}
  - : تراز افقی جدول را درون عنصر والد مشخص می‌کند. مقادیر ممکن {{Glossary("enumerated")}} عبارتند از `left`، `center` و `right`. به جای این ویژگی منسوخ شده، از خصوصیات CSS {{cssxref("margin-inline-start")}} و {{cssxref("margin-inline-end")}} استفاده کنید.

- `bgcolor` {{deprecated_inline}}
  - : رنگ پس‌زمینه جدول را تعریف می‌کند. مقدار آن یک رنگ HTML است؛ یا یک کد RGB هگزادسیمال ۶ رقمی ([6-digit hexadecimal RGB code](/en-US/docs/Web/CSS/Reference/Values/hex-color)) که با `#` شروع می‌شود، یا یک کلیدواژه رنگ ([color keyword](/en-US/docs/Web/CSS/Reference/Values/named-color)). سایر مقادیر CSS {{cssxref("&lt;color&gt;")}} پشتیبانی نمی‌شوند. به جای این ویژگی منسوخ شده، از خصوصیت CSS {{cssxref("background-color")}} استفاده کنید.

- `border` {{deprecated_inline}}
  - : اندازه قاب دور جدول را به صورت یک عدد صحیح نامنفی (بر حسب پیکسل) تعریف می‌کند. اگر مقدار `0` باشد، ویژگی [`frame`](#frame) روی `void` تنظیم می‌شود. به جای این ویژگی منسوخ شده، از خصوصیت CSS {{cssxref("border")}} استفاده کنید.

- `cellpadding` {{deprecated_inline}}
  - : فاصله بین محتوای سلول و حاشیه آن را تعریف می‌کند. این ویژگی منسوخ شده است؛ به جای آن، خصوصیت CSS {{cssxref("padding")}} را روی عناصر {{HTMLElement("th")}} و {{HTMLElement("td")}} اعمال کنید.

- `cellspacing` {{deprecated_inline}}
  - : اندازه فاصله بین دو سلول را تعریف می‌کند. این ویژگی منسوخ شده است؛ به جای آن، خصوصیت CSS {{cssxref("border-spacing")}} را روی عنصر `<table>` تنظیم کنید. توجه داشته باشید که اگر خصوصیت CSS {{cssxref("border-collapse")}} عنصر `<table>` روی `collapse` تنظیم شده باشد، این ویژگی تأثیری ندارد.

- `frame` (منسوخ شده)
  - : مشخص می‌کند که کدام سمت از قابِ دور جدول نمایش داده شود. مقدارهای ممکن `enumerated` عبارتند از: `void`، `above`، `below`، `hsides`، `vsides`، `lhs`، `rhs`، `box` و `border`. به جای آن از property های CSS یعنی `border-style` و `border-width` استفاده کنید؛ زیرا این attribute منسوخ شده است.

- `rules` (منسوخ شده)
  - : مشخص می‌کند که خطوط جدایی‌انداز (borders) در کجای جدول نمایش داده شوند. مقدارهای ممکن `enumerated` عبارتند از: `none` (مقدار پیش‌فرض)، `groups` (برای element های `<thead>`، `<tbody>` و `<tfoot>`)، `rows` (خطوط افقی)، `cols` (خطوط عمودی) و `all` (border دور تمام سلول‌ها). به جای آن از property کلیدی `border` در CSS روی element های مرتبط با جدول و خودِ `<table>` استفاده کنید؛ زیرا این attribute منسوخ شده است.

- `summary` (منسوخ شده)
  - : متنی جایگزین را تعریف می‌کند که محتوای جدول را خلاصه می‌کند. به جای آن از element `<caption>` استفاده کنید؛ زیرا این attribute منسوخ شده است.

- `width` (منسوخ شده)
  - : عرض جدول را مشخص می‌کند. به جای آن از property کلیدی `width` در CSS استفاده کنید؛ زیرا این attribute منسوخ شده است.

    > [!NOTE]
    > اگرچه هیچ مشخصات HTML ای شامل `height` به عنوان attribute برای `<table>` نیست، برخی browser ها از تفسیر غیراستانداردِ `height` پشتیبانی می‌کنند. مقدار بدون واحد، حداقل ارتفاع مطلق را بر حسب پیکسل تنظیم می‌کند. اگر مقدار به صورت درصد داده شود، حداقل ارتفاع جدول نسبت به ارتفاع ظرف والد (parent container) خواهد بود. به جای آن از property کلیدی `min-height` در CSS استفاده کنید؛ زیرا این attribute منسوخ شده است.

## چیدمان بصری محتویات جدول

Element های زیر بخشی از ساختار جدول هستند:

- {{HTMLElement("caption")}}
- {{HTMLElement("thead")}}
- {{HTMLElement("colgroup")}}
- {{HTMLElement("col")}}
- {{HTMLElement("th")}}
- {{HTMLElement("tbody")}}
- {{HTMLElement("tr")}}
- {{HTMLElement("td")}}
- {{HTMLElement("tfoot")}}

جعبه‌ی `<table>` یک **table formatting context** ایجاد می‌کند. element های داخل `<table>` جعبه‌های مستطیلی تولید می‌کنند. هر جعبه با توجه به قوانین زیر، تعدادی از سلول‌های جدول را اشغال می‌کند:

1. جعبه‌های ردیف (row boxes) جدول را به ترتیب کد منبع از بالا به پایین پر می‌کنند. هر جعبه‌ی ردیف، یک ردیف از سلول‌ها را اشغال می‌کند.
2. جعبه‌ی گروه‌ردیف (row group box) یک یا چند جعبه‌ی ردیف را اشغال می‌کند.
3. جعبه‌های ستون (column boxes) به ترتیب کد منبع کنار یکدیگر قرار می‌گیرند. بسته به مقدار attribute کلیدی [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir)، ستون‌ها در جهت چپ‌به‌راست یا راست‌به‌چپ چیده می‌شوند. یک جعبه‌ی ستون، یک یا چند ستون از سلول‌های جدول را اشغال می‌کند.
4. جعبه‌ی گروه‌ستون (column group box) یک یا چند جعبه‌ی ستون را اشغال می‌کند.
5. جعبه‌ی سلول ممکن است روی چند ردیف و چند ستون کشیده شود (span). عامل‌های کاربر (user agents) سلول‌ها را طوری کوتاه می‌کنند که در تعداد ردیف‌ها و ستون‌های موجود جا شوند.

سلول‌های جدول padding دارند؛ اما جعبه‌هایی که جدول را می‌سازند margin ندارند.

### لایه‌های جدول و شفافیت

برای اهداف استایل‌دهی، می‌توان element های جدول را به صورت شش لایه‌ی روی‌هم‌قرارگرفته در نظر گرفت:

![Table element layers](table_element_layers.png)

پس‌زمینه‌ای که روی یک element در یک لایه تنظیم شده است، فقط زمانی دیده می‌شود که لایه‌های بالای آن پس‌زمینه‌ی شفاف داشته باشند. اگر سلولی وجود نداشته باشد، به گونه‌ای رندر می‌شود که گویی یک جعبه‌ی ناشناسِ `table-cell` آن مکان را اشغال کرده است.

## دسترس‌پذیری

### Caption ها

با قرار دادن یک element `<caption>` که مقدار آن به‌روشنی و به‌طور خلاصه هدف جدول را توصیف می‌کند، به افراد کمک می‌کنید تا تصمیم بگیرند که آیا لازم است بقیه‌ی محتوای جدول را بررسی کنند یا از آن رد شوند.

این کار به افرادی که با کمک فناوری کمکی مانند screen reader حرکت می‌کنند، افرادی با شرایط کم‌بینایی، و افرادی با نگرانی‌های شناختی کمک می‌کند.

- [MDN Adding a caption to your table with \<caption>](/en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility#adding_a_caption_to_your_table_with_caption)
- [Caption & Summary • Tables • W3C WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/tables/caption-summary/)

### محدوده‌بندی سطرها و ستون‌ها

attributeی `scope` روی سلول‌های سربرگ (elementهای `<th>`) در زمینه‌های ساده اضافی است، زیرا scope به‌صورت خودکار استنتاج می‌شود. با این حال، برخی فناوری‌های کمکی ممکن است در استنتاج درست ناتوان باشند، بنابراین مشخص‌کردن scope برای سربرگ‌ها می‌تواند تجربه کاربری را بهبود دهد. در جدول‌های پیچیده، می‌توان `scope` را مشخص کرد تا اطلاعات لازم درباره سلول‌های مرتبط با یک سربرگ فراهم شود.

- [MDN table accessibility guide](/en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility)
- [Tables with two headers • Tables • W3C WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/tables/two-headers/)
- [Tables with irregular headers • Tables • W3C WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/tables/irregular/)
- [H63: Using the scope attribute to associate header cells and data cells in data tables | W3C Techniques for WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/H63.html)

### جدول‌های پیچیده

فناوری‌های کمکی مانند صفحه‌خوان‌ها ممکن است در تجزیه جدول‌هایی که به‌قدری پیچیده‌اند که سلول‌های سربرگ را نمی‌توان به‌صورت کاملاً افقی یا عمودی مرتبط کرد، دچار مشکل شوند. این معمولاً با وجود attributeهای `colspan` و `rowspan` مشخص می‌شود.

در حالت ایده‌آل، به راه‌های جایگزین برای نمایش محتوای جدول فکر کنید؛ مثلاً تقسیم آن به مجموعه‌ای از جدول‌های کوچک‌تر و مرتبط که نیازی به استفاده از attributeهای `colspan` و `rowspan` نداشته باشند. این کار علاوه بر کمک به افرادی که از فناوری کمکی استفاده می‌کنند تا محتوای جدول را بفهمند، برای افرادی که مشکلات شناختی دارند و ممکن است در درک ارتباطاتی که چیدمان جدول توصیف می‌کند دچار مشکل شوند نیز مفید است.

اگر جدول قابل تقسیم نیست، از ترکیب attributeهای `id` و `headers` استفاده کنید تا هر سلول جدول را به‌صورت برنامه‌نویسی با سربرگ(های) مرتبط‌اش مرتبط کنید.

- [MDN table accessibility guide](/en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility)
- [Tables with multi-level headers • Tables • W3C WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/tables/multi-level/)
- [H43: Using id and headers attributes to associate data cells with header cells in data tables | Techniques for W3C WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/H43.html)

## مثال‌ها

مثال‌های زیر شامل جدول‌هایی با پیچیدگی فزاینده هستند. برای اطلاعات مربوط به استایل‌دهی جدول، از جمله تکنیک‌های رایج و کاربردی، به راهنمای مبتدی [Styling tables](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables) مراجعه کنید.

از آنجا که ساختار یک `<table>` شامل استفاده از چندین element مرتبط با جدول و attributeهای گوناگون است، مثال‌های زیر توضیحی ساده‌شده ارائه می‌دهند که اصول پایه و استانداردهای رایج را پوشش می‌دهد. اطلاعات بیشتر و جزئی‌تر را می‌توانید در صفحات مرتبط که پیوند داده شده‌اند بیابید.

این مثال‌های جدول نشان می‌دهند که چگونه یک جدول دسترس‌پذیر (accessible) با ساختار HTML و استایل‌دهی با [CSS](/en-US/docs/Web/CSS) ایجاد کنید.

به دلیل ساختار خاص جداول HTML، نشانه‌گذاری (markup) آن‌ها می‌تواند به سرعت حجیم شود. به همین دلیل، مهم است که هدف و ظاهر نهایی جدول را به وضوح مشخص کنید تا ساختار مناسبی ایجاد شود. یک ساختار منطقی که با نشانه‌گذاری معنایی (semantic markup) توسعه یافته باشد، نه تنها استایل‌دهی آسان‌تری دارد، بلکه جداول مفید و قابل دسترسی ایجاد می‌کند که برای همه، از جمله موتورهای جستجو و کاربران فناوری‌های کمکی، قابل درک و پیمایش باشد.

مثال اول ساده است و مثال‌های بعدی پیچیده‌تر می‌شوند. ابتدا یک ساختار جدول HTML بسیار ساده ایجاد می‌کنیم. دو مثال اول شامل گروه‌بندی بخش‌های جدول مانند سر (head)، بدنه (body) یا پا (foot) نیستند، و هیچ سلول کشیده‌شده (cell spanning) یا رابطه‌ای صریح بین سلول‌ها ندارند. حتی عنوان (caption) هم ارائه نشده است. با پیشرفت مثال‌ها، آن‌ها را تدریجاً بهبود می‌دهیم تا تمام ویژگی‌هایی که یک جدول داده‌های پیچیده باید داشته باشد، شامل شوند.

### جدول پایه

این مثال شامل یک جدول **بسیار** ساده با سه ردیف و دو ستون است. برای نشان دادن استایل‌های پیش‌فرض مرورگر، در این مثال از CSS استفاده نشده است.

#### HTML

ردیف‌های جدول با عناصر `<tr>` و ستون‌ها با سلول‌های سرستون و داده درون آن‌ها تعریف می‌شوند. ردیف اول شامل سلول‌های سرستون (عناصر `<th>`) است که به عنوان سرستون ستون‌ها برای سلول‌های داده (عناصر `<td>`) عمل می‌کنند. هر عنصر (`<th>` یا `<td>`) در هر ردیف در ستون مربوط به خود قرار دارد – یعنی اولین عنصر یک ردیف در ستون اول و دومین عنصر آن ردیف در ستون دوم است.

```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Maria Sanchez</td>
    <td>28</td>
  </tr>
  <tr>
    <td>Michael Johnson</td>
    <td>34</td>
  </tr>
</table>
```

#### نتیجه

هیچ [CSS](/en-US/docs/Web/CSS) یا [شیوه‌نامه نویسنده (user stylesheet)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#author_stylesheets) سفارشی روی این جدول اعمال نشده است. استایل‌دهی صرفاً ناشی از [شیوه‌نامه پیش‌فرض مرورگر (user-agent stylesheet)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#user-agent_stylesheets) است.

### جدول گسترش‌یافته با سلول‌های سرستون

این مثال جدول ساده را گسترش می‌دهد، محتوا را افزایش می‌دهد و استایل‌های CSS پایه اضافه می‌کند.

#### HTML

جدول اکنون شامل چهار ردیف (عنصر `<tr>`) است که هر کدام چهار ستون دارند. ردیف اول یک ردیف از سلول‌های سرستون است (ردیف اول فقط شامل عناصر `<th>` است). ردیف‌های بعدی شامل یک ستون سرستون (عناصر `<th>` به عنوان اولین فرزند هر ردیف) و سه ستون داده (عناصر `<td>`) هستند. از آنجایی که از عناصر بخش‌بندی جدول استفاده نشده، مرورگر به طور خودکار ساختار گروه‌بندی محتوا را تعریف می‌کند؛ یعنی همه ردیف‌ها درون بدنه جدول یک عنصر `<tbody>` ضمنی قرار می‌گیرند.

```html
<table>
  <tr>
    <th>Name</th>
    <th>ID</th>
    <th>Member Since</th>
    <th>Balance</th>
  </tr>
  <tr>
    <th>Margaret Nguyen</th>
    <td>427311</td>
    <td><time datetime="2010-06-03">June 3, 2010</time></td>
    <td>0.00</td>
  </tr>
  <tr>
    <th>Edvard Galinski</th>
    <td>533175</td>
    <td><time datetime="2011-01-13">January 13, 2011</time></td>
    <td>37.00</td>
  </tr>
  <tr>
    <th>Hoshi Nakamura</th>
    <td>601942</td>
    <td><time datetime="2012-07-23">July 23, 2012</time></td>
    <td>15.00</td>
  </tr>
</table>
```

#### CSS

با استفاده از CSS، استایل‌های پایه را برای ایجاد خطوط دور اجزای جدول اعمال می‌کنیم تا ساختار داده واضح‌تر شود. CSS یک حاشیه (border) توپر دور `<table>` و دور هر یک از سلول‌های جدول، از جمله سلول‌های مشخص شده با عناصر `<th>` و `<td>` اضافه می‌کند و هر سلول سرستون و داده را مشخص می‌کند.

```css
table {
  border: 2px solid rgb(140 140 140);
}

th,
td {
  border: 1px solid rgb(160 160 160);
}
```

### مشخص کردن ارتباط سلول‌های جدول

قبل از اینکه سراغ ساختارهای پیشرفته‌تر برویم، بهتر است با تعریف رابطه بین سلول‌های header (عنوان) و داده (سلول‌های `<th>` و `<td>`) دسترسی‌پذیری (accessibility) جدول را بهبود بدهیم.

#### HTML

این کار با اضافه کردن ویژگی [`scope`](/en-US/docs/Web/HTML/Reference/Elements/th#scope) به عناصر `<th>` و مقداردهی آن با `col` (ستون) یا `row` (ردیف) انجام می‌شود.

```html
<table>
  <tr>
    <th scope="col">Name</th>
    <th scope="col">ID</th>
    <th scope="col">Member Since</th>
    <th scope="col">Balance</th>
  </tr>
  <tr>
    <th scope="row">Margaret Nguyen</th>
    <td>427311</td>
    <td><time datetime="2010-06-03">June 3, 2010</time></td>
    <td>0.00</td>
  </tr>
  <tr>
    <th scope="row">Edvard Galinski</th>
    <td>533175</td>
    <td><time datetime="2011-01-13">January 13, 2011</time></td>
    <td>37.00</td>
  </tr>
  <tr>
    <th scope="row">Hoshi Nakamura</th>
    <td>601942</td>
    <td><time datetime="2012-07-23">July 23, 2012</time></td>
    <td>15.00</td>
  </tr>
</table>
```

CSS و نتیجه بصری تغییری نمی‌کند – این تغییر فقط اطلاعات زمینه‌ای ارزشمندی را برای فناوری‌های کمکی مثل screen reader فراهم می‌کند تا بتوانند تشخیص دهند headerها به کدام سلول‌ها مربوط می‌شوند.

> [!NOTE]
> اگر ساختار جدول پیچیده‌تر باشد، استفاده از ویژگی [`headers`](/en-US/docs/Web/HTML/Reference/Elements/th#headers) روی عناصر `<th>` و `<td>` می‌تواند دسترسی‌پذیری را بیشتر بهبود دهد و به فناوری‌های کمکی در شناسایی ارتباط بین سلول‌ها کمک کند. برای اطلاعات بیشتر به بخش [Complicated tables](#complicated_tables) مراجعه کنید.

### مشخص کردن صریح بخش‌های گروه‌بندی جدول

علاوه بر بهبود دسترسی‌پذیری با [تعیین ارتباط سلول‌ها](#مشخص-کردن-ارتباط-سلول-های-جدول)، می‌توان معناشناسی (semantics) جدول را با معرفی گروه‌های بخش (section groups) نیز بهبود بخشید.

#### HTML

از آنجا که اولین ردیف (عنصر `<tr>`) فقط شامل سلول‌های header ستون است و header بقیه محتوای جدول را تشکیل می‌دهد، می‌توان آن را درون عنصر `<thead>` قرار داد تا به‌طور صریح این ردیف به عنوان بخش head جدول مشخص شود. علاوه بر این، کاری که مرورگر به‌طور خودکار انجام می‌دهد را می‌توان به‌صورت صریح هم تعریف کرد – بخش body جدول که داده‌های اصلی را در خود دارد، با قرار دادن ردیف‌های مربوطه درون عنصر `<tbody>` مشخص می‌شود. استفاده صریح از `<tbody>` به مرورگر کمک می‌کند ساختار مورد نظر جدول را ایجاد کند و از نتایج ناخواسته جلوگیری شود.

```html
<table>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">ID</th>
      <th scope="col">Member Since</th>
      <th scope="col">Balance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Margaret Nguyen</th>
      <td>427311</td>
      <td><time datetime="2010-06-03">June 3, 2010</time></td>
      <td>0.00</td>
    </tr>
    <tr>
      <th scope="row">Edvard Galinski</th>
      <td>533175</td>
      <td><time datetime="2011-01-13">January 13, 2011</time></td>
      <td>37.00</td>
    </tr>
    <tr>
      <th scope="row">Hoshi Nakamura</th>
      <td>601942</td>
      <td><time datetime="2012-07-23">July 23, 2012</time></td>
      <td>15.00</td>
    </tr>
  </tbody>
</table>
```

باز هم CSS و نتیجه بصری تغییری نمی‌کند – مشخص کردن این گروه‌های بخش جدول، اطلاعات زمینه‌ای ارزشمندی را برای فناوری‌های کمکی (از جمله screen readerها و موتورهای جستجو) و همچنین برای استایل‌دهی در CSS فراهم می‌کند که در مثال بعدی نشان داده خواهد شد.

### گسترش ستون‌ها و ردیف‌ها (Column and row spanning)

در این مثال، جدول را با اضافه کردن یک ستون و معرفی یک بخش head چندردیفی گسترش می‌دهیم.

#### HTML

بر اساس جدولی که تا اینجا ساخته شده، یک ستون تازه برای «تاریخ پایان عضویت» در هر ردیف از بدنه (body) با استفاده از عنصر `<td>` اضافه می‌شود. همچنین یک ردیف اضافی (عنصر `<tr>`) در بخش سربرگ (عنصر `<thead>`) قرار می‌گیرد تا سربرگ «Membership Dates» به‌عنوان عنوان ستون‌های «Joined» و «Canceled» معرفی شود.

برای ایجاد ردیف دوم سربرگ، ویژگی‌های [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/th#colspan) و [`rowspan`](/en-US/docs/Web/HTML/Reference/Elements/th#rowspan) به عناصر `<th>` اضافه می‌شوند تا سلول‌های سربرگ در ستون‌ها و ردیف‌های درست قرار بگیرند.

```html
<table>
  <thead>
    <tr>
      <th scope="col" rowspan="2">Name</th>
      <th scope="col" rowspan="2">ID</th>
      <th scope="col" colspan="2">Membership Dates</th>
      <th scope="col" rowspan="2">Balance</th>
    </tr>
    <tr>
      <th scope="col">Joined</th>
      <th scope="col">Canceled</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Margaret Nguyen</th>
      <td>427311</td>
      <td><time datetime="2010-06-03">June 3, 2010</time></td>
      <td>n/a</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th scope="row">Edvard Galinski</th>
      <td>533175</td>
      <td><time datetime="2011-01-13">January 13, 2011</time></td>
      <td><time datetime="2017-04-08">April 8, 2017</time></td>
      <td>37.00</td>
    </tr>
    <tr>
      <th scope="row">Hoshi Nakamura</th>
      <td>601942</td>
      <td><time datetime="2012-07-23">July 23, 2012</time></td>
      <td>n/a</td>
      <td>15.00</td>
    </tr>
  </tbody>
</table>
```

```css hidden
table {
  border: 2px solid rgb(140 140 140);
}

th,
td {
  border: 1px solid rgb(160 160 160);
}
```

#### نتیجه

بخش سربرگ حالا دو ردیف دارد؛ ردیف اول شامل سربرگ‌های (عناصر `<th>`) «Name»، «ID»، «Membership Dates» و «Balance» است، و سربرگ «Membership Dates» دارای دو زیرسربرگ در ردیف دوم: «Joined» و «Canceled». این کار با این روش انجام می‌شود:

- سلول‌های سربرگ «Name»، «ID» و «Balance» در ردیف اول با استفاده از ویژگی [`rowspan`](/en-US/docs/Web/HTML/Reference/Elements/th#rowspan) هر دو ردیف سربرگ جدول را می‌پوشانند و به همین دلیل هر کدام دو ردیف ارتفاع می‌گیرند.
- سلول سربرگ «Membership Dates» در ردیف اول با استفاده از ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/th#colspan) دو ستون را می‌پوشاند و به همین دلیل عرض آن دو ستون است.
- ردیف دوم فقط دو سلول سربرگ «Joined» و «Canceled» را دارد، زیرا سه ستون دیگر با سلول‌های ردیف اول که دو ردیف را می‌پوشانند ادغام شده‌اند. این دو سلول سربرگ دقیقاً زیر سربرگ «Membership Dates» قرار می‌گیرند.

### عنوان جدول و جمع‌بندی ستون

ارائه خلاصه‌ای از محتوای جدول یک روش معمول و توصیه‌شده است که به کاربران امکان می‌دهد به‌سرعت ارتباط جدول با موضوع موردنظر را تشخیص دهند. علاوه بر این، ستون «Balance» با نمایش مجموع موجودی اعضای مختلف جمع‌بندی می‌شود.

#### HTML

خلاصه جدول با استفاده از یک [caption](#captions) (عنصر `<caption>`) به‌عنوان اولین فرزند `<table>` اضافه می‌شود. این caption نام دسترس‌پذیر (accessible name) یا توضیح دسترس‌پذیر (accessible description) جدول را فراهم می‌کند.

در پایان، یک بخش پابرگی جدول (عنصر `<tfoot>`) زیر بخش بدنه اضافه شده است و در آن یک ردیف وجود دارد که ستون «Balance» را با نمایش مجموع جمع‌بندی می‌کند. عناصر و ویژگی‌هایی که قبلاً معرفی شدند در اینجا نیز به کار رفته‌اند.

```html
<table>
  <caption>
    Status of the club members 2021
  </caption>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">ID</th>
      <th scope="col">Joined</th>
      <th scope="col">Canceled</th>
      <th scope="col">Balance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Margaret Nguyen</th>
      <td>427311</td>
      <td><time datetime="2010-06-03">June 3, 2010</time></td>
      <td>n/a</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th scope="row">Edvard Galinski</th>
      <td>533175</td>
      <td><time datetime="2011-01-13">January 13, 2011</time></td>
      <td><time datetime="2017-04-08">April 8, 2017</time></td>
      <td>37.00</td>
    </tr>
    <tr>
      <th scope="row">Hoshi Nakamura</th>
      <td>601942</td>
      <td><time datetime="2012-07-23">July 23, 2012</time></td>
      <td>n/a</td>
      <td>15.00</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row" colspan="4">Total balance</th>
      <td>52.00</td>
    </tr>
  </tfoot>
</table>
```

```html
<table>
  <caption>
    Status of the club members 2021
  </caption>
  <thead>
    <tr>
      <th scope="col" rowspan="2">Name</th>
      <th scope="col" rowspan="2">ID</th>
      <th scope="col" colspan="2">Membership Dates</th>
      <th scope="col" rowspan="2">Balance</th>
    </tr>
    <tr>
      <th scope="col">Joined</th>
      <th scope="col">Canceled</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Margaret Nguyen</th>
      <td>427311</td>
      <td><time datetime="2010-06-03">June 3, 2010</time></td>
      <td>n/a</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th scope="row">Edvard Galinski</th>
      <td>533175</td>
      <td><time datetime="2011-01-13">January 13, 2011</time></td>
      <td><time datetime="2017-04-08">April 8, 2017</time></td>
      <td>37.00</td>
    </tr>
    <tr>
      <th scope="row">Hoshi Nakamura</th>
      <td>601942</td>
      <td><time datetime="2012-07-23">July 23, 2012</time></td>
      <td>n/a</td>
      <td>15.00</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row" colspan="4">Total balance</th>
      <td>52.00</td>
    </tr>
  </tfoot>
</table>
```

```css hidden
table {
  border: 2px solid rgb(140 140 140);
}

th,
td {
  border: 1px solid rgb(160 160 160);
}
```

#### نتیجه

### استایل پایه جدول

حالا یک استایل پایه به جدول اعمال می‌کنیم تا فونت را تنظیم کنیم و یک `background-color` به ردیف‌های هدر (header) و فوتر (footer) اضافه کنیم. این بار HTML تغییری نکرده است؛ پس مستقیم به سراغ CSS می‌رویم.

```html hidden
<table>
  <caption>
    Status of the club members 2021
  </caption>
  <thead>
    <tr>
      <th scope="col" rowspan="2">Name</th>
      <th scope="col" rowspan="2">ID</th>
      <th scope="col" colspan="2">Membership Dates</th>
      <th scope="col" rowspan="2">Balance</th>
    </tr>
    <tr>
      <th scope="col">Joined</th>
      <th scope="col">Canceled</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Margaret Nguyen</th>
      <td>427311</td>
      <td><time datetime="2010-06-03">June 3, 2010</time></td>
      <td>n/a</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th scope="row">Edvard Galinski</th>
      <td>533175</td>
      <td><time datetime="2011-01-13">January 13, 2011</time></td>
      <td><time datetime="2017-04-08">April 8, 2017</time></td>
      <td>37.00</td>
    </tr>
    <tr>
      <th scope="row">Hoshi Nakamura</th>
      <td>601942</td>
      <td><time datetime="2012-07-23">July 23, 2012</time></td>
      <td>n/a</td>
      <td>15.00</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row" colspan="4">Total balance</th>
      <td>52.00</td>
    </tr>
  </tfoot>
</table>
```

#### CSS

در اینجا یک ویژگی `font` به عنصر `<table>` اضافه شده تا فونت بهتری از نظر بصری تنظیم شود (بسته به سلیقهٔ شخصی، ممکن است فونت بدون سریف را ناخوشایند بدانید)، اما بخش جالب، استایل دوم است که در آن به المان‌های `<tr>` که در `<thead>` و `<tfoot>` قرار دارند، یک `background-color` آبی روشن اضافه می‌شود. این روش به شما امکان می‌دهد به‌سرعت رنگ پس‌زمینه را به همهٔ سلول‌های بخش‌های مشخص اعمال کنید.

```css
table {
  border: 2px solid rgb(140 140 140);
  font:
    16px "Open Sans",
    "Helvetica",
    "Arial",
    sans-serif;
}

thead > tr,
tfoot > tr {
  background-color: rgb(228 240 245);
}

th,
td {
  border: 1px solid rgb(160 160 160);
}
```

#### نتیجه

### استایل پیشرفته جدول

حالا به‌صورت کامل پیش می‌رویم؛ با استایل‌ها روی ردیف‌های هم در سربرگ و هم در بدنه، شامل رنگ‌های یک‌درمیان ردیف‌ها، سلول‌هایی با رنگ‌های متفاوت بسته به موقعیت در ردیف، و غیره. این بار اول نتیجه را ببینیم.

#### نتیجه

جدول نهایی به این شکل خواهد بود:

باز هم تغییری در HTML داده نشده است. ببینید آماده‌سازی درست ساختار HTML چه تأثیری می‌تواند داشته باشد؟

```html hidden
<table>
  <caption>
    Status of the club members 2021
  </caption>
  <thead>
    <tr>
      <th scope="col" rowspan="2">Name</th>
      <th scope="col" rowspan="2">ID</th>
      <th scope="col" colspan="2">Membership Dates</th>
      <th scope="col" rowspan="2">Balance</th>
    </tr>
    <tr>
      <th scope="col">Joined</th>
      <th scope="col">Canceled</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Margaret Nguyen</th>
      <td>427311</td>
      <td><time datetime="2010-06-03">June 3, 2010</time></td>
      <td>n/a</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th scope="row">Edvard Galinski</th>
      <td>533175</td>
      <td><time datetime="2011-01-13">January 13, 2011</time></td>
      <td><time datetime="2017-04-08">April 8, 2017</time></td>
      <td>37.00</td>
    </tr>
    <tr>
      <th scope="row">Hoshi Nakamura</th>
      <td>601942</td>
      <td><time datetime="2012-07-23">July 23, 2012</time></td>
      <td>n/a</td>
      <td>15.00</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row" colspan="4">Total balance</th>
      <td>52.00</td>
    </tr>
  </tfoot>
</table>
```

#### CSS

این بار CSS خیلی بیشتر درگیر است. پیچیده نیست، اما جزئیات زیادی دارد. بگذارید مرحله‌به‌مرحله بررسی‌اش کنیم.

در اینجا خاصیت‌های `border-collapse` و `border-spacing` اضافه شده‌اند تا فاصله بین سلول‌ها حذف شود و borderهای مجاور به‌جای تبدیل شدن به borderهای دوتایی، در یک border واحد ادغام شوند. علاوه بر این، عنصر `<caption>` با استفاده از خاصیت `caption-side` در پایین جدول قرار گرفته است:

```css
table {
  border-collapse: collapse;
  border-spacing: 0;
  border: 2px solid rgb(140 140 140);
  font:
    16px "Open Sans",
    "Helvetica",
    "Arial",
    sans-serif;
}

caption {
  caption-side: bottom;
  padding: 10px;
  font-weight: bold;
}
```

در مرحله بعد، از خاصیت `padding` برای ایجاد فضا در اطراف محتوای همه سلول‌های جدول استفاده می‌شود. خاصیت `vertical-align` محتوای سلول‌های هدر را در پایین سلول قرار می‌دهد؛ این را می‌توانید در سلول‌های بخش head که دو ردیف را پوشش می‌دهند ببینید:

```css
th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 4px 6px;
}

th {
  vertical-align: bottom;
}
```

قانون CSS بعدی مقدار `background-color` همه عناصر `<tr>` در بخش head جدول (که با `<thead>` مشخص شده) را تعیین می‌کند. سپس border پایینی این بخش به‌صورت خطی به عرض دو پیکسل تنظیم می‌شود. اما توجه کنید که از انتخابگر `:nth-of-type` استفاده می‌کنیم تا خاصیت `border-bottom` را روی ردیف دومِ head اعمال کنیم. چرا؟ چون head از دو ردیف تشکیل شده و بعضی سلول‌ها روی هر دو ردیف کشیده شده‌اند. یعنی در واقع دو ردیف آنجاست؛ اگر استایل را روی ردیف اول اعمال کنیم نتیجه دلخواه را نخواهیم گرفت:

```css
thead > tr {
  background-color: rgb(228 240 245);
}

thead > tr:nth-of-type(2) {
  border-bottom: 2px solid rgb(140 140 140);
}
```

حالا بیایید دو سلول هدر «Joined» و «Canceled» را به ترتیب با رنگ‌های سبز و قرمز استایل دهیم؛ سبز نشان‌دهنده «خوبی» عضویت جدید و قرمز نشان‌دهنده «ناراحتی» لغو عضویت است. در اینجا با استفاده از انتخابگر `:last-of-type` سراغ آخرین ردیف بخش head می‌رویم و به اولین سلول هدر در آن (هدر «Joined») رنگ سبز و به دومین سلول هدر (هدر «Canceled») رنگ قرمز می‌دهیم:

```css
thead > tr:last-of-type > th:nth-of-type(1) {
  background-color: rgb(225 255 225);
}

thead > tr:last-of-type > th:nth-of-type(2) {
  background-color: rgb(255 225 225);
}
```

چون ستون اول هم باید برجسته شود، در اینجا هم چند استایل سفارشی اضافه شده است. این قانون CSS، اولین سلولِ عنوان (`th`) را در هر ردیف از بدنهٔ جدول با استفاده از ویژگی `text-align` به‌چپ تراز می‌کند و با یک `background-color` کمی متفاوت مشخص می‌کند:

```css
tbody > tr > th:first-of-type {
  text-align: left;
  background-color: rgb(225 229 244);
}
```

برای بهبود خوانایی داده‌های جدول، معمولاً رنگ ردیف‌های یک‌درمیان تغییر می‌کند — به این کار «زبرا استرایپینگ» هم گفته می‌شود. بیایید یک `background-color` به هر ردیف زوج اضافه کنیم:

```css
tbody > tr:nth-of-type(even) {
  background-color: rgb(237 238 242);
}
```

چون استاندارد این است که مقادیر ارز در جدول راست‌چین شوند، این کار را هم انجام می‌دهیم. این قانون فقط ویژگی `text-align` را برای آخرین `<td>` در هر ردیف بدنه روی `right` تنظیم می‌کند:

```css
tbody > tr > td:last-of-type {
  text-align: right;
}
```

در نهایت، برای بخش پایانی جدول (`tfoot`) هم استایلی مشابه بخش سربرگ اعمال می‌شود تا آن نیز برجسته شود:

```css
tfoot > tr {
  border-top: 2px dashed rgb(140 140 140);
  background-color: rgb(228 240 245);
}

tfoot th,
tfoot td {
  text-align: right;
  font-weight: bold;
}
```

### نمایش جدول‌های بزرگ در فضاهای کوچک

یک مشکل رایج در جدول‌های وب این است که وقتی محتوای زیادی دارند، در صفحه‌های کوچک به‌طور طبیعی خوب کار نمی‌کنند؛ راه واضحی هم برای اسکرول‌پذیر کردنشان وجود ندارد، به‌خصوص وقتی مارکاپ از یک CMS می‌آید و نمی‌توان آن را تغییر داد تا یک wrapper داشته باشد.

این مثال یک راه‌حل برای نمایش جدول‌ها در فضاهای کوچک ارائه می‌دهد. محتوای HTML را چون خیلی بزرگ است مخفی کرده‌ایم و چیز چشمگیری هم ندارد. در این مثال، بررسی CSS مفیدتر است.

```html
<table>
  <thead>
    <tr>
      <th>۱<sup>۳</sup> برابر است با:</th>
      <th>۲<sup>۳</sup> برابر است با:</th>
      <th>۳<sup>۳</sup> برابر است با:</th>
      <th>۴<sup>۳</sup> برابر است با:</th>
      <th>۵<sup>۳</sup> برابر است با:</th>
      <th>۶<sup>۳</sup> برابر است با:</th>
      <th>۷<sup>۳</sup> برابر است با:</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>ردیف ۱: ۱</td>
      <td>ردیف ۱: ۸</td>
      <td>ردیف ۱: ۲۷</td>
      <td>ردیف ۱: ۶۴</td>
      <td>ردیف ۱: ۱۲۵</td>
      <td>ردیف ۱: ۲۱۶</td>
      <td>ردیف ۱: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۲: ۱</td>
      <td>ردیف ۲: ۸</td>
      <td>ردیف ۲: ۲۷</td>
      <td>ردیف ۲: ۶۴</td>
      <td>ردیف ۲: ۱۲۵</td>
      <td>ردیف ۲: ۲۱۶</td>
      <td>ردیف ۲: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۳: ۱</td>
      <td>ردیف ۳: ۸</td>
      <td>ردیف ۳: ۲۷</td>
      <td>ردیف ۳: ۶۴</td>
      <td>ردیف ۳: ۱۲۵</td>
      <td>ردیف ۳: ۲۱۶</td>
      <td>ردیف ۳: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۴: ۱</td>
      <td>ردیف ۴: ۸</td>
      <td>ردیف ۴: ۲۷</td>
      <td>ردیف ۴: ۶۴</td>
      <td>ردیف ۴: ۱۲۵</td>
      <td>ردیف ۴: ۲۱۶</td>
      <td>ردیف ۴: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۵: ۱</td>
      <td>ردیف ۵: ۸</td>
      <td>ردیف ۵: ۲۷</td>
      <td>ردیف ۵: ۶۴</td>
      <td>ردیف ۵: ۱۲۵</td>
      <td>ردیف ۵: ۲۱۶</td>
      <td>ردیف ۵: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۶: ۱</td>
      <td>ردیف ۶: ۸</td>
      <td>ردیف ۶: ۲۷</td>
      <td>ردیف ۶: ۶۴</td>
      <td>ردیف ۶: ۱۲۵</td>
      <td>ردیف ۶: ۲۱۶</td>
      <td>ردیف ۶: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۷: ۱</td>
      <td>ردیف ۷: ۸</td>
      <td>ردیف ۷: ۲۷</td>
      <td>ردیف ۷: ۶۴</td>
      <td>ردیف ۷: ۱۲۵</td>
      <td>ردیف ۷: ۲۱۶</td>
      <td>ردیف ۷: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۸: ۱</td>
      <td>ردیف ۸: ۸</td>
      <td>ردیف ۸: ۲۷</td>
      <td>ردیف ۸: ۶۴</td>
      <td>ردیف ۸: ۱۲۵</td>
      <td>ردیف ۸: ۲۱۶</td>
      <td>ردیف ۸: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۹: ۱</td>
      <td>ردیف ۹: ۸</td>
      <td>ردیف ۹: ۲۷</td>
      <td>ردیف ۹: ۶۴</td>
      <td>ردیف ۹: ۱۲۵</td>
      <td>ردیف ۹: ۲۱۶</td>
      <td>ردیف ۹: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۰: ۱</td>
      <td>ردیف ۱۰: ۸</td>
      <td>ردیف ۱۰: ۲۷</td>
      <td>ردیف ۱۰: ۶۴</td>
      <td>ردیف ۱۰: ۱۲۵</td>
      <td>ردیف ۱۰: ۲۱۶</td>
      <td>ردیف ۱۰: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۱: ۱</td>
      <td>ردیف ۱۱: ۸</td>
      <td>ردیف ۱۱: ۲۷</td>
      <td>ردیف ۱۱: ۶۴</td>
      <td>ردیف ۱۱: ۱۲۵</td>
      <td>ردیف ۱۱: ۲۱۶</td>
      <td>ردیف ۱۱: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۲: ۱</td>
      <td>ردیف ۱۲: ۸</td>
      <td>ردیف ۱۲: ۲۷</td>
      <td>ردیف ۱۲: ۶۴</td>
      <td>ردیف ۱۲: ۱۲۵</td>
      <td>ردیف ۱۲: ۲۱۶</td>
      <td>ردیف ۱۲: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۳: ۱</td>
      <td>ردیف ۱۳: ۸</td>
      <td>ردیف ۱۳: ۲۷</td>
      <td>ردیف ۱۳: ۶۴</td>
      <td>ردیف ۱۳: ۱۲۵</td>
      <td>ردیف ۱۳: ۲۱۶</td>
      <td>ردیف ۱۳: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۴: ۱</td>
      <td>ردیف ۱۴: ۸</td>
      <td>ردیف ۱۴: ۲۷</td>
      <td>ردیف ۱۴: ۶۴</td>
      <td>ردیف ۱۴: ۱۲۵</td>
      <td>ردیف ۱۴: ۲۱۶</td>
      <td>ردیف ۱۴: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۵: ۱</td>
      <td>ردیف ۱۵: ۸</td>
      <td>ردیف ۱۵: ۲۷</td>
      <td>ردیف ۱۵: ۶۴</td>
      <td>ردیف ۱۵: ۱۲۵</td>
      <td>ردیف ۱۵: ۲۱۶</td>
      <td>ردیف ۱۵: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۶: ۱</td>
      <td>ردیف ۱۶: ۸</td>
      <td>ردیف ۱۶: ۲۷</td>
      <td>ردیف ۱۶: ۶۴</td>
      <td>ردیف ۱۶: ۱۲۵</td>
      <td>ردیف ۱۶: ۲۱۶</td>
      <td>ردیف ۱۶: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۷: ۱</td>
      <td>ردیف ۱۷: ۸</td>
      <td>ردیف ۱۷: ۲۷</td>
      <td>ردیف ۱۷: ۶۴</td>
      <td>ردیف ۱۷: ۱۲۵</td>
      <td>ردیف ۱۷: ۲۱۶</td>
      <td>ردیف ۱۷: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۸: ۱</td>
      <td>ردیف ۱۸: ۸</td>
      <td>ردیف ۱۸: ۲۷</td>
      <td>ردیف ۱۸: ۶۴</td>
      <td>ردیف ۱۸: ۱۲۵</td>
      <td>ردیف ۱۸: ۲۱۶</td>
      <td>ردیف ۱۸: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۱۹: ۱</td>
      <td>ردیف ۱۹: ۸</td>
      <td>ردیف ۱۹: ۲۷</td>
      <td>ردیف ۱۹: ۶۴</td>
      <td>ردیف ۱۹: ۱۲۵</td>
      <td>ردیف ۱۹: ۲۱۶</td>
      <td>ردیف ۱۹: ۳۴۳</td>
    </tr>
    <tr>
      <td>ردیف ۲۰: ۱</td>
      <td>ردیف ۲۰: ۸</td>
      <td>ردیف ۲۰: ۲۷</td>
      <td>ردیف ۲۰: ۶۴</td>
      <td>ردیف ۲۰: ۱۲۵</td>
      <td>ردیف ۲۰: ۲۱۶</td>
      <td>ردیف ۲۰: ۳۴۳</td>
    </tr>
  </tbody>
</table>
```

#### CSS

وقتی به این استایل‌ها نگاه می‌کنید، می‌بینید که خاصیت `display` جدول روی `block` تنظیم شده است. این کار اسکرول را ممکن می‌کند، اما جدول یکپارچگی خود را تا حدی از دست می‌دهد و سلول‌ها سعی می‌کنند تا حد امکان کوچک شوند. برای رفع این مشکل، `white-space` را روی `nowrap` برای عنصر `<tbody>` تنظیم کرده‌ایم. اما این کار را برای `<thead>` انجام نمی‌دهیم تا عنوان‌های طولانی ستون‌ها را مجبور به پهن‌تر شدن از حد لازم برای نمایش داده‌ها نکنند.

برای اینکه headerهای جدول در هنگام اسکرول در صفحه باقی بمانند، خاصیت `position` را روی `sticky` برای عناصر `<th>` تنظیم کرده‌ایم. توجه کنید که `border-collapse` را روی `collapse` **قرار نداده‌ایم**، زیرا اگر این کار را انجام دهیم، header به درستی از بقیه جدول جدا نمی‌شود.

با توجه به اینکه `<table>` اندازه ثابتی دارد، `overflow: auto` بخش مهمی است، زیرا جدول را قابل اسکرول می‌کند.

```css
table,
th,
td {
  border: 1px solid black;
}

table {
  overflow: auto;
  width: 100%;
  max-width: 400px;
  height: 240px;
  display: block;
  margin: 0 auto;
  border-spacing: 0;
}

tbody {
  white-space: nowrap;
}

th,
td {
  padding: 5px 10px;
  border-top-width: 0;
  border-left-width: 0;
}

th {
  position: sticky;
  top: 0;
  background: white;
  vertical-align: bottom;
}

th:last-child,
td:last-child {
  border-right-width: 0;
}

tr:last-child td {
  border-bottom-width: 0;
}
```

#### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتواهای جریانی (flow content)</a>
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        به این ترتیب:
        <ol>
          <li>یک عنصر اختیاری {{HTMLElement("caption")}}</li>
          <li>صفر یا چند عنصر {{HTMLElement("colgroup")}}</li>
          <li>یک عنصر اختیاری {{HTMLElement("thead")}}</li>
          <li>
            یکی از موارد زیر:
            <ul>
              <li>صفر یا چند عنصر {{HTMLElement("tbody")}}</li>
              <li>یک یا چند عنصر {{HTMLElement("tr")}}</li>
            </ul>
          </li>
          <li>یک عنصر اختیاری {{HTMLElement("tfoot")}}</li>
        </ol>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف برچسب</th>
      <td>هیچ‌کدام؛ هر دو برچسب شروع و پایان ضروری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>هر عنصری که محتوای جریانی را می‌پذیرد</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role">table</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLTableElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- [یادگیری: مبانی جدول‌های HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- `caption`, `col`, `colgroup`, `tbody`, `td`, `tfoot`, `th`, `thead`, `tr`: دیگر عناصر مرتبط با جدول
- `background-color`: ویژگی CSS برای تعیین رنگ پس‌زمینهٔ جدول
- `border`, `border-collapse`, `border-spacing`: ویژگی‌های CSS برای کنترل ظاهر حاشیه‌ها، خطوط و قاب سلول‌ها
- `margin`, `padding`: ویژگی‌های CSS برای تراز کردن جدول و تنظیم فاصلهٔ محتوای سلول
- `text-align`: ویژگی CSS برای تراز افقی محتوای سلول جدول
- `vertical-align`: ویژگی CSS برای تراز عمودی محتوای سلول جدول
- `width`: ویژگی CSS برای کنترل عرض جدول