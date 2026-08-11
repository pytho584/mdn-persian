---
title: "Using CSS custom properties (variables)"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties"
translated_by: "n8n + AI"
---

## استفاده از ویژگی‌های سفارشی CSS (متغیرها)

**ویژگی‌های سفارشی** (که گاهی به‌عنوان **متغیرهای CSS** یا **متغیرهای آبشاری** هم شناخته می‌شوند) موجودیت‌هایی هستند که توسط توسعه‌دهندهٔ CSS تعریف می‌شوند و مقادیر مشخصی را برای استفادهٔ مجدد در سراسر یک سند نمایش می‌دهند. این ویژگی‌ها یا با استفاده از at-rule `@property` یا با [نحو اختصاصی ویژگی‌های سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) (مثلاً `--primary-color: blue;`) تعریف می‌شوند. برای دسترسی به ویژگی‌های سفارشی از تابع `var()` استفاده می‌شود (مثلاً `color: var(--primary-color);`).

وب‌سایت‌های پیچیده حجم بسیار زیادی از CSS دارند و این اغلب به تکرار مقادیر CSS منجر می‌شود. مثلاً دیدن یک رنگ مشخص در صدها نقطهٔ مختلف از شیوه‌نامه‌ها رایج است. تغییر رنگی که در جاهای متعددی تکرار شده، نیاز به جستجو و جایگزینی در تمام قوانین و فایل‌های CSS دارد. ویژگی‌های سفارشی این امکان را می‌دهند که یک مقدار در یک جا تعریف شود و در چندین جای دیگر به آن ارجاع داده شود تا کار با آن آسان‌تر شود. مزیت دیگر خوانایی و معناداری است. برای مثال، `--main-text-color` خیلی راحت‌تر از رنگ هگزادسیمال `#00ff00` قابل درک است، به‌خصوص اگر آن رنگ در زمینه‌های مختلفی استفاده شود.

ویژگی‌های سفارشی که [با دو خط تیره (`--`) تعریف می‌شوند](/en-US/docs/Web/CSS/Reference/Properties/--*) تحت تأثیر [آبشار (cascade)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction) هستند و مقدار خود را از والد به ارث می‌برند. at-rule `@property` کنترل بیشتری روی ویژگی سفارشی می‌دهد و به شما اجازه می‌دهد مشخص کنید که آیا مقدار از والد به ارث می‌رسد، مقدار اولیه چیست، و چه محدودیت‌هایی برای نوع داده باید اعمال شود.

> **نکته:** متغیرها در media queries و container queries کار نمی‌کنند.
> می‌توانید از تابع `var()` در هر بخشی از یک مقدار در هر property روی یک عنصر استفاده کنید.
> نمی‌توانید از `var()` برای نام propertyها، انتخاب‌گرها (selector) یا هر چیزی غیر از مقادیر property استفاده کنید؛ یعنی نمی‌توانید از آن در media query یا container query استفاده کنید.

## اعلام ویژگی‌های سفارشی

در CSS، می‌توانید یک ویژگی سفارشی را با استفاده از پیشوند دو خط تیره برای نام property، یا با استفاده از at-rule `@property` اعلام کنید. بخش‌های زیر نحوهٔ استفاده از این دو روش را توضیح می‌دهند.

### استفاده از پیشوند دو خط تیره (`--`)

یک ویژگی سفارشی که با دو خط تیره پیشوندگذاری شده است، با `--` شروع می‌شود و سپس نام property (مثلاً `--my-property`) و یک مقدار property که می‌تواند هر [مقدار معتبر CSS](/en-US/docs/Learn_web_development/Core/Styling_basics/Values_and_units) باشد، قرار می‌گیرد. مانند هر property دیگری، این داخل یک ruleset نوشته می‌شود. مثال زیر نحوهٔ ایجاد یک ویژگی سفارشی به نام `--main-bg-color` را با استفاده از مقدار `brown` (یک [رنگ نام‌گذاری شده](/en-US/docs/Web/CSS/named-color)) نشان می‌دهد:

