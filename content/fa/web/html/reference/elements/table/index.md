---
title: <table> HTML table element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/table
translated_by: n8n + AI
---

# \<table> HTML table element

عنصر `<table>` در HTML — نمایش داده‌های جدولی

عنصر **`<table>`** در HTML برای نمایش داده‌های جدولی استفاده می‌شود؛ یعنی اطلاعاتی که در یک جدول دو‌بعدی شامل ردیف‌ها و ستون‌های سلول‌های حاوی داده ارائه می‌شوند.

```html
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

```css
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

### ویژگی‌ها (Attributes)

این عنصر از [ویژگی‌های سراسری](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) پشتیبانی می‌کند.

#### ویژگی‌های منسوخ شده (Deprecated attributes)

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع و به‌روزرسانی کدهای قدیمی و همچنین آشنایی تاریخی ذکر شده‌اند.

* `align` (منسوخ شده)
  * : تراز افقی جدول را نسبت به عنصر والد مشخص می‌کرد. مقدارهای مجاز (enumerated) عبارت بودند از `left`، `center` و `right`. به‌جای آن از خصوصیت‌های CSS \{{cssxref("margin-inline-start")\}} و \{{cssxref("margin-inline-end")\}} استفاده کنید.
* `bgcolor` (منسوخ شده)
  * : رنگ پس‌زمینه جدول را تعیین می‌کرد. مقدار آن یک رنگ HTML بود: یا یک کد RGB هگزادسیمال ۶ رقمی با پیشوند `#`، یا یک رنگ نام‌دار (color keyword). سایر مقدارهای CSS \{{cssxref("\<color>")\}} پشتیبانی نمی‌شد. به‌جای آن از خصوصیت CSS \{{cssxref("background-color")\}} استفاده کنید.
