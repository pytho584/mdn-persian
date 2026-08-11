---
title: "CSS box alignment overview"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_alignment/Overview"
translated_by: "n8n + AI"
---

ماژول [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment) ویژگی‌های مرتبط با هم‌ترازی جعبه‌ها را در مدل‌های چیدمان مختلف CSS مشخص می‌کند. هدف این ماژول ایجاد یک روش یکسان برای هم‌ترازی در تمام CSS است. ویژگی‌های box alignment امکان هم‌ترازی کامل افقی و عمودی را فراهم می‌کنند.

این راهنما مفاهیم کلی این ماژول را توضیح می‌دهد. راهنماهای دیگر اطلاعات بیشتری درباره box alignment در [flexbox](/en-US/docs/Web/CSS/Guides/Box_alignment/In_flexbox)، [grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)، [multiple-column layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_multi-column_layout) و [block, absolutely positioned and table layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_block_abspos_tables) ارائه می‌دهند. هم‌ترازی متن در ماژول‌های [CSS text](/en-US/docs/Web/CSS/Guides/Text) و [CSS inline layout](/en-US/docs/Web/CSS/Guides/Inline_layout) پوشش داده شده است.

## مفاهیم و اصطلاحات کلیدی

این مشخصات فنی، اصطلاحاتی را برای alignment تعریف می‌کند تا بتوان درباره این ویژگی‌ها بدون وابستگی به یک روش layout خاص صحبت کرد. همچنین مفاهیم کلیدی مشترکی بین تمام روش‌های چیدمان وجود دارد.

### ارتباط با writing modes

Alignment با writing modes (حالت‌های نوشتاری) مرتبط است. به این معنا که هنگام هم‌ترازی یک آیتم، به ابعاد فیزیکی (بالا، پایین، چپ، راست) توجه نمی‌کنیم، بلکه بر اساس start و end آن بُعد خاص کار می‌کنیم. این کار تضمین می‌کند که alignment در هر writing mode ای که سند استفاده می‌کند به یک شکل عمل کند.

### دو بُعد alignment

هنگام استفاده از ویژگی‌های box alignment، محتوا را روی یکی از دو محور هم‌تراز می‌کنید: **محور inline** (یا main) و **محور block** (یا cross). محور inline همان جهتی است که کلمات در یک جمله در writing mode جاری حرکت می‌کنند. برای مثال در انگلیسی، محور inline افقی است. محور block جهتی است که بلوک‌ها (مانند عناصر پاراگراف) در آن قرار می‌گیرند و عمود بر محور inline است.

![محور inline از چپ به راست (افقی) و محور block از بالا به پایین (عمودی) است.](two-axes.png)

برای هم‌ترازی آیتم‌ها روی محور inline از ویژگی‌هایی استفاده می‌کنید که با `justify-` شروع می‌شوند:

- {{cssxref("justify-items")}}
- {{cssxref("justify-self")}}
- {{cssxref("justify-content")}}

برای هم‌ترازی روی محور block از ویژگی‌هایی که با `align-` شروع می‌شوند استفاده می‌کنید:

- {{cssxref("align-items")}}
- {{cssxref("align-self")}}
- {{cssxref("align-content")}}

Flexbox یک پیچیدگی اضافه دارد: این قاعده زمانی صادق است که {{cssxref("flex-direction")}} روی `row` تنظیم شده باشد. وقتی flexbox روی `column` تنظیم می‌شود، این ویژگی‌ها جابه‌جا می‌شوند. بنابراین در کار با flexbox بهتر است به جای inline و block به محور main و cross فکر کنید. ویژگی‌های `justify-` همیشه برای هم‌ترازی روی محور main استفاده می‌شوند و ویژگی‌های `align-` روی محور cross.

### alignment subject (موضوع هم‌ترازی)

**{{Glossary("alignment subject")}}** چیزی است که در حال هم‌تراز شدن است. برای `justify-self` یا `align-self`، یا وقتی این مقادیر را به صورت گروهی با `justify-items` یا `align-items` تنظیم می‌کنید، alignment subject همان margin box عنصری است که این ویژگی روی آن اعمال می‌شود. ویژگی‌های `justify-content` و `align-content` بسته به روش layout متفاوت عمل می‌کنند.

### alignment container (ظرف هم‌ترازی)