```css
section {
  --main-bg-color: brown;
}
```

انتخاب‌گر (selector) که به ruleset داده شده است (در مثال بالا عناصر `<section>`) محدوده‌ای را مشخص می‌کند که در آن ویژگی سفارشی قابل استفاده است. به همین دلیل، یک روش رایج این است که ویژگی‌های سفارشی را روی شبه‌کلاس `:root` تعریف کنید تا بتوان به صورت سراسری به آن ارجاع داد:

```css
:root {
  --main-bg-color: brown;
}
```

این همیشه لازم نیست؛ ممکن است دلیل خوبی برای محدود کردن دامنهٔ ویژگی‌های سفارشی خود داشته باشید.

> **نکته:** نام ویژگی‌های سفارشی به حروف بزرگ و کوچک حساس هستند — `--my-color` و `--My-color` دو ویژگی سفارشی جداگانه در نظر گرفته می‌شوند.

### استفاده از at-rule `@property`

at-rule `@property` به شما امکان می‌دهد در تعریف یک ویژگی سفارشی دقیق‌تر عمل کنید؛ می‌توانید یک نوع داده را به property مرتبط کنید، مقادیر پیش‌فرض تعیین کنید، و نحوهٔ ارث‌بری را کنترل کنید. مثال زیر یک ویژگی سفارشی به نام `--logo-color` ایجاد می‌کند که انتظار یک مقدار از نوع `<color>` را دارد:

```css
@property --logo-color {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

اگر می‌خواهید خاصیت‌های سفارشی (custom properties) را در JavaScript تعریف کنید یا با آن‌ها کار کنید — به جای تعریف مستقیم در CSS — یک API مخصوص این کار وجود دارد.  
می‌توانید نحوه‌ی کار این API را در صفحه‌ی [CSS Properties and Values API](/en-US/docs/Web/API/CSS_Properties_and_Values_API) مطالعه کنید.

### ارجاع به خاصیت‌های سفارشی با `var()`

روش تعریف خاصیت سفارشی هرچه که باشد، برای استفاده از آن‌ها باید خاصیت را درون تابع {{cssxref("var()")}} به‌جای یک مقدار استاندارد قرار دهید:

```css
details {
  background-color: var(--main-bg-color);
}
```

## اولین قدم‌ها با خاصیت‌های سفارشی

بیایید با یک HTML ساده شروع کنیم که می‌خواهیم استایل‌هایی به آن اضافه کنیم. یک `<div>` به عنوان کانتینر داریم که شامل چند المان فرزند است، بعضی از آن‌ها خودشان فرزندانی دارند:

```html
<div class="container">
  <div class="one">
    <p>One</p>
  </div>
  <div class="two">
    <p>Two</p>
    <div class="three">
      <p>Three</p>
    </div>
  </div>
  <input class="four" placeholder="Four" />
  <textarea class="five">Five</textarea>
</div>
```

از CSS زیر استفاده می‌کنیم تا چند المان مختلف را بر اساس کلاس‌هایشان استایل دهیم (برخی قوانین layout برای تمرکز روی رنگ‌ها در اینجا نشان داده نشده‌اند). بسته به کلاس‌ها، به المان‌ها رنگ‌های `teal` یا `pink` می‌دهیم:

```css hidden
/* تنظیم فونت، حاشیه و padding */
body,
textarea,
::placeholder {
  font-family: sans-serif;
  color: white;
}

div,
input,
textarea {
  border: 2px black solid;
  padding: 4px;
  margin: 4px;
}

.container {
  display: grid;
  gap: 10px;
}
```

```css
/* برای هر کلاس، رنگ‌هایی تنظیم می‌کنیم */
.one {
  background-color: teal;
}

.two {
  color: black;
  background-color: pink;
}

.three {
  color: white;
  background-color: teal;
}

.four {
  background-color: teal;
}