* `border` (منسوخ شده)
  * : اندازه قاب دور جدول را بر حسب پیکسل و به صورت یک عدد صحیح غیرمنفی مشخص می‌کرد. اگر مقدار `0` می‌گرفت، ویژگی [`frame`](index.md#frame) به `void` تنظیم می‌شد. به‌جای آن از خصوصیت CSS \{{cssxref("border")\}} استفاده کنید.
* `cellpadding` (منسوخ شده)
  * : فاصله بین محتوای سلول و حاشیه آن را تعیین می‌کرد. این ویژگی منسوخ شده است؛ به‌جای آن از خصوصیت CSS \{{cssxref("padding")\}} روی عناصر \{{HTMLElement("th")\}} و \{{HTMLElement("td")\}} استفاده کنید.
* `cellspacing` (منسوخ شده)
  * : اندازه فاصله بین دو سلول را مشخص می‌کرد. این ویژگی منسوخ شده است؛ به‌جای آن از خصوصیت CSS \{{cssxref("border-spacing")\}} روی عنصر `<table>` استفاده کنید. توجه داشته باشید که اگر خصوصیت CSS \{{cssxref("border-collapse")\}} روی `collapse` تنظیم شده باشد، `border-spacing` تأثیری نخواهد داشت.
* `frame` \{{deprecated\_inline\}}
  * : مشخص می‌کند کدام سمت از قاب اطراف جدول نمایش داده شود. مقادیر ممکن از نوع \{{Glossary("enumerated")\}} عبارتند از: `void`، `above`، `below`، `hsides`، `vsides`، `lhs`، `rhs`، `box` و `border`. به‌جای آن از ویژگی‌های CSS \{{cssxref("border-style")\}} و \{{cssxref("border-width")\}} استفاده کنید، زیرا این attribute منسوخ شده است.
* `rules` \{{deprecated\_inline\}}
  * : محل نمایش خطوط (borders) در جدول را مشخص می‌کند. مقادیر ممکن از نوع \{{Glossary("enumerated")\}} عبارتند از: `none` (مقدار پیش‌فرض)، `groups` (عناصر \{{HTMLElement("thead")\}}، \{{HTMLElement("tbody")\}} و \{{HTMLElement("tfoot")\}})، `rows` (خطوط افقی)، `cols` (خطوط عمودی) و `all` (border دور تمام سلول‌ها). به‌جای آن از ویژگی CSS \{{cssxref("border")\}} روی عناصر مرتبط با جدول و همچنین روی خود `<table>` استفاده کنید، زیرا این attribute منسوخ شده است.
* `summary` \{{deprecated\_inline\}}
  * : متن جایگزینی را تعریف می‌کند که محتوای جدول را خلاصه می‌کند. به‌جای آن از عنصر \{{htmlelement("caption")\}} استفاده کنید، زیرا این attribute منسوخ شده است.
*   `width` \{{deprecated\_inline\}}

    * : عرض جدول را مشخص می‌کند. به‌جای آن از ویژگی CSS \{{cssxref("width")\}} استفاده کنید، زیرا این attribute منسوخ شده است.

    > \[!NOTE] در حالی که هیچ مشخصات HTML ای `height` را به عنوان attribute برای `<table>` در نظر نگرفته است، برخی مرورگرها از تفسیر غیراستاندارد `height` پشتیبانی می‌کنند. مقدار بدون واحد، حداقل ارتفاع مطلق را بر حسب پیکسل تنظیم می‌کند. اگر به صورت درصدی تنظیم شود، حداقل ارتفاع جدول نسبت به ارتفاع ظرف والد (parent container) خواهد بود. به‌جای آن از ویژگی CSS \{{cssxref("min-height")\}} استفاده کنید، زیرا این attribute منسوخ شده است.

### Visual layout of table contents

عناصر زیر بخشی از ساختار جدول هستند:

* \{{HTMLElement("caption")\}}
* \{{HTMLElement("thead")\}}
* \{{HTMLElement("colgroup")\}}
* \{{HTMLElement("col")\}}
* \{{HTMLElement("th")\}}
* \{{HTMLElement("tbody")\}}
* \{{HTMLElement("tr")\}}
* \{{HTMLElement("td")\}}
* \{{HTMLElement("tfoot")\}}

جعبهٔ `<table>` یک context قالب‌بندی جدول ایجاد می‌کند. عناصر داخل `<table>` جعبه‌های مستطیلی تولید می‌کنند. هر جعبه طبق قوانین زیر تعدادی سلول جدول را اشغال می‌کند:

1. جعبه‌های ردیف (row boxes) جدول را به ترتیب کد منبع از بالا به پایین پر می‌کنند. هر جعبه ردیف، یک ردیف از سلول‌ها را اشغال می‌کند.
2. جعبه گروه ردیف (row group box) یک یا چند جعبه ردیف را اشغال می‌کند.
3. جعبه‌های ستون (column boxes) به ترتیب کد منبع در کنار یکدیگر قرار می‌گیرند. بسته به مقدار attribute [`dir`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/dir/)، ستون‌ها در جهت چپ‌به‌راست یا راست‌به‌چپ چیده می‌شوند. یک جعبه ستون، یک یا چند ستون از سلول‌های جدول را اشغال می‌کند.
4. جعبه گروه ستون (column group box) یک یا چند جعبه ستون را اشغال می‌کند.
5. جعبه سلول (cell box) ممکن است روی چند ردیف و ستون کشیده شود. عامل‌های کاربر (user agents) سلول‌ها را برش می‌دهند تا در تعداد ردیف‌ها و ستون‌های موجود جا شوند.

سلول‌های جدول دارای padding هستند. جعبه‌هایی که جدول را می‌سازند margin ندارند.

#### Table layers and transparency

برای استایل‌دهی، عناصر جدول را می‌توان به شکل شش لایه‌ی روی‌هم‌افتاده در نظر گرفت:

پس‌زمینه‌ای که روی یک عنصر در یک لایه تنظیم شده باشد، تنها زمانی دیده می‌شود که لایه‌های بالای آن پس‌زمینه شفاف داشته باشند. سلول از دست‌رفته (missing cell) به گونه‌ای رندر می‌شود که گویی یک جعبه سلول جدول ناشناس (anonymous table-cell box) آن مکان را اشغال کرده است.

### Accessibility

#### Captions

ارائه یک عنصر \{{HTMLElement("caption")\}} که مقدار آن به‌وضوح و به‌طور خلاصه هدف جدول را توصیف می‌کند، به افراد کمک می‌کند تصمیم بگیرند که آیا نیاز به بررسی بقیه محتوای جدول دارند یا از آن رد شوند.

این کار به افرادی که با کمک فناوری کمکی مانند صفحه‌خوان (screen reader) پیمایش می‌کنند، افرادی که مشکلات بینایی دارند، و افرادی که دغدغه‌های شناختی دارند کمک می‌کند.

* [MDN — افزودن عنوان به جدول با `<caption>`](../../../../../../../en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility/#adding_a_caption_to_your_table_with_caption)
* [عنوان و خلاصه • جدولها • آموزشهای دسترسپذیری وب W3C WAI](https://www.w3.org/WAI/tutorials/tables/caption-summary/)

#### محدودهبندی ردیفها و ستونها

ویژگی `scope` روی سلولهای سربرگ (المانهای `<th>`) در زمینههای ساده اضافی است، چون scope بهطور خودکار استنباط میشود. با این حال، برخی فناوریهای کمکی ممکن است نتوانند استنباط درستی داشته باشند؛ بنابراین مشخص کردن scope برای سربرگها میتواند تجربه کاربر را بهبود دهد. در جدولهای پیچیده، میتوان `scope` را مشخص کرد تا اطلاعات لازم درباره سلولهای مرتبط با یک سربرگ فراهم شود.

* [راهنمای دسترسپذیری جدول در MDN](../../../../../../../en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility/)
* [جدولهای با دو سربرگ • جدولها • آموزشهای دسترسپذیری وب W3C WAI](https://www.w3.org/WAI/tutorials/tables/two-headers/)
* [جدولهای با سربرگهای نامنظم • جدولها • آموزشهای دسترسپذیری وب W3C WAI](https://www.w3.org/WAI/tutorials/tables/irregular/)
* [H63: استفاده از ویژگی scope برای ارتباط دادن سلولهای سربرگ و سلولهای داده در جدولهای داده | تکنیکهای W3C برای WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/H63.html)

#### جدولهای پیچیده

فناوریهای کمکی مانند صفحهخوانها ممکن است در تجزیه جدولهایی مشکل داشته باشند که آنقدر پیچیدهاند که سلولهای سربرگ را نمیتوان بهصورت کاملاً افقی یا عمودی با سلولها مرتبط کرد. این وضعیت معمولاً با وجود ویژگیهای [`colspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/td/#colspan) و [`rowspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/td/#rowspan) نشان داده میشود.

در حالت ایدهآل، به راههای جایگزین برای ارائه محتوای جدول فکر کنید؛ از جمله تقسیم آن به مجموعهای از جدولهای کوچکتر و مرتبط که مجبور به استفاده از ویژگیهای [`colspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/td/#colspan) و [`rowspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/td/#rowspan) نباشند. این کار علاوه بر کمک به افرادی که از فناوری کمکی استفاده میکنند تا محتوای جدول را بفهمند، میتواند برای افرادی با مشکلات شناختی هم مفید باشد که درک ارتباطاتی که ساختار جدول توصیف میکند برایشان دشوار است.

اگر جدول قابل تقسیم نیست، از ترکیب ویژگیهای [`id`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/id/) و [`headers`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/td/#headers) استفاده کنید تا بهصورت برنامهای (programmatically) هر سلول جدول را به سربرگ(های) مرتبط با آن (`<th>`) متصل کنید.

* [راهنمای دسترسپذیری جدول در MDN](../../../../../../../en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility/)
* [جدولهای با سربرگهای چندسطحی • جدولها • آموزشهای دسترسپذیری وب W3C WAI](https://www.w3.org/WAI/tutorials/tables/multi-level/)
* [H43: استفاده از ویژگیهای id و headers برای مرتبط کردن سلولهای داده با سلولهای سربرگ در جدولهای داده | تکنیکهای W3C برای WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/H43.html)

### مثالها

مثالهای زیر شامل جدولهایی با پیچیدگی فزاینده هستند. همچنین برای اطلاعات مربوط به استایلدهی جدول، از جمله تکنیکهای رایج و کاربردی، به راهنمای مبتدی [استایلدهی جدولها](../../../../../../../en-US/docs/Learn_web_development/Core/Styling_basics/Tables/) مراجعه کنید.

از آنجا که ساختار یک `<table>` شامل استفاده از چندین المان HTML مرتبط با جدول و همچنین ویژگیهای مختلفی است، مثالهای زیر برای ارائه توضیحی سادهشده طراحی شدهاند که اصول پایه و استانداردهای رایج را پوشش میدهد. اطلاعات بیشتر و جزئیتر را میتوانید در صفحات مرتبطی که لینک شدهاند بیابید.

این مثالهای جدول نشان میدهند که چگونه یک جدول دسترسپذیر بسازیم که با HTML ساختاربندی شده و با [CSS](../../../../../../../en-US/docs/Web/CSS/) استایلدهی شده است.

به دلیل ساختار جداول HTML، حجم markup (نشانه‌گذاری) می‌تواند به سرعت زیاد شود. به همین دلیل مهم است که هدف و ظاهر نهایی جدول را به‌روشنی مشخص کنید تا ساختار مناسبی ایجاد شود. یک ساختار منطقی که با markup semantic (معنایی) توسعه داده شده باشد، نه تنها استایل‌دهی را آسان‌تر می‌کند، بلکه جداول مفید و قابل دسترسی ایجاد می‌کند که همه، از جمله موتورهای جستجو و کاربران فناوری‌های کمکی، بتوانند آن را درک کرده و در آن پیمایش کنند.

مثال اول بسیار ساده است و مثال‌های بعدی به تدریج پیچیده‌تر می‌شوند. ابتدا یک ساختار جدول HTML بسیار پایه برای جدول ایجاد می‌کنیم. دو مثال اول شامل گروه‌های بخش‌بندی جدول مانند head، body یا foot تعریف‌شده نیستند و هیچ سلول spanning یا روابط صریح بین سلول‌ها را شامل نمی‌شوند. حتی یک caption هم ارائه نشده است. در طول مثال‌ها، به تدریج بهبود می‌یابند تا تمام ویژگی‌های جدول را که یک جدول داده‌های پیچیده باید داشته باشد، در بر گیرند.

#### جدول پایه

این مثال شامل یک جدول _بسیار_ ساده با سه ردیف و دو ستون است. برای نمایش استایل‌های پیش‌فرض مرورگر برای جدول، در این مثال از CSS استفاده نشده است.

**HTML**

ردیف‌های جدول با عناصر \{{HTMLElement("tr")\}} تعریف می‌شوند و ستون‌ها با سلول‌های header و داده درون آن‌ها مشخص می‌گردند. ردیف اول شامل سلول‌های header (عناصر \{{HTMLElement("th")\}}) است که به عنوان header ستون برای سلول‌های داده (عناصر \{{HTMLElement("td")\}}) عمل می‌کنند. هر عنصر (\{{HTMLElement("th")\}} یا \{{HTMLElement("td")\}}) در هر ردیف در ستون مربوط به خود قرار دارد — یعنی اولین عنصر یک ردیف در ستون اول و دومین عنصر آن ردیف در ستون دوم است.

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

**نتیجه**

هیچ [CSS](../../../../../../../en-US/docs/Web/CSS/) سفارشی یا [user stylesheet](../../../../../../../en-US/docs/Web/CSS/Guides/Cascade/Introduction/#author_stylesheets) روی این جدول اعمال نشده است. استایل‌دهی صرفاً از [user-agent stylesheet](../../../../../../../en-US/docs/Web/CSS/Guides/Cascade/Introduction/#user-agent_stylesheets) ناشی می‌شود.

#### جدول گسترش‌یافته با سلول‌های header

این مثال [جدول پایه](index.md#basic_table) را گسترش می‌دهد، محتوا را افزایش داده و استایل‌های CSS پایه را اضافه می‌کند.

**HTML**

جدول اکنون چهار ردیف (عناصر \{{HTMLElement("tr")\}}) دارد که هر کدام چهار ستون دارند. ردیف اول یک ردیف از سلول‌های header است (ردیف اول فقط شامل عناصر \{{HTMLElement("th")\}} است). ردیف‌های بعدی شامل یک ستون header (عناصر \{{HTMLElement("th")\}} به عنوان اولین فرزند هر ردیف) و سه ستون داده (عناصر \{{HTMLElement("td")\}}) هستند. از آنجایی که از عناصر بخش‌بندی جدول استفاده نشده، مرورگر به طور خودکار ساختار گروه محتوا را تعریف می‌کند، یعنی تمام ردیف‌ها درون بدنه جدول یک عنصر ضمنی \{{HTMLElement("tbody")\}} قرار می‌گیرند.

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

**CSS**

با CSS، استایل‌دهی پایه را برای ایجاد خطوط دور اجزای جدول فراهم می‌کنیم تا ساختار داده واضح‌تر شود. CSS یک حاشیه solid دور `<table>` و دور هر یک از سلول‌های جدول، از جمله آن‌هایی که با عناصر \{{HTMLElement("th")\}} و \{{HTMLElement("td")\}} مشخص شده‌اند، اضافه می‌کند و هر header و سلول داده را مشخص می‌کند.

```css
table {
  border: 2px solid rgb(140 140 140);
}

th,
td {
  border: 1px solid rgb(160 160 160);
}
```

#### مشخص کردن ارتباط سلول‌های جدول

پیش از آنکه جدول را به روش‌های پیشرفته‌تر گسترش دهیم، بهتر است با تعریف رابطه بین سلول‌های سربرگ و سلول‌های داده (المان‌های `<th>` و `<td>`) دسترس‌پذیری (accessibility) را بهبود ببخشیم.

**HTML**

این کار با افزودن ویژگی (attribute) `scope` به المان‌های `<th>` و تنظیم مقدار آن به `col` (ستون) یا `row` (ردیف) انجام می‌شود.

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

نتیجهٔ CSS و نمایش بصری تغییری نمی‌کند. این سازگاری اطلاعات زمینه‌ای مفیدی در اختیار فناوری‌های کمکی مانند صفحه‌خوان‌ها قرار می‌دهد تا مشخص کنند هر سلول به کدام سربرگ مربوط است.

> \[!NOTE] اگر ساختار جدول پیچیده‌تر باشد، استفاده (اضافی) از ویژگی `headers` روی المان‌های `<th>` و `<td>` می‌تواند دسترس‌پذیری را بهبود ببخشد و به فناوری‌های کمکی در شناسایی رابطه بین سلول‌ها کمک کند؛ به [جدول‌های پیچیده](index.md#complicated_tables) مراجعه کنید.

#### مشخص کردن صریح گروه‌های بخش جدول

علاوه بر بهبود دسترس‌پذیری با مشخص کردن روابط سلول‌ها، می‌توان معنایی (semantics) جدول را نیز با معرفی گروه‌های بخش جدول بهتر کرد.

**HTML**

از آنجا که اولین ردیف (المان `<tr>`) فقط شامل سلول‌های سربرگ ستون است و سربرگ بقیه محتوای جدول را فراهم می‌کند، می‌توان آن را در المان `<thead>` قرار داد تا این ردیف به‌صورت صریح به‌عنوان بخش سربرگ جدول مشخص شود. علاوه بر این، کاری که مرورگر به‌صورت خودکار انجام می‌دهد را می‌توان به‌صورت صریح هم تعریف کرد: بخش بدنه جدول که داده‌های اصلی را شامل می‌شود، با قرار دادن ردیف‌های مربوطه در المان `<tbody>` مشخص می‌شود. استفاده صریح از المان `<tbody>` به مرورگر کمک می‌کند ساختار مورد نظر جدول را ایجاد کند و از نتایج ناخواسته جلوگیری کند.

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

باز هم نتیجهٔ CSS و نمایش بصری تغییر نمی‌کند. مشخص کردن این گروه‌های بخش، اطلاعات زمینه‌ای مفیدی برای فناوری‌های کمکی از جمله صفحه‌خوان‌ها و موتورهای جستجو و همچنین برای استایل‌دهی با CSS فراهم می‌کند که در مثال بعدی نشان داده خواهد شد.

#### ادغام ستون‌ها و ردیف‌ها

در این مثال، جدول را بیشتر گسترش می‌دهیم؛ یک ستون اضافه می‌کنیم و یک بخش سربرگ چندردیفی معرفی می‌کنیم.

**HTML**

با تکمیل جدولی که تا اینجا ساختهایم، یک ستون جدید برای «تاریخ پایان عضویت» در هر ردیف از بخش بدنه با استفاده از عنصر `<td>` اضافه میشود. همچنین یک ردیف دیگر (عنصر `<tr>`) در بخش سربرگ (`<thead>`) قرار می‌گیرد تا سربرگی به نام «Membership Dates» به عنوان عنوانِ ستون‌های «Joined» و «Canceled» معرفی شود.

برای ایجاد ردیف دومِ سربرگ، ویژگی‌های [`colspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/th/#colspan) و [`rowspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/th/#rowspan) (attribute) به عنصرهای `<th>` اضافه می‌شوند تا سلول‌های سربرگ به ستون‌ها و ردیف‌های درست نسبت داده شوند.

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

```css
table {
  border: 2px solid rgb(140 140 140);
}

th,
td {
  border: 1px solid rgb(160 160 160);
}
```

**نتیجه**

بخش سربرگ حالا دو ردیف دارد؛ ردیفی با سربرگ‌های (عنصرهای `<th>`) «Name»، «ID»، «Membership Dates» و «Balance»، و یک سربرگ «Membership Dates» با دو زیرسربرگ در ردیف دوم: «Joined» و «Canceled». این کار به این صورت انجام می‌شود:

* سلول‌های سربرگ «Name»، «ID» و «Balance» در ردیف اول با استفاده از ویژگی [`rowspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/th/#rowspan) هر دو ردیف سربرگ جدول را پوشش می‌دهند و به این ترتیب هرکدام به ارتفاع دو ردیف می‌شوند.
* سلول سربرگ «Membership Dates» در ردیف اول با استفاده از ویژگی [`colspan`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/th/#colspan) دو ستون را پوشش می‌دهد و به این ترتیب عرض آن دو ستون می‌شود.
* ردیف دوم فقط شامل دو سلول سربرگ «Joined» و «Canceled» است؛ زیرا سه ستون دیگر با سلول‌های ردیف اول که دو ردیف را پوشش می‌دهند ادغام شده‌اند. این دو سلول سربرگ دقیقاً زیر سربرگ «Membership Dates» قرار می‌گیرند.

#### کپشن جدول و جمع‌بندی ستون

ارائه خلاصه‌ای از محتوای جدول یک رویه رایج و توصیه‌شده است؛ این کار به کاربران کمک می‌کند سریعاً بفهمند جدول چقدر مرتبط است. علاوه بر این، ستون «Balance» با نمایش مجموع موجودی اعضا جمع‌بندی می‌شود.

**HTML**

خلاصه جدول با استفاده از یک [caption](index.md#captions) (عنصر `<caption>`) به عنوان اولین فرزند `<table>` اضافه می‌شود. این کپشن، نام قابل‌دسترس (accessible name) یا توضیح قابل‌دسترس (accessible description) جدول را فراهم می‌کند.

در نهایت، یک بخش پاصفحه جدول (عنصر `<tfoot>`) در پایین بدنه اضافه می‌شود، با ردیفی که ستون «Balance» را با نمایش مجموع جمع‌بندی می‌کند. عنصرها و ویژگی‌هایی که قبلاً معرفی شدند در اینجا به کار رفته‌اند.

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

```css
table {
  border: 2px solid rgb(140 140 140);
}

th,
td {
  border: 1px solid rgb(160 160 160);
}
```

#### Basic table styling

حالا یک استایل پایه روی جدول اعمال می‌کنیم تا نوع قلم (typeface) را تنظیم کنیم و به ردیف‌های سر (head) و پا (foot) یک `background-color` اضافه کنیم. این بار HTML تغییری نمی‌کند، پس مستقیم سراغ CSS می‌رویم.

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

**CSS**

در اینجا با استفاده از خاصیت `font` روی عنصر `<table>` یک قلم خوش‌ترکیب (یا بسته به سلیقه‌تان قلم بی‌عرض sans-serif) تنظیم می‌کنیم. اما بخش جالب، استایل دوم است: به عناصر `<tr>` که درون `<thead>` و `<tfoot>` قرار دارند، یک `background-color` آبی روشن اضافه می‌کنیم. این روشی سریع برای اعمال یک رنگ پس‌زمینه به تمام سلول‌های بخش‌های مشخص در یک لحظه است.

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

#### Advanced table styling

حالا می‌خواهیم همه‌کاره شویم: استایل‌هایی روی ردیف‌های سر (header) و بدنه (body) اعمال می‌کنیم، از جمله رنگ‌های متناوب ردیف‌ها، سلول‌هایی با رنگ‌های متفاوت بسته به جایگاهشان در ردیف و غیره. بیایید اول نتیجه نهایی را ببینیم.

باز هم هیچ تغییری در HTML داده نشده است. ببینید آماده‌سازی درست ساختار HTML چه تأثیری می‌تواند داشته باشد؟

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

**CSS**

این بار CSS بسیار مفصل‌تر است. پیچیده نیست، اما اتفاقات زیادی در آن رخ می‌دهد. بیایید آن را موبهمو بررسی کنیم.

در اینجا، برای حذف فاصله بین سلول‌ها و تبدیل حاشیه‌های مجاور به یک حاشیه‌ی واحد به‌جای حاشیه‌های دوتایی، ویژگی‌های `border-collapse` و `border-spacing` اضافه شده‌اند. همچنین `<caption>` با استفاده از ویژگی `caption-side` در پایین (`bottom`) جدول قرار گرفته است:

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

در مرحله‌ی بعد، ویژگی `padding` برای ایجاد فضای خالی دور محتوای همه‌ی سلول‌های جدول استفاده شده است. ویژگی `vertical-align` محتوای سلول‌های سربرگ را در پایین سلول تراز می‌کند؛ این رفتار را می‌توان در سلول‌های سربرگی که دو ردیف را پوشش می‌دهند مشاهده کرد:

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

قانون بعدی CSS، رنگ پس‌زمینه‌ی همه‌ی عناصر `<tr>` را در سربرگ جدول (که با `<thead>` مشخص شده) تعیین می‌کند. سپس حاشیه‌ی پایین سربرگ به‌صورت خطی به عرض دو پیکسل تنظیم شده است. اما توجه کنید که ما با استفاده از انتخابگر `:nth-of-type`، ویژگی `border-bottom` را روی ردیف _دوم_ سربرگ اعمال می‌کنیم. چرا؟ چون سربرگ از دو ردیف تشکیل شده که برخی از سلول‌ها هر دو را پوشش داده‌اند. یعنی واقعاً دو ردیف وجود دارد؛ اعمال استایل روی ردیف اول نتیجه‌ی مورد انتظار را به ما نمی‌دهد:

```css
thead > tr {
  background-color: rgb(228 240 245);
}

thead > tr:nth-of-type(2) {
  border-bottom: 2px solid rgb(140 140 140);
}
```

حالا دو سلول سربرگ «Joined» و «Canceled» را به‌ترتیب با رنگ‌های سبز و قرمز استایل می‌دهیم تا «خوبیِ» عضویت جدید و «ناراحتیِ» لغو عضویت را نشان دهند. در اینجا با استفاده از انتخابگر `:last-of-type` به آخرین ردیف بخش سربرگ جدول می‌رویم و به اولین سلول سربرگ در آن (سربرگ «Joined») رنگی سبز و به دومین سلول سربرگ (سربرگ «Canceled») رنگی قرمز می‌دهیم:

```css
thead > tr:last-of-type > th:nth-of-type(1) {
  background-color: rgb(225 255 225);
}

thead > tr:last-of-type > th:nth-of-type(2) {
  background-color: rgb(255 225 225);
}
```

چون ستون اول هم باید برجسته باشد، در این‌جا چند استایل سفارشی دیگر هم اضافه شده است. این قاعدهٔ CSS اولین سلولِ عنوان را در هر ردیف از بدنهٔ جدول با خاصیت `text-align` به‌چپ تراز می‌کند و با یک `background-color` کمی متفاوت، آن را متمایز می‌کند:

```css
tbody > tr > th:first-of-type {
  text-align: left;
  background-color: rgb(225 229 244);
}
```

برای بهبود خوانایی داده‌های جدول، معمول است که رنگ ردیف‌ها را یک‌درمیان تغییر دهند؛ به این کار گاهی «زبرا استرایپینگ» هم می‌گویند. بیایید به هر ردیف زوج یک `background-color` اضافه کنیم:

```css
tbody > tr:nth-of-type(even) {
  background-color: rgb(237 238 242);
}
```

از آنجا که در جدول‌ها مرسوم است مقادیر پول را راست‌چین نشان دهند، این کار را هم انجام می‌دهیم. این قاعده فقط خاصیت `text-align` را برای آخرین `<td>` در هر ردیف بدنه، روی `right` قرار می‌دهد:

```css
tbody > tr > td:last-of-type {
  text-align: right;
}
```

در نهایت، برای بخش پابرگی (foot) جدول هم استایلی شبیه به سربرگ اعمال می‌کنیم تا آن نیز برجسته شود:

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

#### نمایش جدول‌های بزرگ در فضاهای کوچک

یک مشکل رایج در جدول‌های وب این است که در صفحه‌های کوچک با محتوای زیاد، طبیعتاً خوب کار نمی‌کنند و روش اسکرول‌پذیر کردنشان هم چندان واضح نیست، به‌خصوص وقتی که مارک‌آپ از یک CMS می‌آید و نمی‌توان آن را تغییر داد تا یک wrapper داشته باشد.

این مثال یک راه برای نمایش جدول‌ها در فضاهای کوچک ارائه می‌دهد. محتوای HTML را مخفی کرده‌ایم چون خیلی بزرگ است و نکتهٔ خاصی ندارد؛ اما CSS این مثال ارزش بررسی دارد.

```markdown
| 1<sup>3</sup> برابر است با: | 2<sup>3</sup> برابر است با: | 3<sup>3</sup> برابر است با: | 4<sup>3</sup> برابر است با: | 5<sup>3</sup> برابر است با: | 6<sup>3</sup> برابر است با: | 7<sup>3</sup> برابر است با: |
| --- | --- | --- | --- | --- | --- | --- |
| ردیف 1: 1 | ردیف 1: 8 | ردیف 1: 27 | ردیف 1: 64 | ردیف 1: 125 | ردیف 1: 216 | ردیف 1: 343 |
| ردیف 2: 1 | ردیف 2: 8 | ردیف 2: 27 | ردیف 2: 64 | ردیف 2: 125 | ردیف 2: 216 | ردیف 2: 343 |
| ردیف 3: 1 | ردیف 3: 8 | ردیف 3: 27 | ردیف 3: 64 | ردیف 3: 125 | ردیف 3: 216 | ردیف 3: 343 |
| ردیف 4: 1 | ردیف 4: 8 | ردیف 4: 27 | ردیف 4: 64 | ردیف 4: 125 | ردیف 4: 216 | ردیف 4: 343 |
| ردیف 5: 1 | ردیف 5: 8 | ردیف 5: 27 | ردیف 5: 64 | ردیف 5: 125 | ردیف 5: 216 | ردیف 5: 343 |
| ردیف 6: 1 | ردیف 6: 8 | ردیف 6: 27 | ردیف 6: 64 | ردیف 6: 125 | ردیف 6: 216 | ردیف 6: 343 |
| ردیف 7: 1 | ردیف 7: 8 | ردیف 7: 27 | ردیف 7: 64 | ردیف 7: 125 | ردیف 7: 216 | ردیف 7: 343 |
| ردیف 8: 1 | ردیف 8: 8 | ردیف 8: 27 | ردیف 8: 64 | ردیف 8: 125 | ردیف 8: 216 | ردیف 8: 343 |
| ردیف 9: 1 | ردیف 9: 8 | ردیف 9: 27 | ردیف 9: 64 | ردیف 9: 125 | ردیف 9: 216 | ردیف 9: 343 |
| ردیف 10: 1 | ردیف 10: 8 | ردیف 10: 27 | ردیف 10: 64 | ردیف 10: 125 | ردیف 10: 216 | ردیف 10: 343 |
| ردیف 11: 1 | ردیف 11: 8 | ردیف 11: 27 | ردیف 11: 64 | ردیف 11: 125 | ردیف 11: 216 | ردیف 11: 343 |
| ردیف 12: 1 | ردیف 12: 8 | ردیف 12: 27 | ردیف 12: 64 | ردیف 12: 125 | ردیف 12: 216 | ردیف 12: 343 |
| ردیف 13: 1 | ردیف 13: 8 | ردیف 13: 27 | ردیف 13: 64 | ردیف 13: 125 | ردیف 13: 216 | ردیف 13: 343 |
| ردیف 14: 1 | ردیف 14: 8 | ردیف 14: 27 | ردیف 14: 64 | ردیف 14: 125 | ردیف 14: 216 | ردیف 14: 343 |
| ردیف 15: 1 | ردیف 15: 8 | ردیف 15: 27 | ردیف 15: 64 | ردیف 15: 125 | ردیف 15: 216 | ردیف 15: 343 |
| ردیف 16: 1 | ردیف 16: 8 | ردیف 16: 27 | ردیف 16: 64 | ردیف 16: 125 | ردیف 16: 216 | ردیف 16: 343 |
| ردیف 17: 1 | ردیف 17: 8 | ردیف 17: 27 | ردیف 17: 64 | ردیف 17: 125 | ردیف 17: 216 | ردیف 17: 343 |
| ردیف 18: 1 | ردیف 18: 8 | ردیف 18: 27 | ردیف 18: 64 | ردیف 18: 125 | ردیف 18: 216 | ردیف 18: 343 |
| ردیف 19: 1 | ردیف 19: 8 | ردیف 19: 27 | ردیف 19: 64 | ردیف 19: 125 | ردیف 19: 216 | ردیف 19: 343 |
| ردیف 20: 1 | ردیف 20: 8 | ردیف 20: 27 | ردیف 20: 64 | ردیف 20: 125 | ردیف 20: 216 | ردیف 20: 343 |
```

**CSS**

وقتی به این استایل‌ها نگاه می‌کنید، متوجه می‌شوید که خاصیت `display` جدول روی `block` تنظیم شده است. این کار امکان اسکرول را فراهم می‌کند، اما باعث می‌شود جدول تا حدی یکپارچگی خود را از دست بدهد و سلول‌ها سعی کنند تا حد ممکن کوچک شوند. برای رفع این مشکل، خاصیت `white-space` را روی `nowrap` برای عنصر `<tbody>` تنظیم کرده‌ایم. اما این کار را برای `<thead>` انجام نمی‌دهیم تا عنوان‌های طولانی باعث نشوند ستون‌ها از حد لازم برای نمایش داده‌ها عریض‌تر شوند.

برای اینکه سرستون‌ها هنگام اسکرول به پایین همچنان در صفحه باقی بمانند، خاصیت `position` را روی `sticky` برای عناصر `<th>` تنظیم کرده‌ایم. توجه داشته باشید که **نه** `border-collapse` را روی `collapse` تنظیم کرده‌ایم، چون اگر این کار را بکنیم، سرستون به درستی از بقیه جدول جدا نمی‌شود.

با توجه به اینکه `<table>` اندازه ثابتی دارد، `overflow` با مقدار `auto` بخش مهمی است، زیرا جدول را قابل اسکرول می‌کند.

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

**نتیجه**

### خلاصه فنی

\`

* یک عنصر اختیاری \`

\`

* یکی از موارد زیر:
  * صفر یا چند عنصر \`

\`

* یک یا چند عنصر \`

\`

* یک عنصر اختیاری \`

\`

| [دسته‌بندی محتوا](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | [محتواهای جریانی (Flow content)](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content) |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| محتوای مجاز                                                                            | <p>به این ترتیب:</p><ol><li>یک عنصر اختیاری `</li></ol>                                                            |
|                                                                                        |                                                                                                                    |
| حذف تگ                                                                                 | هیچکدام، هر دو تگ شروع و پایان الزامی هستند.                                                                       |
| والدین مجاز                                                                            | هر عنصری که محتوای جریانی (flow content) را بپذیرد.                                                                |
| نقش ARIA پیش‌فرض                                                                       | [`table`](../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role/)                      |
| نقش‌های ARIA مجاز                                                                      | هر نقشی                                                                                                            |
| رابط DOM                                                                               | \`HTMLTableElement\`                                                                                               |

### مشخصات

### سازگاری با مرورگر

### همچنین ببینید

```markdown
- [Learn: HTML table basics](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- caption, col, colgroup, tbody, td, tfoot, th, thead, tr: سایر عناصر مرتبط با جدول
- background-color: ویژگی CSS برای تنظیم رنگ پس‌زمینه جدول
- border, border-collapse, border-spacing: ویژگی‌های CSS برای کنترل ظاهر حاشیه‌های سلول، خطوط و قاب جدول
- margin, padding: ویژگی‌های CSS برای تراز کردن جدول و تنظیم فاصله بین محتوای سلول‌ها
- text-align: ویژگی CSS برای تراز افقی محتوای سلول‌های جدول
- vertical-align: ویژگی CSS برای تراز عمودی محتوای سلول‌های جدول
- width: ویژگی CSS برای کنترل عرض جدول
```
