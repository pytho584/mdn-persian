---
title: "Specificity"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Specificity"
translated_by: "n8n + AI"
---

**ویژگی (Specificity)**

**Specificity** وزنی است که مرورگر در الگوریتم cascade برای تعیین [اعلان CSS] استفاده می‌کند که بیشترین ارتباط را با یک عنصر دارد. در نتیجه، مشخص می‌کند کدام مقدار property به عنصر اعمال شود. الگوریتم specificity این وزن را از روی یک [CSS selector] محاسبه می‌کند و مقادیر به‌دست‌آمده را مقایسه می‌کند تا مشخص کند از میان اعلان‌های CSS رقیب (که در یک origin و layer یکسان قرار دارند)، کدام rule روی عنصر اعمال شود.

> [!NOTE]  
> مرورگرها specificity را **پس** از تعیین [cascade origin و importance] در نظر می‌گیرند. به عبارت دیگر، برای اعلان‌های property رقیب، specificity فقط بین selectorهایی از همان [cascade origin و layer] که اولویت را برای آن property دارد، مقایسه می‌شود. [نزدیکی محدوده (scoping proximity)] و ترتیب ظاهر شدن زمانی اهمیت پیدا می‌کنند که specificityهای selector اعلان‌های رقیب در layer با اولویت برابر باشند.

## وضوه محاسبه specificity

Specificity وزنی است که به یک اعلان CSS داده می‌شود. الگوریتم specificity این وزن را بر اساس تعداد [selectorهای هر دسته وزنی] در selectorای که با عنصر (یا pseudo-element) مطابقت دارد، محاسبه می‌کند. اگر دو یا چند اعلان مقادیر property متفاوتی برای یک عنصر ارائه دهند، مقدار اعلان در بلوک style که selector منطبق آن بیشترین وزن را دارد، اعمال می‌شود.

مقدار specificity اساساً یک مقدار سه‌ستونی از سه دسته یا وزن است: ID، CLASS و TYPE که متناظر با سه نوع selector هستند. این مقدار نشان‌دهنده شمارش اجزای selector در هر دسته وزنی است و به صورت _ID - CLASS - TYPE_ نوشته می‌شود. سه ستون با شمارش تعداد اجزای selector برای هر دسته وزنی در selectorهایی که با عنصر مطابقت دارند، ایجاد می‌شوند.

### دسته‌های وزنی selector

دسته‌های وزنی selector به ترتیب کاهش specificity در اینجا فهرست شده‌اند:

- ستون ID
  - : فقط شامل [ID selectors] مانند `#example` است. به ازای هر ID در یک selector منطبق، 1-0-0 به مقدار وزن اضافه کنید.
- ستون CLASS
  - : شامل [class selectors] مانند `.myClass`، attribute selectorهایی مانند `[type="radio"]` و `[lang|="fr"]`، و pseudo-classهایی مانند `:hover`، `:nth-of-type(3n)` و `:required` است. به ازای هر class، attribute selector یا pseudo-class در یک selector منطبق، 0-1-0 به مقدار وزن اضافه کنید.
- ستون TYPE
  - : شامل [type selectors] مانند `p`، `h1` و `td` و pseudo-elementهایی مانند `::before`، `::placeholder` و سایر selectorهای با نشانه‌گذاری دو نقطه است. به ازای هر type یا pseudo-element در یک selector منطبق، 0-0-1 به مقدار وزن اضافه کنید.
- بدون مقدار
  - : universal selector ({{CSSxRef("Universal_selectors", "*")}}) و pseudo-class {{cssxref(":where()")}} و پارامترهای آن هنگام محاسبه وزن شمارش نمی‌شوند، بنابراین مقدار آنها 0-0-0 است، اما با عناصر مطابقت دارند. این selectorها بر وزن specificity تأثیر نمی‌گذارند.

Combinatorهایی مانند {{CSSxRef("Next-sibling_combinator", "+")}}، {{CSSxRef("Child_combinator", "&gt;")}}، {{CSSxRef("Subsequent-sibling_combinator", "~")}}، [" "](/en-US/docs/Web/CSS/Reference/Selectors/Descendant_combinator) و {{CSSxRef("Column_combinator", "||")}} ممکن است selector را در انتخاب دقیق‌تر کنند، اما هیچ مقداری به وزن specificity اضافه نمی‌کنند.