.five {
  background-color: teal;
}
```

این کد نتیجه‌ی زیر را تولید می‌کند:

{{EmbedLiveSample("First_steps_with_custom_properties",600,360)}}

اینجا فرصت خوبی است تا از خاصیت‌های سفارشی برای جایگزینی مقادیر تکراری در این قوانین استفاده کنیم. بعد از تعریف `--main-bg-color` در اسکوپ `.container` و ارجاع به مقدار آن در چندین جا، استایل‌های به‌روز شده به این شکل درمی‌آیند:

```css
/* --main-bg-color را اینجا تعریف می‌کنیم */
.container {
  --main-bg-color: teal;
}

/* برای هر کلاس، رنگ‌هایی تنظیم می‌کنیم */
.one {
  background-color: var(--main-bg-color);
}

.two {
  color: black;
  background-color: pink;
}

.three {
  color: white;
  background-color: var(--main-bg-color);
}

.four {
  background-color: var(--main-bg-color);
}

.five {
  background-color: var(--main-bg-color);
}
```

## استفاده از pseudo-class :root

برای بعضی اعلان‌های CSS می‌توان این مقادیر را در سطح بالاتر cascade تعریف کرد و اجازه داد ارث‌بری (inheritance) خودکار CSS مشکل را حل کند. اما در پروژه‌های غیرساده این کار همیشه ممکن نیست. با تعریف یک خاصیت سفارشی روی pseudo-class {{cssxref(":root")}} و استفاده از آن در سراسر سند، یک توسعه‌دهنده CSS می‌تواند تکرار را کاهش دهد:

```css
/* --main-bg-color را اینجا تعریف می‌کنیم */
:root {
  --main-bg-color: teal;
}

/* برای هر کلاس، رنگ‌هایی تنظیم می‌کنیم */
.one,
.three,
.four,
.five {
  background-color: var(--main-bg-color);
}

.two {
  color: black;
  background-color: pink;
}
```

این کار به همان نتیجه‌ی مثال قبلی می‌رسد، اما یک اعلان واحد و استاندارد برای مقدار خاصیت مورد نظر (`--main-bg-color: teal;`) فراهم می‌کند که اگر بخواهید بعداً مقدار را در کل پروژه تغییر دهید، بسیار مفید است.

## ارث‌بری خاصیت‌های سفارشی

یک خاصیت سفارشی که با دو خط تیره `--` تعریف شده باشد (به جای `@property`) همیشه مقدار والد خود را به ارث می‌برد. این موضوع در مثال زیر نشان داده شده است:

```html live-sample___dash-custom-property-inheritance
<div class="one">
  <p>One</p>
  <div class="two">
    <p>Two</p>
    <div class="three"><p>Three</p></div>
    <div class="four"><p>Four</p></div>
  </div>
</div>
```

```css hidden live-sample___dash-custom-property-inheritance
div {
  color: black;
  font-family: sans-serif;
  width: 75%;
  height: 80%;
  margin: 4px;
  border: 2px black solid;
  display: inline-block;
}

p {
  margin: 0;
}

.one {
  height: 250px;
}

.two {
  color: white;
  height: 80%;
}

.three {
  color: black;
  height: 40%;
}

.four {
  color: white;
  height: 40%;
}
```

```css live-sample___dash-custom-property-inheritance
div {
  background-color: var(--box-color);
}

.two {
  --box-color: teal;
}