**{{Glossary("alignment container")}}** جعبه‌ای است که subject درون آن هم‌تراز می‌شود. معمولاً این جعبه، containing block عنصر subject است. یک alignment container ممکن است شامل یک یا چند alignment subject باشد.

تصویر زیر یک alignment container را با دو alignment subject درون آن نشان می‌دهد.

![یک جعبه شامل دو مستطیل با عرض یکسان اما ارتفاع‌های متفاوت. دو مستطیل نسبت به بالا هم‌تراز شده‌اند؛ یعنی خط بالای هر دو حدود ۱۰ پیکسل از لبهٔ بالای جعبهٔ والد فاصله دارد.](align-container-subjects.png)

## انواع هم‌ترازی

مشخصات CSS سه نوع هم‌ترازی را تعریف کرده است که با مقدارهای کلیدواژه‌ای (keyword values) کار می‌کنند:

- [هم‌ترازی موقعیتی](#positional_alignment)
- [هم‌ترازی baseline](#baseline_alignment)
- [هم‌ترازی توزیعی](#distributed_alignment)

### هم‌ترازی موقعیتی

**هم‌ترازی موقعیتی** یعنی موقعیتِ یک alignment subject نسبت به alignment container خودش. مقدارهای کلیدواژه‌ای هم‌ترازی موقعیتی برای content alignment با `justify-content` و `align-content` و همچنین برای self alignment با `justify-self` و `align-self` تعریف شده‌اند:

- `center`
- `start`
- `end`
- `self-start`
- `self-end`
- `flex-start` (فقط در flexbox)
- `flex-end` (فقط در flexbox)
- `left`
- `right`

به‌جز مقدارهای فیزیکی `left` و `right` که به ویژگی‌های فیزیکی صفحه مربوط می‌شوند، بقیهٔ مقدارها — یعنی مقدارهای `self-position` و `content-position` — مقدارهایی منطقی هستند و به حالت نوشتاری (writing mode) محتوا وابسته‌اند.

برای مثال، در CSS Grid اگر زبان شما انگلیسی باشد و `justify-content: start` تنظیم کنید، آیتم‌ها در بعد inline به سمت ابتدا حرکت می‌کنند. چون جمله‌های انگلیسی از سمت چپ صفحه شروع می‌شوند، این «ابتدا» در سمت چپ خواهد بود. اگر از زبان عربی استفاده کنید که راست‌به‌چپ است، همان مقدار `start` آیتم‌ها را به سمت راست می‌برد؛ چون جمله‌های عربی از سمت راست شروع می‌شوند.

![دو جعبه که هرکدام ۳ فرزند با ارتفاع‌های متفاوت و عرض‌های مشابه دارند. جعبهٔ اول سه فرزند با حروف A، B و C دارد که همگی چپ‌تراز شده‌اند. جعبهٔ دوم سه فرزند با حروف عربی دارد که همگی راست‌تراز شده‌اند.](writing-mode-start.png)

هر دو حالت `justify-content: start` دارند، اما جای «شروع» به دلیل حالت نوشتاری متفاوت است.

### هم‌ترازی baseline

**هم‌ترازی baseline** رابطهٔ بین خط‌های پایه (baseline) چند alignment subject در یک alignment context است. کلیدواژه‌های `baseline-position` برای هم‌ترازی خط پایهٔ جعبه‌ها در میان یک گروه از alignment subject ها استفاده می‌شوند. این مقدارها می‌توانند برای content alignment با `justify-content` و `align-content` و برای self alignment با `justify-self` و `align-self` استفاده شوند:

- `baseline`
- `first baseline`
- `last baseline`

هم‌ترازی baseline از نوع content — یعنی استفاده از مقدار baseline برای `justify-content` یا `align-content` — در روش‌های چیدمانی کار می‌کند که آیتم‌ها را در قالب ردیف می‌چینند. در این حالت، alignment subject ها با اضافه‌کردن padding داخل جعبه‌ها نسبت به هم baseline می‌شوند.

هم‌ترازی baseline از نوع self، جعبه‌ها را با اضافه‌کردن margin بیرون جعبه جابه‌جا می‌کند تا بر اساس baseline هم‌تراز شوند. self alignment برای جعبه‌های تکی با `justify-self` یا `align-self` انجام می‌شود و برای گروهی از جعبه‌ها با `justify-items` و `align-items`.

### هم‌ترازی توزیعی

**هم‌ترازی توزیعی** هم‌ترازی را به‌صورت توزیع فضا بین alignment subject ها تعریف می‌کند. کلیدواژه‌های `content-distribution` با ویژگی‌های `align-content` و `justify-content` استفاده می‌شوند. این کلیدواژه‌ها تعیین می‌کنند با فضای اضافه‌ای که بعد از نمایش alignment subject ها باقی می‌ماند چه اتفاقی بیفتد:

- `stretch`
- `space-between`
- `space-around`
- `space-evenly`

برای مثال، در Flex Layout آیتم‌ها ابتدا با `flex-start` هم‌تراز می‌شوند. در حالت نوشتاری افقی و از بالا به پایین (مثل انگلیسی) با `flex-direction: row`، آیتم‌ها از دورترین نقطهٔ چپ شروع می‌شوند و هر فضای خالی باقی‌مانده بعد از نمایش آیتم‌ها قرار می‌گیرد.

![سه مستطیل با عرض‌های متفاوت درون یک جعبه قرار دارند. همه‌ی آن‌ها به سمت چپ جعبه‌ی والد تراز شده‌اند، با فاصله‌ی حدود ۱۰ پیکسل بین خودشان و ۱۰ پیکسل بین لبه‌ی چپ اولین مستطیل و والد.](justify-content-start.png)

اگر `justify-content: space-between` را روی کانتینر flex تنظیم کنید، فضای موجود بین آیتم‌ها تقسیم می‌شود.

![سه مستطیل با عرض‌های متفاوت درون یک جعبه. اولین مستطیل به سمت چپ جعبه‌ی والد تراز شده، سومین مستطیل به سمت راست، و مستطیل وسطی به‌طور مساوی بین اولی و آخری فاصله دارد.](justify-content-space-between.png)

برای اینکه این کلیدواژه‌ها اثر کنند، باید در امتدادی که می‌خواهید آیتم‌ها را تراز کنید فضا وجود داشته باشد. اگر فاصله‌ای نباشد، چیزی برای توزیع وجود ندارد.

### مثال‌های پایه

مثال‌های زیر نشان می‌دهند که چگونه برخی از ویژگی‌های ترازبندی جعبه در [Grid](/en-US/docs/Web/CSS/Guides/Grid_layout) و [Flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) اعمال می‌شوند.

#### مثال ترازبندی در CSS Grid layout

در این مثال از Grid layout، پس از چیدمان trackهای با عرض ثابت در محور اصلی (inline)، فضای اضافی در کانتینر Grid باقی می‌ماند. این فضا با استفاده از {{cssxref("justify-content")}} توزیع می‌شود. در محور بلوکی (cross)، ترازبندی آیتم‌ها درون نواحی Grid خود با {{cssxref("align-items")}} کنترل می‌شود. اولین آیتم با تنظیم {{cssxref("align-self")}} به `center`، مقدار `align-items` تنظیم‌شده روی گروه را override می‌کند.

```html live-sample___grid-align-items
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>Three <br />has <br />extra <br />text</div>
  <div>Four</div>
  <div>Five</div>
  <div>Six</div>
</div>
```

```css hidden live-sample___grid-align-items
body {
  font: 1.2em sans-serif;
}

.box {
  border: 2px dotted rgb(96 139 168);
}

.box > * {
  padding: 20px;
  border: 2px solid rgb(96 139 168);
  border-radius: 5px;
  background-color: rgb(96 139 168 / 0.2);
}
```

```css live-sample___grid-align-items
.box {
  display: grid;
  grid-template-columns: 120px 120px 120px;
  align-items: start;
  justify-content: space-between;
}

.box :first-child {
  align-self: center;
}
```

#### مثال ترازبندی در Flexbox

در این مثال، سه آیتم flex در محور اصلی با `justify-content` و در محور عرضی با `align-items` تراز شده‌اند. اولین آیتم با تنظیم `align-self` به `center`، مقدار `align-items` گروه را override می‌کند.

```html live-sample___flex-align-items
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>Three <br />has <br />extra <br />text</div>
</div>
```

```css hidden live-sample___flex-align-items
body {
  font: 1.2em sans-serif;
}

.box {
  border: 2px dotted rgb(96 139 168);
}

.box > * {
  padding: 20px;
  border: 2px solid rgb(96 139 168);
  border-radius: 5px;
  background-color: rgb(96 139 168 / 0.2);
}
```

```css live-sample___flex-align-items
.box {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
}

.box :first-child {
  align-self: center;
}
```

## ترازبندی هنگام سرریز (overflow)

کلیدواژه‌های {{cssxref("overflow-position")}} یعنی `safe` و `unsafe` به تعریف رفتار زمانی کمک می‌کنند که یک آیتمِ در حال ترازبندی بزرگ‌تر از کانتینر ترازبندی باشد. کلیدواژه‌ی `safe` باعث می‌شود در صورت بروز سرریز ناشی از ترازبندی مشخص‌شده، آیتم به `start` تراز شود – هدف این است که از «از دست رفتن داده» جلوگیری شود، یعنی بخشی از آیتم خارج از مرزهای کانتینر ترازبندی قرار نگیرد و قابل اسکرول نباشد.

اگر `unsafe` را مشخص کنید، ترازبندی حتی اگر باعث چنین از دست رفتن داده‌ای شود، اجرا خواهد شد.

## فاصله‌های بین جعبه‌ها

مشخصات ترازبندی جعبه شامل ویژگی‌های `gap`، `row-gap` و `column-gap` نیز می‌شود. این ویژگی‌ها امکان تنظیم یک فاصله‌ی ثابت بین آیتم‌ها در یک ردیف یا ستون را در هر روش layout که آیتم‌ها را به این شکل مرتب می‌کند، فراهم می‌کنند.

ویژگی `gap` یک shorthand برای `row-gap` و `column-gap` است که به ما امکان می‌دهد این ویژگی‌ها را یکجا تنظیم کنیم:

- `row-gap`
- `column-gap`
- `gap`

در مثال زیر، یک چیدمان grid از shorthand مربوط به `gap` برای تنظیم فاصلهٔ `10px` بین ردیف‌ها (row tracks) و `2em` بین ستون‌ها (column tracks) استفاده می‌کند.

```html live-sample___grid-gap
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>Three</div>
  <div>Four</div>
  <div>Five</div>
  <div>Six</div>
</div>
```

```css hidden live-sample___grid-gap
body {
  font: 1.2em sans-serif;
}

.box {
  border: 2px dotted rgb(96 139 168);
}

.box > * {
  padding: 20px;
  border: 2px solid rgb(96 139 168);
  border-radius: 5px;
  background-color: rgb(96 139 168 / 0.2);
}
```

```css live-sample___grid-gap
.box {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 10px 2em;
}

.box :first-child {
  align-self: center;
}
```

پیاده‌سازی‌های اولیهٔ grid شامل ویژگی‌های `gap` با پیشوند `grid-` بودند. همهٔ مرورگرها از نسخه‌های بدون پیشوند پشتیبانی می‌کنند، اما احتمالاً این ویژگی‌ها را در پایگاه کد ببینید: `grid-row-gap`، `grid-column-gap` و `grid-gap`. نسخه‌های پیشونددار، نام‌های مستعار (alias) نسخه‌های بدون پیشوند هستند.

توجه داشته باشید که عوامل دیگری نیز می‌توانند فاصلهٔ بصری نمایش‌داده‌شده را افزایش دهند؛ برای مثال، استفاده از کلیدواژه‌های توزیع فضا یا افزودن margin به آیتم‌ها.

## تراز جعبه (Box alignment) بر اساس نوع چیدمان

از آنجا که ویژگی‌های تراز جعبه در CSS بسته به مشخصاتی که با آن تعامل دارند، پیاده‌سازی‌های متفاوتی دارند، برای جزئیات استفاده از این ویژگی‌ها در هر نوع چیدمان به راهنماهای زیر مراجعه کنید:

- [Box alignment in flexbox](/en-US/docs/Web/CSS/Guides/Box_alignment/In_flexbox)
- [Box alignment in CSS grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [Box alignment in multiple-column layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_multi-column_layout)
- [Box alignment for block, absolutely positioned and table layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_block_abspos_tables)

## همچنین ببینید

- [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment) module
- [Box alignment in grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [CSS display](/en-US/docs/Web/CSS/Guides/Display) module
- [CSS flex layout](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) module
- [Basic concepts of flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [Aligning items in a flex container](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items)
- [CSS grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout) module