### ترکیب‌کننده `&` و وزن ویژگی

ترکیب‌کننده `&` به خودی خود وزنی به ویژگی (specificity) اضافه نمی‌کند، اما قواعد تو در تو (nested rules) این کار را می‌کنند. از نظر وزن ویژگی و عملکرد، تو در تو کردن (nesting) شباهت زیادی به شبه‌کلاس `:is()` دارد.

مانند تو در تو کردن، شبه‌کلاس‌های `:is()`، `:has()` و نفی (`:not()`) نیز خودشان وزنی اضافه نمی‌کنند. اما پارامترهای داخل این سلکتورها وزن دارند. وزن ویژگی هرکدام از این شبه‌کلاس‌ها از سلکتوری در لیست سلکتورها می‌آید که بیشترین وزن را دارد. در سلکتورهای تو در تو نیز، وزن ویژگی که توسط بخش تو در تو اضافه می‌شود، برابر با سلکتوری است که در لیست سلکتورهای تو در تو (با کاما جدا شده‌اند) بیشترین وزن را دارد.

استثناهای `:not()`، `:is()`، `:has()` و تو در تو کردن CSS در ادامه توضیح داده شده‌اند.

#### سلکتور منطبق (Matching selector)

وزن ویژگی از سلکتور منطبق (matching selector) می‌آید. مثال زیر را با سه سلکتور که با کاما از هم جدا شده‌اند در نظر بگیرید:

```css
[type="password"],
input:focus,
:root #myApp input:required {
  color: blue;
}
```

سلکتور `[type="password"]` در لیست بالا با وزن ویژگی `0-1-0` اعلام `color: blue` را برای تمام فیلدهای ورودی از نوع پسورد اعمال می‌کند.

تمام ورودی‌ها، صرف‌نظر از نوع، وقتی فوکس بگیرند با دومین سلکتور لیست، یعنی `input:focus`، مطابقت می‌کنند. وزن این سلکتور `0-1-1` است: `:focus` (0-1-0) و `input` (0-0-1). اگر فیلد پسورد فوکس داشته باشد، با `input:focus` منطبق می‌شود و وزن ویژگی برای `color: blue` برابر `0-1-1` خواهد بود. وقتی فیلد پسورد فوکس ندارد، وزن همان `0-1-0` می‌ماند.

وزن ویژگی برای یک ورودی `required` که داخل عنصری با `id="myApp"` قرار دارد، `1-2-1` است (یک ID، دو شبه‌کلاس و یک نوع عنصر).

اگر فیلد پسورد با ویژگی `required` داخل عنصری با `id="myApp"` باشد، وزن ویژگی `1-2-1` خواهد بود – چه فوکس داشته باشد چه نداشته باشد. چرا وزن `1-2-1` است و مثلاً `0-1-1` یا `0-1-0` نیست؟ چون وزن ویژگی از سلکتور منطبقی می‌آید که بیشترین وزن را دارد. وزن با مقایسه مقادیر سه ستون از چپ به راست تعیین می‌شود.

```css
[type="password"] {
  /* 0-1-0 */
}
input:focus {
  /* 0-1-1 */
}
:root #myApp input:required {
  /* 1-2-1 */
}
```

### مقایسه سه‌ستونی

وقتی مقدار وزن ویژگی سلکتورهای مرتبط مشخص شد، تعداد اجزای سلکتور در هر ستون، از چپ به راست، مقایسه می‌شود.

```css
#myElement {
  color: green; /* 1-0-0  - برنده!! */
}
.bodyClass .sectionClass .parentClass [id="myElement"] {
  color: yellow; /* 0-4-0 */
}
```

ستون اول مقدار مؤلفه _ID_ است که تعداد IDها در هر سلکتور را نشان می‌دهد. اعداد ستون _ID_ سلکتورهای رقیب با هم مقایسه می‌شوند. سلکتوری که عدد بزرگتری در ستون _ID_ داشته باشد، بدون توجه به مقادیر ستون‌های دیگر، برنده است. در مثال بالا، هرچند سلکتور زرد تعداد کل مؤلفه‌های بیشتری دارد، فقط مقدار ستون اول اهمیت دارد.