.three {
  --box-color: pink;
}
```

نتایج `var(--box-color)` با توجه به ارث‌بری به این صورت است:

- `class="one"`: _مقدار نامعتبر_، که مقدار پیش‌فرض یک خاصیت سفارشی تعریف‌شده به این روش است
- `class="two"`: `teal`
- `class="three"`: `pink`
- `class="four"`: `teal` (از والد خود به ارث برده)

یک نکته‌ی مهم که مثال‌های بالا نشان می‌دهند این است که خاصیت‌های سفارشی (custom properties) دقیقاً مثل متغیرهای زبان‌های برنامه‌نویسی دیگر رفتار نمی‌کنند. مقدار در جایی که نیاز است محاسبه می‌شود، نه اینکه ذخیره و در جاهای دیگر stylesheet استفاده مجدد شود. مثلاً نمی‌توانید مقداری را برای یک خاصیت تعیین کنید و انتظار داشته باشید که آن مقدار را در قانون مربوط به فرزند یک خواهر یا برادر (sibling descendant) بازیابی کنید. خاصیت فقط برای selector منطبق و فرزندان آن تنظیم می‌شود.

### استفاده از `@property` برای کنترل ارث‌بری

قانون at-rule با نام `@property` به شما اجازه می‌دهد به صراحت مشخص کنید که آیا یک خاصیت ارث‌بری دارد یا نه. مثال زیر یک خاصیت سفارشی با استفاده از `@property` ایجاد می‌کند. ارث‌بری غیرفعال شده، یک نوع داده‌ی {{cssxref("&lt;color&gt;")}} تعریف شده، و یک مقدار اولیه‌ی `teal` وجود دارد.

عنصر والد مقدار `--box-color` را به `green` تنظیم کرده و از `--box-color` به عنوان مقدار رنگ پس‌زمینه‌اش استفاده می‌کند. عنصر فرزند نیز از `background-color: var(--box-color)` استفاده می‌کند و اگر ارث‌بری فعال بود (یا اگر با syntax دو خط تیره تعریف شده بود)، انتظار داشتیم رنگ `green` داشته باشد.

```html live-sample___at-property-inheritance
<div class="parent">
  <p>Parent element</p>
  <div class="child">
    <p>Child element with inheritance disabled for --box-color.</p>
  </div>
</div>
```

```css hidden live-sample___at-property-inheritance
div {
  color: white;
  font-family: sans-serif;
  width: 200px;
  height: 200px;
  margin: 4px;
  padding: 8px;
  border: 2px black solid;
  display: inline-block;
}
```

```css live-sample___at-property-inheritance
@property --box-color {
  syntax: "<color>";
  inherits: false;
  initial-value: teal;
}

.parent {
  --box-color: green;
  background-color: var(--box-color);
}

.child {
  width: 80%;
  height: 40%;
  background-color: var(--box-color);
}
```

از آنجا که `inherits: false;` در قانون at تعیین شده و هیچ مقداری برای خاصیت `--box-color` در محدوده‌ی `.child` اعلام نشده است، به جای `green` که از والد به ارث می‌رسید، مقدار اولیه‌ی `teal` استفاده می‌شود:

## مقادیر جایگزین (fallback) برای خاصیت‌های سفارشی

می‌توانید برای خاصیت‌های سفارشی با استفاده از تابع `var()` و `initial-value` در قانون `@property` مقادیر جایگزین تعریف کنید.

> **نکته:** مقادیر جایگزین برای رفع مشکلات سازگاری در مرورگرهایی که از خاصیت‌های سفارشی CSS پشتیبانی نمی‌کنند استفاده نمی‌شوند، زیرا در آن صورت مقدار جایگزین کمکی نمی‌کند. مقادیر جایگزین مواردی را پوشش می‌دهند که مرورگر از خاصیت‌های سفارشی CSS پشتیبانی می‌کند و در صورت تعریف‌نشدن متغیر مورد نظر یا نامعتبر بودن آن، می‌تواند از یک مقدار متفاوت استفاده کند.

### تعریف مقادیر جایگزین در تابع `var()`

با استفاده از تابع [`var()`](/en-US/docs/Web/CSS/Reference/Values/var) می‌توانید چندین **مقدار جایگزین** برای زمانی که متغیر مشخص شده هنوز تعریف نشده است تعریف کنید. این کار هنگام کار با [عناصر سفارشی (Custom Elements)](/en-US/docs/Web/API/Web_components/Using_custom_elements) و [Shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM) مفید است.

اولین آرگومان تابع، نام خاصیت سفارشی (custom property) است. آرگومان دوم یک مقدار جایگزین (fallback value) اختیاری است که وقتی خاصیت سفارشی ارجاع‌شده نامعتبر باشد، به‌عنوان مقدار جایگزین استفاده می‌شود.

این تابع دو پارامتر می‌پذیرد و هر چیزی که بعد از اولین کاما قرار بگیرد را به‌عنوان پارامتر دوم در نظر می‌گیرد. اگر پارامتر دوم نامعتبر باشد، جایگزین (fallback) هم کار نمی‌کند. مثال:

```css
.one {
  /* اگر --my-var تعریف نشده باشد، قرمز */
  color: var(--my-var, red);
}

