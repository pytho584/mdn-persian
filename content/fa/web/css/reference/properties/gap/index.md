---
title: "gap CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/gap"
translated_by: "n8n + AI"
---

ویژگی خلاصه‌ی **`gap`** در CSS فاصله‌ها (که به آن‌ها gutter هم گفته می‌شود) را بین سطرها و ستون‌ها در containerهای [چیدمان چندستونی](/en-US/docs/Web/CSS/Guides/Multicol_layout)، [flex](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) و [grid](/en-US/docs/Web/CSS/Guides/Grid_layout) تنظیم می‌کند.

## ویژگی‌های تشکیل‌دهنده

این ویژگی خلاصه‌ای برای دو ویژگی زیر است:

- `row-gap`
- `column-gap`

## ساختار

```css
/* مقدار کلیدی */
gap: normal;

/* یک مقدار */
gap: 20px;
gap: 1em;
gap: 3vmin;
gap: 0.5cm;
gap: 16%;
gap: 100%;
gap: calc(10% + 20px);

/* دو مقدار */
gap: 20px 10px;
gap: 1em 0.5em;
gap: 3vmin 2vmax;
gap: 0.5cm 2mm;
gap: 16% 100%;
gap: 21px 82%;
gap: calc(20px + 10%) calc(10% - 5px);

/* مقادیر سراسری */
gap: inherit;
gap: initial;
gap: revert;
gap: revert-layer;
gap: unset;
```

## مقادیر

- `normal`
  - : مقداری معادل `1em` در containerهای multi-column و `0` در سایر contextها.
- `<length>`
  - : اندازهٔ فاصله به‌صورت یک مقدار `<length>` نامنفی.