اگر اعداد ستون _ID_ سلکتورهای رقیب برابر باشد، نوبت به ستون بعدی یعنی _CLASS_ می‌رسد، مانند مثال زیر:

```css
#myElement {
  color: yellow; /* 1-0-0 */
}
#myApp [id="myElement"] {
  color: green; /* 1-1-0  - برنده!! */
}
```

ستون _CLASS_ تعداد نام‌کلاس‌ها، سلکتورهای ویژگی و شبه‌کلاس‌ها را در سلکتور شمارش می‌کند. وقتی مقدار ستون _ID_ برابر است، سلکتوری که مقدار بیشتری در ستون _CLASS_ دارد، بدون توجه به مقدار ستون _TYPE_ برنده می‌شود. این را در مثال زیر می‌بینید:

```css
:root input {
  color: green; /* 0-1-1 - برنده چون ستون CLASS بزرگتر است */
}
html body main input {
  color: yellow; /* 0-0-4 */
}
```

اگر شماره‌های ستون‌های _CLASS_ و _ID_ در selectorهای رقیب یکسان باشند، ستون _TYPE_ تعیین‌کننده می‌شود. ستون _TYPE_ تعداد نوع‌های عنصر (element types) و pseudo-element‌ها در selector را نشان می‌دهد. وقتی دو ستون اول مقدار یکسانی داشته باشند، selectorای که عدد بزرگتری در ستون _TYPE_ دارد برنده می‌شود.

اگر selectorهای رقیب در هر سه ستون مقدار یکسان داشته باشند، قانون نزدیکی (proximity rule) اعمال می‌شود؛ یعنی آخرین استایلی که تعریف شده اولویت می‌گیرد.

```css
input.myClass {
  color: yellow; /* 0-1-1 */
}
:root input {
  color: green; /* 0-1-1 WINS because it comes later */
}
```

### استثناهای `:is()`، `:not()`، `:has()` و CSS nesting