.two {
  /* اگر --my-var و --my-background تعریف نشده باشند، صورتی */
  color: var(--my-var, var(--my-background, pink));
}

.three {
  /* نامعتبر: "--my-background, pink" */
  color: var(--my-var, --my-background, pink);
}
```

استفاده از یک خاصیت سفارشی به‌عنوان fallback، همان‌طور که در مثال دوم دیده می‌شود (`var(--my-var, var(--my-background, pink))`)، روش درست برای ارائه چندین fallback با `var()` است. البته باید از تأثیر این روش روی عملکرد آگاه باشید، چون解析 متغیرهای تو در تو زمان بیشتری می‌برد.

> **نکته:** ساختار fallback، مانند خاصیت‌های سفارشی، اجازه کاما می‌دهد. برای مثال، `var(--foo, red, blue)` یک fallback برابر با `red, blue` تعریف می‌کند — هر چیزی بین اولین کاما و انتهای تابع به‌عنوان مقدار fallback در نظر گرفته می‌شود.

### جایگزین با استفاده از initial-value در @property

علاوه بر `var()`، مقدار `initial-value` که در at-rule `@property` تعریف می‌شود نیز می‌تواند به‌عنوان مکانیزم جایگزین استفاده شود. در واقع در بخش [استفاده از @property برای کنترل وراثت](#using_property_to_control_inheritance) این را دیده‌ایم.

مثال زیر مقدار اولیه `--box-color` را با استفاده از at-rule `@property` به `teal` تنظیم می‌کند. در مجموعه قوانین (ruleset) بعد از آن، می‌خواهیم `--box-color` را به `pink` تنظیم کنیم، اما در نام مقدار یک اشتباه تایپی وجود دارد. همین وضعیت برای `<div>` سوم هم صادق است که از `2rem` برای خاصیت سفارشی استفاده کرده‌ایم، در حالی که انتظار یک [`<color>` value](/en-US/docs/Web/CSS/Reference/Values/color_value) معتبر را دارد. هر دو `2rem` و `peenk` مقادیر رنگی نامعتبر هستند، بنابراین مقدار اولیه `teal` اعمال می‌شود:

```css
@property --box-color {
  syntax: "<color>";
  initial-value: teal;
  inherits: false;
}

.one {
  --box-color: pink;
  background-color: var(--box-color);
}

.two {
  --box-color: peenk;
  background-color: var(--box-color);
}

.three {
  --box-color: 2rem;
  background-color: var(--box-color);
}
```

## خاصیت‌های سفارشی نامعتبر

هر خاصیت CSS مجموعه‌ای از [مقادیر معتبر](/en-US/docs/Learn_web_development/Core/Styling_basics/Values_and_units) تعریف‌شده دارد. اگر تلاش کنید مقداری به یک خاصیت بدهید که خارج از مجموعه مقادیر معتبر آن باشد، آن مقدار _نامعتبر_ در نظر گرفته می‌شود.

وقتی مرورگر با یک مقدار نامعتبر برای یک خاصیت معمولی CSS مواجه می‌شود (مثلاً مقدار `16px` برای خاصیت {{cssxref("color")}})، آن اعلان (declaration) را دور می‌ریزد و عناصر مقادیری را می‌گیرند که اگر آن اعلان وجود نداشت، می‌گرفتند. در مثال زیر می‌بینیم وقتی یک اعلان معمولی CSS نامعتبر است چه اتفاقی می‌افتد: `color: 16px;` دور ریخته می‌شود و به جای آن قانون قبلی `color: blue` اعمال می‌شود:

```html
<p>This paragraph is initially black.</p>
```

```css
p {
  font-weight: bold;
  color: blue;
}