- `<percentage>`
  - : اندازهٔ فاصله به‌صورت یک مقدار `<percentage>` نامنفی که نسبت به اندازهٔ [content box](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#content_area) عنصر container در آن بُعد محاسبه می‌شود.

## توضیحات

ویژگی `gap` فاصلهٔ بین ستون‌ها و سطرها را تعیین می‌کند و تأثیر آن بسته به اینکه container از نوع grid، flexbox یا چیدمان چندستونی باشد، متفاوت است.

این ویژگی خلاصه به‌صورت یک مقدار برای `<'row-gap'>` و سپس (به‌صورت اختیاری) یک مقدار برای `<'column-gap'>` نوشته می‌شود. مقدار پیش‌فرض هر دو ویژگی زیرین `normal` است، اما اگر فقط یک مقدار اعلام شود، همان مقدار برای هر دو به‌کار می‌رود. `<'row-gap'>` و `<'column-gap'>` می‌توانند به‌صورت `<length>`، `<percentage>` یا کلیدواژهٔ `normal` مشخص شوند.

مقادیر درصدی gap همیشه نسبت به اندازهٔ [content box](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#content_area) عنصر container محاسبه می‌شوند. وقتی اندازهٔ container قطعی باشد، رفتار در تمام حالت‌های چیدمان کاملاً مشخص و یکسان است.

فاصله‌های ایجادشده فضایی خالی با عرض یا ارتفاع اندازهٔ مشخص‌شده برای gap می‌سازند، درست مانند یک آیتم یا track خالی. فضای قابل مشاهده بین عناصر ممکن است با مقدار `gap` تعیین‌شده تفاوت داشته باشد، زیرا marginها، paddingها و تراز توزیع‌شده می‌توانند جدایی بین عناصر را بیشتر از آنچه `gap` تعیین کرده، افزایش دهند.

فاصله‌ها می‌توانند شامل جداکننده‌های دیداری به‌عنوان تزئینات gap باشند. اگر بین ستون‌ها، سطرها یا هردو خطوط تزئینی وجود داشته باشد، آن‌ها در وسط gap خود ظاهر می‌شوند اما تأثیری بر اندازهٔ فاصله ندارند. این خطوط تزئینی را می‌توان با استفاده از ویژگی خلاصهٔ `rule` به فضای خالی اضافه کرد.

### در چیدمان‌های grid

در [چیدمان شبکه‌ای CSS](/en-US/docs/Web/CSS/Guides/Grid_layout) ویژگی `gap` فاصلهٔ بین سطرها و ستون‌ها را تعیین می‌کند. مقدار اول فاصلهٔ بین سطرها و مقدار دوم فاصلهٔ بین ستون‌ها را مشخص می‌کند. اگر فقط یک مقدار داده شود، همان مقدار برای هر دو بعد استفاده می‌شود.

مقادیر درصدی بر اساس اندازهٔ [content box](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#content_area) عنصر container محاسبه می‌شوند. اندازه‌های درصدی چرخه‌ای (cyclic percentage sizes) برای تعیین مشارکت در [intrinsic size](/en-US/docs/Glossary/Intrinsic_Size) نسبت به صفر محاسبه می‌شوند، اما هنگام چیدمان محتوا بر اساس content box کانتینر شبکه‌ای محاسبه می‌شوند. دو مثال در بخش مثال‌ها این موضوع را با [اندازهٔ صریح container](#percentage_gap_value_and_explicit_container_size) و [اندازهٔ ضمنی container](#percentage_gap_value_and_implicit_container_size) نشان می‌دهند.

تأثیر مقادیر مثبت `gap` مانند این است که grid lineها ضخامت پیدا کرده‌اند: track شبکه‌ای بین دو grid line برابر با فضای بین شکاف‌هایی است که نمایندهٔ آن‌ها هستند. اگر یک آیتم شبکه چندین سطر یا ستون را بپوشاند، برای اندازه‌گیری track، شکاف به‌عنوان یک track اضافی، خالی و با اندازهٔ ثابت از جنس همان بعد در نظر گرفته می‌شود. برای مثال، اگر روی یک شبکهٔ ۳×۳ از باکس‌های `100px` در `100px` ویژگی `gap: 10px` تنظیم شود، آیتم شبکه‌ای که دو ستون عمودی را می‌پوشاند `210px` عرض خواهد داشت و اگر هر سه ستون را بپوشاند `320px` عرض پیدا می‌کند.

فضای بین سطرها و ستون‌های شبکه ممکن است به دلیل فضای اضافه‌شده توسط ویژگی‌های {{cssxref("justify-content")}} و {{cssxref("align-content")}} بین trackها، بزرگ‌تر از مقدار `gap` باشد.

شکاف‌ها فقط بین trackهای شبکهٔ ضمنی (implicit grid) ظاهر می‌شوند. اگر شبکه‌ای بین trackها قطعه‌قطعه شود، هیچ فاصله‌ای بین آن trackها اضافه نمی‌شود. قبل از اولین track یا بعد از آخرین track شکافی وجود ندارد و اگر یک track جمع شود، شکافی نخواهد داشت.

نسخه‌های اولیهٔ مشخصات CSS Grid این ویژگی را `grid-gap` نام‌گذاری کرده بودند. برای حفظ سازگاری با وب‌سایت‌های قدیمی، مرورگرها `grid-gap` را به‌عنوان نام مستعار `gap` می‌پذیرند.

### در Flexbox

در یک flex container، ویژگی `gap` فاصلهٔ بین آیتم‌های flex و خطوط flex را تعیین می‌کند. اینکه مقدار اول فاصلهٔ بین آیتم‌ها باشد یا بین خطوط، به جهت بستگی دارد. آیتم‌های flex بر اساس مقدار ویژگی {{cssxref("flex-direction")}} در سطرها یا ستون‌ها چیده می‌شوند. برای سطرها (مقادیر `row` (پیش‌فرض) یا `row-reverse`)، مقدار اول فاصلهٔ بین خطوط flex را مشخص می‌کند و مقدار دوم فاصلهٔ بین آیتم‌های داخل هر خط. اگر فقط یک مقدار داده شود، برای هر دو بعد استفاده می‌شود.

برای ستون‌ها (`column` یا `column-reverse`)، مقدار اول فاصلهٔ بین آیتم‌های flex درون یک خط flex را مشخص می‌کند و مقدار دوم فاصلهٔ بین خطوط flex را. باز هم اگر فقط یک مقدار داده شود، برای هر دو بعد استفاده می‌شود.

### در چیدمان چندستونی

در [چیدمان چندستونی CSS](/en-US/docs/Web/CSS/Guides/Multicol_layout)، این ویژگی فاصلهٔ بین ستون‌ها و ردیف‌های ستونی را تعیین می‌کند. مقدار اول فاصلهٔ بین جعبه‌های ستونی مجاور را مشخص می‌کند، در حالی که مقدار دوم اندازهٔ فاصلهٔ بین ردیف‌های ستونی را مشخص می‌کند (اگر چند ردیف توسط ویژگی {{cssxref("column-height")}} ایجاد شده باشند).

## مثال‌ها

### چیدمان Flex

#### HTML

```html
<div id="flexbox">
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
#flexbox {
  display: flex;
  flex-wrap: wrap;
  width: 300px;
  gap: 20px 5px;
}

#flexbox > div {
  border: 1px solid green;
  background-color: lime;
  flex: 1 1 auto;
  width: 100px;
  height: 50px;
}
```

### چیدمان Grid

#### HTML

```html
<div id="grid">
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
#grid {
  display: grid;
  height: 200px;
  grid-template: repeat(3, 1fr) / repeat(3, 1fr);
  gap: 20px 5px;
}

#grid > div {
  border: 1px solid green;
  background-color: lime;
}
```

### چیدمان چندستونی

#### HTML

```html
<p class="content-box">
  This is some multi-column text with a 40px column gap created with the CSS
  <code>gap</code> property. Don't you think that's fun and exciting? I sure do!
</p>
```

#### CSS

```css
.content-box {
  column-count: 3;
  gap: 40px;
}
```

### مقدار درصدی gap و اندازه صریح container

اگر container دارای اندازه‌ای ثابت (fixed size) باشد، محاسبات مقدار درصدی gap بر اساس اندازه خود container انجام می‌شود. بنابراین رفتار gap در تمام چیدمان‌ها یکسان خواهد بود. در مثال زیر دو container وجود دارد، یکی با چیدمان grid و دیگری با چیدمان flex. هر container پنج عنصر فرزند قرمز رنگ ۲۰ در ۲۰ پیکسلی دارد. ارتفاع هر دو container به‌طور صریح با `height: 200px` برابر با ۲۰۰ پیکسل تنظیم شده و gap با `gap: 12.5% 0` مقداردهی شده است.

```html
<span>Grid</span>
<div id="grid">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
</div>
<span>Flex</span>
<div id="flex">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
</div>
```

```css hidden
body > div {
  background-color: #cccccc;
  width: 200px;
  flex-flow: column;
}
```

```css
#grid {
  display: inline-grid;
  height: 200px;
  gap: 12.5% 0;
}

#flex {
  display: inline-flex;
  height: 200px;
  gap: 12.5% 0;
}

#grid > div,
#flex > div {
  background-color: coral;
  width: 20px;
  height: 20px;
}
```

حالا با استفاده از [برگه Inspector در ابزارهای توسعه‌دهنده وب](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/open_the_inspector/index.html) عناصر grid و flex را بررسی کنید. برای دیدن gapهای واقعی، نشانگر موس را روی تگ‌های `<div id="grid">` و `<div id="flex">` در Inspector نگه دارید. متوجه خواهید شد که gap در هر دو حالت یکسان و برابر ۲۵ پیکسل است.

### مقدار درصدی gap و اندازه ضمنی container

اگر اندازه به‌طور صریح روی container تنظیم نشده باشد، gap درصدی در چیدمان‌های grid و flex رفتار متفاوتی خواهد داشت. در مثال زیر ارتفاع containerها به‌طور صریح مشخص نشده است.

```html hidden
<span>Grid</span>
<div id="grid">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
</div>
<span>Flex</span>
<div id="flex">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
</div>
```

```css hidden
body > div {
  background-color: #cccccc;
  width: 200px;
}

#grid {
  display: inline-grid;
  gap: 12.5% 0;
}

#flex {
  display: inline-flex;
  gap: 12.5% 0;
  flex-flow: column;
}

#grid > div,
#flex > div {
  background-color: coral;
  width: 20px;
  height: 20px;
}
```

در چیدمان grid، gap درصدی تأثیری در ارتفاع واقعی grid ندارد. ارتفاع container با فرض gap صفر (`0px`) محاسبه می‌شود، بنابراین ارتفاع واقعی ۱۰۰ پیکسل (۵ × ۲۰px) به‌دست می‌آید. سپس gap درصدی واقعی با استفاده از ارتفاع content box محاسبه می‌شود: `12.5px` (۱۲.۵٪ × ۱۰۰px). این gap درست قبل از رندر شدن اعمال می‌شود. بنابراین ارتفاع grid همچنان ۱۰۰ پیکسل باقی می‌ماند، اما به دلیل gap درصدی که بعداً اضافه می‌شود، سرریز رخ می‌دهد.

در چیدمان flex، gap درصدی همیشه مقدار صفر را نتیجه می‌دهد.

## همچنین ببینید

- [row-gap](/en-US/docs/Web/CSS/row-gap)
- [column-gap](/en-US/docs/Web/CSS/column-gap)
- [مفاهیم پایه‌ای گرید: gutters](/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts#gutters)
- ماژول [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment)
- ماژول [CSS flexible box layout](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)
- ماژول [CSS grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout)
- ماژول [CSS multi-column layout](/en-US/docs/Web/CSS/Guides/Multicol_layout)