pseudo-classهای تطبیق‌دهنده (matches-any) یعنی `:is()`، pseudo-class رابطه‌ای (relational) یعنی `:has()` و pseudo-class نفی (negation) یعنی `:not()` در محاسبه وزن specificity به‌عنوان pseudo-class در نظر گرفته نمی‌شوند. خودشان هیچ وزنی به معادله specificity اضافه نمی‌کنند. با این حال، پارامترهای selector که داخل پرانتز این pseudo-classها قرار می‌گیرند در الگوریتم specificity نقش دارند؛ وزن این pseudo-classها در محاسبه specificity برابر است با وزن پارامتر‌هایشان (طبق [دسته‌بندی وزن selectorها](#selector_weight_categories)).

```css
p {
  /* 0-0-1 */
}
:is(p) {
  /* 0-0-1 */
}

h2:nth-last-of-type(n + 2) {
  /* 0-1-1 */
}
h2:has(~ h2) {
  /* 0-0-2 */
}

div.outer p {
  /* 0-1-2 */
}
div:not(.inner) p {
  /* 0-1-2 */
}
```

توجه کنید که در جفت‌های CSS بالا، وزن specificity که توسط pseudo-classهای `:is()`، `:has()` و `:not()` ارائه می‌شود، مقدار پارامتر selector است، نه خود pseudo-class.

هر سه این pseudo-classها می‌توانند لیست‌های selector پیچیده (complex selector lists) – یعنی لیستی از selectorهای جدا شده با کاما – را به عنوان پارامتر بپذیرند. این ویژگی می‌تواند برای افزایش specificity یک selector به کار رود:

```css
:is(p, #fakeId) {
  /* 1-0-0 */
}
h1:has(+ h2, > #fakeId) {
  /* 1-0-1 */
}
p:not(#fakeId) {
  /* 1-0-0 */
}
div:not(.inner, #fakeId) p {
  /* 1-0-2 */
}
```

در بلوک کد CSS بالا، ما `#fakeId` را در selectorها قرار داده‌ایم. این `#fakeId` به وزن specificity هر پاراگراف `1-0-0` اضافه می‌کند.

هنگام ایجاد لیست‌های selector پیچیده با [CSS nesting](/en-US/docs/Web/CSS/Guides/Nesting)، این رفتار دقیقاً مشابه pseudo-class `:is()` است.

```css
p,
#fakeId {
  span {
    /* 1-0-1 */
  }
}
```

در بلوک کد بالا، selector پیچیده `p, #fakeId` – specificity از `#fakeId` گرفته می‌شود و همچنین از `span`، بنابراین هم برای `p span` و هم برای `#fakeId span` یک specificity معادل `1-0-1` ایجاد می‌کند. این معادل است با selector `:is(p, #fakeId) span`.

به طور کلی، بهتر است specificity را تا حد ممکن پایین نگه دارید، اما اگر به دلیلی خاص نیاز به افزایش specificity یک عنصر دارید، این سه pseudo-class می‌توانند کمک کنند.

```css
a:not(#fakeId#fakeId#fakeID) {
  color: blue; /* 3-0-1 */
}
```

در این مثال، تمام لینک‌ها آبی خواهند بود، مگر اینکه با یک اعلان (declaration) لینک که ۳ یا بیشتر ID دارد، یک مقدار رنگ که با `!important` روی `a` مشخص شده، یا اگر لینک دارای [استایل درون‌خطی (inline style)](#inline_styles) رنگی باشد، لغو شوند. اگر از چنین تکنیکی استفاده می‌کنید، یک کامنت اضافه کنید تا توضیح دهد چرا این راه‌حل موقت (hack) لازم بوده است.

### استایل‌های درون‌خطی (inline styles)

استایل‌های درون‌خطی که به یک عنصر اضافه می‌شوند (مثلاً `style="font-weight: bold;"`) همیشه هر استایل عادی را در شیوه‌نامه نویسنده (author stylesheet) لغو می‌کنند، بنابراین می‌توان آنها را دارای بالاترین specificity در نظر گرفت. استایل‌های درون‌خطی را به‌عنوان یک وزن specificity معادل `1-0-0-0` تصور کنید.

تنها راه برای لغو استایل‌های درون‌خطی استفاده از `!important` است.

بسیاری از فریم‌ورک‌ها و کتابخانه‌های جاوااسکریپت استایل‌های درون‌خطی اضافه می‌کنند. استفاده از `!important` به همراه یک selector بسیار هدفمند، مانند یک attribute selector که خود استایل درون‌خطی را هدف قرار می‌دهد، یکی از راه‌های لغو این استایل‌های درون‌خطی است.

```html
<p style="color: purple">…</p>
```

```css
p[style*="purple"] {
  color: rebeccapurple !important;
}
```

حتماً برای هر استفاده از پرچم `!important` یک کامنت اضافه کنید تا نگه‌دارنده‌های کد متوجه شوند چرا از یک ضدالگوی CSS استفاده شده است.

### استثنای `!important`

اعلان‌های CSS که با `important` علامت‌گذاری شده‌اند، هر اعلان دیگری را در همان لایه آبشاری (cascade layer) و مبدأ (origin) لغو می‌کنند. اگرچه از نظر فنی `!important` ربطی به ویژگی‌مندی (specificity) ندارد، اما مستقیماً با ویژگی‌مندی و آبشار (cascade) تعامل دارد. این پرچم ترتیب آبشاری [سبک‌نامه‌ها](/en-US/docs/Web/CSS/Guides/Cascade/Introduction) را معکوس می‌کند.

اگر اعلان‌هایی از یک مبدأ و لایه آبشاری یکسان با هم تضاد داشته باشند و یکی از مقادیر property دارای پرچم `!important` باشد، صرف‌نظر از ویژگی‌مندی، آن اعلان مهم اعمال می‌شود. وقتی اعلان‌های متضاد از یک مبدأ و لایه آبشاری با پرچم `!important` روی یک عنصر اعمال می‌شوند، اعلانی که ویژگی‌مندی بیشتری دارد اعمال می‌شود.

استفاده از `!important` برای نادیده گرفتن ویژگی‌مندی یک **رویه بد** محسوب می‌شود و باید از این کار پرهیز کرد. درک و استفاده صحیح از ویژگی‌مندی و آبشار می‌تواند نیاز به پرچم `!important` را از بین ببرد.

به‌جای استفاده از `!important` برای نادیده گرفتن CSS خارجی (مثلاً از کتابخانه‌های شخص ثالث مثل Bootstrap یا normalize.css)، اسکریپت‌های شخص ثالث را مستقیماً در [لایه‌های آبشاری](/en-US/docs/Web/CSS/Reference/At-rules/@layer) وارد کنید. اگر مجبور به استفاده از `!important` در CSS خود هستید، حتماً برای آن کامنت بگذارید تا نگه‌دارنده‌های کد بدانند چرا این اعلان مهم علامت‌گذاری شده و نباید آن را لغو کنند. اما به هیچ وجه هنگام نوشتن پلاگین یا فریم‌ورکی که توسعه‌دهندگان دیگر باید بدون توانایی کنترل آن را به کار بگیرند، از `!important` استفاده نکنید.

### استثنای `:where()`

شبه-کلاس تنظیم‌کننده ویژگی‌مندی {{cssxref(":where()")}} همیشه ویژگی‌مندی خود را به صفر، یعنی `0-0-0`، تبدیل می‌کند. این امکان را می‌دهد که سلکتورهای CSS را برای هدف‌گیری یک عنصر خاص بسیار مشخص کنید بدون اینکه ویژگی‌مندی افزایش یابد.

در ساخت CSS شخص ثالث که توسط توسعه‌دهندگانی استفاده می‌شود که به ویرایش CSS شما دسترسی ندارند، رعایت این نکته که CSS با کمترین ویژگی‌مندی ممکن نوشته شود یک رویه خوب است. برای مثال، اگر تم شما شامل CSS زیر باشد:

```css
:where(#defaultTheme) a {
  /* 0-0-1 */
  color: red;
}
```

آنگاه توسعه‌دهنده‌ای که ویجت را پیاده‌سازی می‌کند به راحتی می‌تواند رنگ لینک را فقط با استفاده از سلکتورهای نوع (type) لغو کند:

```css
footer a {
  /* 0-0-2 */
  color: blue;
}
```

### چگونه بلوک‌های `@scope` بر ویژگی‌مندی تأثیر می‌گذارند

قرار دادن یک ruleset درون یک بلوک {{cssxref("@scope")}} تأثیری بر ویژگی‌مندی سلکتور آن ندارد، صرف‌نظر از سلکتورهایی که درون [ریشه و محدوده scope](/en-US/docs/Web/CSS/Reference/At-rules/@scope#syntax) استفاده شده‌اند.
اما اگر تصمیم بگیرید که شبه-کلاس {{cssxref(":scope")}} را به صراحت اضافه کنید، باید آن را در محاسبه ویژگی‌مندی در نظر بگیرید.
`:scope` مانند همه شبه-کلاس‌های معمولی، ویژگی‌مندی 0-1-0 دارد. برای مثال:

```css
@scope (.article-body) {
  /* :scope img دارای ویژگی‌مندی 0-1-0 + 0-0-1 = 0-1-1 است */
  :scope img {
  }
}
```

برای اطلاعات بیشتر به [ویژگی‌مندی در `@scope`](/en-US/docs/Web/CSS/Reference/At-rules/@scope#specificity_in_scope) مراجعه کنید.

## نکاتی برای مدیریت سردردهای ویژگی‌مندی

به‌جای استفاده از `!important`، استفاده از لایه‌های آبشاری و به‌کارگیری وزن ویژگی‌مندی پایین در سراسر CSS خود را در نظر بگیرید تا استایل‌ها به راحتی با قوانین کمی خاص‌تر لغو شوند. استفاده از HTML معنایی به ایجاد نقاط اتصال برای اعمال استایل کمک می‌کند.

### مشخص‌کردن سلکتورها بدون افزایش ویژگی‌مندی

با مشخص کردن بخشی از سند که قبل از عنصر انتخاب‌شده به آن استایل می‌دهید، قانون خاص‌تر می‌شود. بسته به نحوه اضافه کردن آن، می‌توانید ویژگی‌مندی را کم، زیاد یا اصلاً افزایش ندهید، همانطور که در زیر نشان داده شده است:

```html
<main id="myContent">
  <h1>متن</h1>
</main>
```

```css
#myContent h1 {
  color: green; /* 1-0-1 */
}
[id="myContent"] h1 {
  color: yellow; /* 0-1-1 */
}
:where(#myContent) h1 {
  color: blue; /* 0-0-1 */
}
```

صرف‌نظر از ترتیب، heading سبز خواهد بود، چون آن rule بیشترین specificity را دارد.

#### کاهش specificity با استفاده از id

Specificity بر اساس شکل یک selector تعیین می‌شود. استفاده از `id` یک عنصر به عنوان attribute selector به جای id selector راه خوبی است برای خاص‌تر کردن یک عنصر بدون افزودن specificity بیش از حد. در مثال قبلی، selector `[id="myContent"]` به عنوان یک attribute selector برای تعیین specificity محسوب می‌شود، حتی اگر یک id را انتخاب کند.

همچنین می‌توانید `id` یا هر بخشی از یک selector را به عنوان پارامتر در pseudo-class تنظیم specificity یعنی `:where()` قرار دهید، اگر نیاز دارید selector خاص‌تر شود اما نمی‌خواهید هیچ specificity اضافه کنید.

### افزایش specificity با تکرار selector

به عنوان یک حالت خاص برای افزایش specificity، می‌توانید وزن‌های ستون‌های _CLASS_ یا _ID_ را تکرار کنید. تکرار id، class، pseudo-class یا attribute selector در یک compound selector باعث افزایش specificity هنگام override کردن selectorهای بسیار خاصی می‌شود که کنترلی روی آن‌ها ندارید.

```css
#myId#myId#myId span {
  /* 3-0-1 */
}
.myClass.myClass.myClass span {
  /* 0-3-1 */
}
```

از این کار کم استفاده کنید، اگر اصلاً استفاده می‌کنید. اگر از تکرار selector استفاده می‌کنید، حتماً CSS خود را comment کنید.

با استفاده از `:is()` و `:not()` (و همچنین `:has()`)، می‌توانید specificity را افزایش دهید حتی اگر نمی‌توانید یک `id` به عنصر والد اضافه کنید:

```css
:not(#fakeID#fakeId#fakeID) span {
  /* 3-0-1 */
}
:is(#fakeID#fakeId#fakeID, span) {
  /* 3-0-0 */
}
```

### اولویت بر CSS شخص ثالث

استفاده از cascade layers روش استاندارد برای اولویت دادن به یک مجموعه از styles بر مجموعه دیگر است؛ cascade layers این کار را بدون استفاده از specificity انجام می‌دهد! styles معمولی (غیر important) که در cascade layers وارد می‌شوند، اولویت کمتری نسبت به styles بدون layer دارند.

اگر styles از یک stylesheet می‌آیند که نمی‌توانید ویرایش کنید یا آن را درک نمی‌کنید و نیاز به override دارید، یک استراتژی این است که stylesی را که کنترل نمی‌کنید در یک cascade layer وارد کنید. Styles در layerهای بعدی اعلام شده اولویت دارند، با styles بدون layer که اولویت بالاتری نسبت به همه styles لایه‌شده از همان origin دارند.

وقتی دو selector از layerهای مختلف با یک عنصر مطابقت دارند، origin و importance اولویت دارند؛ specificity selector در stylesheet بازنده بی‌ربط است.

```css
@import "TW.css" layer();
p,
p * {
  font-size: 1rem;
}
```

در مثال بالا، تمام متن پاراگراف، از جمله محتوای تو در تو، `1rem` خواهد بود، صرف‌نظر از اینکه پاراگراف‌ها چند class name داشته باشند که با stylesheet TW مطابقت دارند.

### اجتناب و override کردن `!important`

بهترین رویکرد این است که از `!important` استفاده نکنید. توضیحات بالا در مورد specificity باید برای جلوگیری از استفاده از این پرچم و حذف آن در صورت مواجهه کمک‌کننده باشد.

برای رفع نیاز ظاهری به `!important`، می‌توانید یکی از کارهای زیر را انجام دهید:

- افزایش specificity selector مربوط به declaration که قبلاً `!important` داشته است، تا از سایر declarations بیشتر شود.
- دادن همان specificity به آن و قرار دادن آن بعد از declarationای که قرار است override کند.
- کاهش specificity selectorای که می‌خواهید override کنید.

همه این روش‌ها در بخش‌های قبلی پوشش داده شده‌اند.

اگر نمی‌توانید پرچم‌های `!important` را از یک stylesheet نویسنده حذف کنید، تنها راه حل برای override کردن styles مهم، استفاده از `!important` است. ایجاد یک [cascade layer](/en-US/docs/Web/CSS/Reference/At-rules/@layer) از overrideهای مهم declaration یک راه‌حل عالی است. دو روش برای این کار وجود دارد:

#### روش ۱

1. یک stylesheet جداگانه و کوتاه ایجاد کنید که فقط شامل declarations مهمی باشد که به طور خاص هر declaration مهمی را که نمی‌توانستید حذف کنید override می‌کند.
2. این stylesheet را به عنوان اولین import در CSS خود با استفاده از `layer()` وارد کنید، همراه با دستور `@import`، قبل از لینک به سایر stylesheets. این کار تضمین می‌کند که overrideهای مهم به عنوان اولین layer وارد شوند.

```css
@import "importantOverrides.css" layer();
```

#### روش دوم

1. در ابتدای اعلان‌های استایل‌نامه، یک لایهٔ آبشاری نام‌گذاری‌شده ایجاد کنید، به این صورت:

   ```css
   @layer importantOverrides;
   ```

2. هر بار که نیاز به override کردن یک اعلان `important` دارید، آن را درون لایهٔ نام‌گذاری‌شده اعلام کنید. فقط قوانین `important` را درون این لایه قرار دهید.

   ```css
   [id="myElement"] p {
     /* استایل‌های معمولی اینجا */
   }
   @layer importantOverrides {
     [id="myElement"] p {
       /* استایل important اینجا */
     }
   }
   ```

ویژگی (specificity) سلکتور استایل `important` درون لایه می‌تواند پایین باشد، تا زمانی که با عنصری که می‌خواهید override کنید مطابقت داشته باشد. لایه‌های معمولی باید بیرون از لایه اعلام شوند، زیرا استایل‌های لایه‌بندی‌شده اولویت کمتری نسبت به استایل‌های بدون لایه دارند.

### عدم تأثیر نزدیکی درخت

نزدیکی یک عنصر به عناصر دیگری که در یک سلکتور مشخص به آن‌ها اشاره شده است، تأثیری روی ویژگی (specificity) ندارد.

```css
body h1 {
  color: green;
}

html h1 {
  color: purple;
}
```

عناصر `<h1>` به رنگ بنفش در می‌آیند، زیرا وقتی اعلان‌ها ویژگی یکسانی دارند، سلکتور آخرین اعلان اولویت دارد.

### عناصر هدف‌گیری مستقیم در مقابل استایل‌های به‌ارث‌رسیده

استایل‌های یک عنصر که مستقیماً هدف‌گیری شده است، همیشه بر استایل‌های به‌ارث‌رسیده اولویت دارد، صرف‌نظر از ویژگی قانون به‌ارث‌رسیده. با توجه به CSS و HTML زیر:

```css
#parent {
  color: green;
}

h1 {
  color: purple;
}
```

```html
<html lang="en">
  <body id="parent">
    <h1>Here is a title!</h1>
  </body>
</html>
```

`h1` به رنگ بنفش خواهد بود، زیرا سلکتور `h1` عنصر را به طور خاص هدف قرار می‌دهد، در حالی که رنگ سبز از اعلان‌های `#parent` به ارث رسیده است.

## مثال‌ها

در CSS زیر، سه سلکتور داریم که عناصر `<input>` را برای تنظیم رنگ هدف قرار می‌دهند. برای یک input مشخص، وزن ویژگی اعلان رنگی که اولویت دارد، سلکتور منطبق با بیشترین وزن است:

```css
#myElement input.myClass {
  color: red;
} /* 1-1-1 */
input[type="password"]:required {
  color: blue;
} /* 0-2-1 */
html body main input {
  color: green;
} /* 0-0-4 */
```

اگر همه سلکتورهای بالا یک input را هدف قرار دهند، input قرمز خواهد بود، زیرا اولین اعلان بیشترین مقدار را در ستون _ID_ دارد.

آخرین سلکتور چهار جزء _TYPE_ دارد. با اینکه بیشترین مقدار عددی را دارد، اما مهم نیست چند عنصر و شبه‌عنصر در آن باشد — حتی اگر ۱۵۰ تا باشد — اجزای TYPE هرگز بر اجزای _CLASS_ اولویت ندارند. مقادیر ستون‌ها از چپ به راست مقایسه می‌شوند، زمانی که مقادیر ستون‌ها برابر باشند.

اگر سلکتور id را در مثال بالا به یک attribute selector تبدیل کنیم، دو سلکتور اول ویژگی یکسانی خواهند داشت، همانطور که در زیر نشان داده شده است:

```css
[id="myElement"] input.myClass {
  color: red;
} /* 0-2-1 */
input[type="password"]:required {
  color: blue;
} /* 0-2-1 */
```

وقتی چندین اعلان ویژگی یکسان دارند، آخرین اعلان موجود در CSS روی عنصر اعمال می‌شود. اگر هر دو سلکتور با یک `<input>` مطابقت داشته باشند، رنگ آن آبی خواهد بود.

## یادداشت‌های تکمیلی

چند نکته دربارهٔ ویژگی (specificity):

1. ویژگی فقط زمانی اعمال می‌شود که یک عنصر توسط چندین اعلان در یک لایه آبشاری یا مبدأ (origin) یکسان هدف قرار گیرد. ویژگی فقط برای اعلان‌های با اهمیت و مبدأ یکسان و [لایه آبشاری](/en-US/docs/Web/CSS/Reference/At-rules/@layer) یکسان مهم است. اگر سلکتورهای منطبق در مبدأهای متفاوتی باشند، [آبشار (cascade)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction) تعیین می‌کند که کدام اعلان اولویت دارد.

2. وقتی دو سلکتور در یک لایه آبشاری و مبدأ یکسان ویژگی یکسانی دارند، نزدیکی دامنه (scoping proximity) محاسبه می‌شود؛ مجموعه قواعدی (ruleset) که کمترین نزدیکی دامنه را دارد برنده است. برای جزئیات بیشتر و یک مثال به [چگونگی حل تعارض‌های `@scope`](/en-US/docs/Web/CSS/Reference/At-rules/@scope#how_scope_conflicts_are_resolved) مراجعه کنید.

۳. اگر نزدیکی scope (حوزه) برای هر دو selector یکسان باشد، ترتیب منبع (source order) مطرح می‌شود. وقتی همه چیز برابر است، آخرین selector برنده می‌شود.

۴. طبق قوانین CSS، [عناصر مستقیماً هدف‌گیری شده](#directly_targeted_elements_vs._inherited_styles) همیشه بر قوانینی که یک عنصر از ancestor خود به ارث می‌برد، اولویت دارند.

۵. [نزدیکی عناصر](#tree_proximity_ignorance) در درخت سند (document tree) هیچ تأثیری بر specificity ندارد.

## Specifications

## See also

- ماژول [CSS cascading and inheritance](/en-US/docs/Web/CSS/Guides/Cascade)
- [یادگیری: مدیریت تعارضات](/en-US/docs/Learn_web_development/Core/Styling_basics/Handling_conflicts#specificity_2)
- [یادگیری: لایه‌های cascade](/en-US/docs/Learn_web_development/Core/Styling_basics/Cascade_layers)
- ماژول [CSS syntax](/en-US/docs/Web/CSS/Guides/Syntax)
- [مقدمه‌ای بر syntax CSS: اعلان‌ها، rulesetها و statementها](/en-US/docs/Web/CSS/Guides/Syntax/Introduction)
- [مدیریت خطا در CSS](/en-US/docs/Web/CSS/Guides/Syntax/Error_handling)
- [At-rules](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)
- [وراثت (inheritance)](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance)
- مقادیر: [initial](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#initial_value)، [computed](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value)، [used](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#used_value) و [actual](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#actual_value)
- [Value definition syntax](/en-US/docs/Web/CSS/Guides/Values_and_units/Value_definition_syntax)
- ماژول [CSS nesting](/en-US/docs/Web/CSS/Guides/Nesting)
- [Specificity Calculator](https://specificity.keegan.st/) توسط کیگان استریت: یک وب‌سایت تعاملی برای آزمایش و درک قوانین CSS خودتان
- [SpeciFISHity](https://specifishity.com/) در specifishity.com: روشی سرگرم‌کننده برای یادگیری specificity در CSS
- تمرین [_ID-CLASS-TYPE_](https://estelle.github.io/CSS/selectors/exercises/specificity.html): یک آزمون specificity از استل وایل