p {
  /* اوه، یک رنگ معتبر نیست */
  color: 16px;
}
```

اما وقتی مقادیر خاصیت‌های سفارشی (custom properties) تجزیه می‌شوند، مرورگر هنوز نمی‌داند این مقادیر کجا استفاده خواهند شد، بنابراین مجبور است تقریباً همهٔ مقادیر را **معتبر** در نظر بگیرد.  
متأسفانه این مقادیر معتبر می‌توانند از طریق تابع `var()` در جایی استفاده شوند که شاید منطقی نباشند. خاصیت‌ها و متغیرهای سفارشی می‌توانند باعث ایجاد دستورات CSS نامعتبر شوند و به مفهوم **معتبر در زمان محاسبه** (valid at computed time) منجر شوند.

وقتی مرورگر با یک جایگزینی `var()` نامعتبر مواجه شود، مقدار [اولیه](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#initial_value) یا [ارث‌بری](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Inheritance) آن خاصیت استفاده می‌شود.  
این مثال دقیقاً مشابه مثال قبلی است، با این تفاوت که از یک خاصیت سفارشی استفاده می‌کنیم.

مرورگر مقدار `--text-color` را به جای `var(--text-color)` قرار می‌دهد، اما `16px` مقدار معتبری برای خاصیت `color` نیست.  
پس از جایگزینی، خاصیت منطقی نیست، بنابراین مرورگر این وضعیت را در دو مرحله مدیریت می‌کند:

1. بررسی می‌کند که آیا خاصیت `color` قابل ارث‌بری است؟ بله، اما این `<p>` هیچ والدینی با خاصیت `color` تنظیم شده ندارد. پس به مرحله بعد می‌رویم.
2. مقدار را به **مقدار اولیه پیش‌فرض** آن که سیاه است تنظیم می‌کند.

```html live-sample___invalid-custom-property
<p>This paragraph is initially black.</p>
```

```css live-sample___invalid-custom-property
:root {
  --text-color: 16px;
}

p {
  font-weight: bold;
  color: blue;
}

p {
  color: var(--text-color);
}
```

برای چنین مواردی، قانون at-rule `@property` می‌تواند با امکان تعریف مقدار اولیهٔ خاصیت، از نتایج غیرمنتظره جلوگیری کند:

```html live-sample___invalid-custom-property-fallbacks
<p>This paragraph is initially black.</p>
```

```css live-sample___invalid-custom-property-fallbacks
@property --text-color {
  syntax: "<color>";
  inherits: false;
  initial-value: teal;
}

:root {
  --text-color: 16px;
}

p {
  font-weight: bold;
  color: blue;
}

p {
  color: var(--text-color);
}
```

## مقادیر در JavaScript

برای استفاده از مقادیر خاصیت‌های سفارشی در JavaScript، مانند خاصیت‌های استاندارد عمل می‌شود.

```js
// get variable from inline style
element.style.getPropertyValue("--my-var");

// get variable from wherever
getComputedStyle(element).getPropertyValue("--my-var");

// set variable on inline style
element.style.setProperty("--my-var", jsVar + 4);
```

## همچنین ببینید

- قانون at-rule [`@property`](/en-US/docs/Web/CSS/@property)
- تابع [`var()`](/en-US/docs/Web/CSS/Reference/Values/var)
- [ماژول خاصیت‌های سفارشی CSS برای متغیرهای آبشاری](/en-US/docs/Web/CSS/Guides/Cascading_variables)
- [نحو خاصیت‌های سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*)
- [API خاصیت‌ها و مقادیر CSS](/en-US/docs/Web/API/CSS_Properties_and_Values_API)