---
title: "CSS property value processing"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing"
translated_by: "n8n + AI"
---

برای هر عنصر در درخت سند، مرورگر به هر ویژگی CSS که برای آن عنصر اعمال می‌شود یک مقدار اختصاص می‌دهد. مقدار نهایی نمایش داده شده هر ویژگی CSS برای یک عنصر یا box خاص، نتیجه محاسبه‌ای مبتنی بر تعاریف stylesheet، وراثت، cascade (آبشار)، وابستگی‌ها، تبدیل واحدها و محیط نمایش است. این راهنما مروری بر مراحل پردازش برای تعیین چگونگی نمایش نهایی هر مقدار CSS با بررسی مفاهیم کلیدی مانند specified (مشخص‌شده)، computed (محاسبه‌شده)، used (استفاده‌شده) و actual (واقعی) values ارائه می‌دهد.

هر استایلی که به یک عنصر یا شبه‌عنصر اعمال می‌شود بر اساس یک اعلامیه (declaration) ویژگی CSS واحد است. هر ویژگی CSS فقط یک مقدار دارد. مقدار اعمال‌شده توسط [مقادیر آبشاری (cascaded values)](#cascaded_value) همه اعلامیه‌های آن ویژگی که برای آن عنصر یا شبه‌عنصر اعمال می‌شوند تعیین می‌شود، به طوری که مقدار واحد اعمال‌شده از اعلامیه‌ای می‌آید که بالاترین رتبه را در [ترتیب مرتب‌سازی cascade (cascade sorting order)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#cascading_order) بر اساس [الگوریتم cascade (cascade algorithm)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction) دارد.

وقتی چندین [مقدار اعلام‌شده (declared value)](#declared_value) با چندین اعلامیه وجود داشته باشد که مقادیر یکسان یا متفاوتی از ویژگی را برای یک عنصر ارائه می‌دهند، هر مقدار ویژگی همچنان باید از یک جفت نام-مقدار ویژگی واحد بیاید، زیرا از هر ویژگی فقط یک مقدار اعمال می‌شود، حتی اگر آن مقدار یک لیست با کاما جدا شده باشد.

برای تعیین اینکه کدام [مقدار اعلام‌شده (declared value)](#declared_value) اعمال می‌شود، عامل کاربر (user agent) تمام استایل‌ها را از منابع مختلف مانند استایل‌های inline و استایل‌شیت‌های داخلی و خارجی جمع‌آوری و پردازش می‌کند.

cascade تعیین می‌کند که وقتی چندین استایل متضاد یک عنصر را هدف قرار می‌دهند، کدام مقدار باید اعمال شود. [الگوریتم cascade (cascade algorithm)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#cascading_order) تعریف می‌کند که عامل‌های کاربر چگونه مقادیر ویژگی را از منابع، scopeها و/یا [لایه‌ها (layers)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#cascade_layers) مختلف ترکیب می‌کنند. وقتی یک selector با یک عنصر مطابقت دارد، [مقدار اعلام‌شده (declared value)](#declared_value) آن ویژگی از [منبع (origin)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#origin_types) با بالاترین اولویت اعمال می‌شود، حتی اگر یک selector از [منبع (origin)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#origin_types) یا [لایه (layer)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#cascade_layers) با اولویت پایین‌تر [اختصاصیت (specificity)](/en-US/docs/Web/CSS/Guides/Cascade/Specificity) بیشتری داشته باشد.

برخی ویژگی‌ها مقادیر خود را از عناصر والد به ارث می‌برند، مگر اینکه صریحاً بازنویسی شوند. [وراثت (inheritance)](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance) ممکن است زمانی رخ دهد که اطلاعات استایلی برای یک ویژگی خاص روی یک عنصر وجود نداشته باشد. اگر ویژگی ارث‌بری باشد، مقدار آن به [مقدار محاسبه‌شده (computed value)](#computed_value) عنصر والد تنظیم می‌شود. اگر ویژگی ارث‌بری نباشد، مقدار آن به [مقدار اولیه (initial value)](#initial_value) آن عنصر تنظیم می‌شود.

پس از اعمال قوانین [آبشاری (cascading)](#cascading) و مقداردهی پیش‌فرض به صورت گام‌به‌گام، مرورگر اطمینان حاصل می‌کند که نمایش بصری با CSS پردازش‌شده مطابقت دارد.

## مرور کلی پردازش

پیش از ورود به مراحل تکی مقدار، مهم است که سه مرحله اصلی که در پردازش مقدار رخ می‌دهند را درک کنیم: [فیلتر کردن (filtering)](#filtering)، [آبشاری کردن (cascading)](#cascading) و [پیش‌فرض‌سازی (defaulting)](#defaulting).

### فیلتر کردن (Filtering)

**فیلتر کردن** فرایند شناسایی تمام اعلامیه‌هایی است که برای هر عنصر اعمال می‌شوند. یک اعلامیه برای یک عنصر اعمال می‌شود فقط اگر:

- اعلامیه (declaration) متعلق به یک stylesheet است که در حال حاضر روی این سند اعمال می‌شود.
- هر [قانون شرطی](/en-US/docs/Web/CSS/Guides/Conditional_rules) (مانند `@media` یا `@supports`) که این اعلامیه را در خود دارد، در حال حاضر برقرار است.
- اعلامیه متعلق به یک قاعدهٔ سبک است که انتخابگر (selector) آن با عنصر (element) مطابقت دارد.
- اعلامیه از نظر نحوی معتبر است: نام property توسط مرورگر شناسایی می‌شود و مقدار آن با نحو مورد انتظار برای آن property مطابقت دارد.

فقط اعلامیه‌های معتبر به «مقادیر اعلام‌شده» (declared values) تبدیل می‌شوند. اعلامیه‌هایی با نام property نامعتبر یا مقدار نامعتبر، طبق [قوانین مدیریت خطای CSS](/en-US/docs/Web/CSS/Guides/Syntax/Error_handling) فیلتر می‌شوند.

در این مثال، فقط اعلامیه‌های `font-size` و `font-weight` پردازش می‌شوند. [تجزیه‌گر CSS خطاها را فیلتر می‌کند](/en-US/docs/Web/CSS/Guides/Syntax/Error_handling#css_parser_errors) و اعلامیه‌ای که نام property نامعتبر دارد را نادیده می‌گیرد (یا «فیلتر» می‌کند):

```css
p {
  font-size: 1.25em;
  colr: blue;
  font-weight: bold;
}
```

پس از پایان فیلتر، هر عنصر برای هر property CSS، صفر یا چند [مقدار اعلام‌شده](#declared_value) دارد. این مقادیر اعلام‌شده نقطهٔ شروع مرحلهٔ پردازش [آبشاری (cascading)](#cascading) هستند.

### آبشاری (Cascading)

[Cascade](/en-US/docs/Web/CSS/Guides/Cascade/Introduction) وقتی چندین اعلامیه روی یک property برای یک عنصر اعمال می‌شوند، تعارض را حل می‌کند. Cascade اعلامیه‌ها را با استفاده از الگوریتم [ترتیب مرتب‌سازی cascade](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#cascading_order) مرتب می‌کند.

برای مثال، هر دو اعلامیهٔ `font-size` با `<p class="large">CSS is fun!</p>` مطابقت دارند، اما اعلامیهٔ دوم اعمال می‌شود چون [specificity](/en-US/docs/Web/CSS/Guides/Cascade/Specificity) بالاتری دارد. هر دو اعلامیه از منبع نویسنده (author origin) هستند، اما انتخابگر دوم specificity برابر `0-1-1` دارد در حالی که اولی `0-0-1` دارد:

```css
p {
  font-size: 1em;
}

p.large {
  font-size: 1.5em;
}
```

پس از cascade، مرورگر برای هر property روی هر عنصر [**مقدار آبشاری**](#cascaded_value) را تعیین می‌کند. این مقداری است که در مرحلهٔ بعدی پردازش، یعنی [پیش‌فرض‌سازی (defaulting)](#defaulting)، استفاده می‌شود.

### پیش‌فرض‌سازی (Defaulting)

**پیش‌فرض‌سازی** تضمین می‌کند که هر property روی هر عنصر یک مقدار دارد. این کار شامل اعمال مقادیر پیش‌فرض property وقتی هیچ اعلامیهٔ CSS به‌صراحت آن property را مقداردهی نکرده است، می‌شود. این شامل موارد زیر است:

- تنظیم **مقادیر ارث‌بری‌شده** برای [خواص ارث‌بر](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance#inherited_properties)
- تنظیم **مقادیر اولیه** برای [خواص غیرارث‌بر](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance#non-inherited_properties)

در نتیجهٔ پیش‌فرض‌سازی، هر property تضمین می‌کند که یک [مقدار مشخص‌شده (specified value)](#specified_value) دارد.

توجه داشته باشید که کلمات کلیدی صریح پیش‌فرض‌سازی (`initial`, `inherit`, `unset`, `revert`, `revert-layer`) نیز به مقادیر متناظر خود تبدیل می‌شوند تا [مقدار مشخص‌شده](#specified_value) تعیین شود.

## مراحل پردازش

تمام عناصری که بخشی از درخت عناصر مسطح (flattened element tree) سند هستند، مقادیر [اعلام‌شده](#declared_value)، [آبشاری](#cascaded_value)، [مشخص‌شده](#specified_value)، [محاسبه‌شده](#computed_value)، [استفاده‌شده](#used_value) و [واقعی](#actual_value) دارند. برای یک property خاص، این مقادیر ممکن است یکسان باشند یا نباشند. مثلاً اگر پایگاه کد بزرگ شما شامل CSS `p { font-size: 1.25em; }` باشد و HTML شما `<p class="large">CSS is fun!</p>` را داشته باشد، پاراگراف با چه اندازه‌ای نمایش داده می‌شود؟ مقدار `font-size` از چند مرحله عبور می‌کند تا از مقدار مشخص‌شدهٔ `em` به مقدار رندر شدهٔ `px` برسد.

مراحل پردازش مقدار عبارتند از: [مقدار اعلام‌شده](#declared_value)، [مقدار آبشاری](#cascaded_value)، [مقدار مشخص‌شده](#specified_value)، [مقدار محاسبه‌شده](#computed_value)، [مقدار استفاده‌شده](#used_value) و [مقدار واقعی](#actual_value). این مقادیر برای تعیین [مقدار نهایی رندر شده](#rendered_values) استفاده می‌شوند.

### مقدار اعلام‌شده (Declared value)

**مقدار اعلام‌شده** هر مقداری است که از نظر دستوری معتبر باشد و در یک اعلان (declaration) که برای یک عنصر اعمال می‌شود، تعریف شده باشد. یک عنصر می‌تواند برای هر ویژگی (property) صفر یا چند مقدار اعلام‌شده داشته باشد. این مقادیر از برگه‌های سبک (نویسنده، کاربر یا عامل کاربر) می‌آیند و در مرحلهٔ [فیلتر کردن](#filtering) شناسایی می‌شوند.

در ادامهٔ مثال قبلی، که برگه‌سبک ما شامل `p { font-size: 1.25em; }` است و سند متصل به آن برگه‌سبک شامل `<p class="large">CSS is fun!</p>` می‌شود، ممکن است اعلان‌های `font-size` دیگری هم وجود داشته باشند که بتوانند روی همان پاراگراف اعمال شوند. برگه‌سبک عامل کاربر ممکن است `font-size: 1em` را برای همهٔ پاراگراف‌ها تنظیم کند، در حالی که یک اعلان دیگر از نویسنده `font-size: 2em` را برای عناصر با کلاس "large" تنظیم کرده است:

```css
/* سبک‌های عامل کاربر */
p {
  font-size: 1em;
}

/* سبک‌های نویسنده */
p {
  font-size: 1.25em;
}

.large {
  font-size: 2em;
}
```

ممکن است اعلان‌های `font-size` دیگری هم در برگه‌سبک ما وجود داشته باشد، اما فقط اعلان‌هایی که انتخابگرشان با عنصر مطابقت دارد، به عنوان مقدار اعلام‌شده در نظر گرفته می‌شوند. در این مثال، چون عنصر `<p>` ما دارای `class="large"` است، هر سه اعلان برای این عنصر مقدار اعلام‌شده محسوب می‌شوند.

### مقدار آبشاری (Cascaded value)

**مقدار آبشاری** همان مقدار اعلام‌شده‌ای است که در [آبشار](#cascading) برنده می‌شود. برای هر ویژگی و هر عنصر حداکثر یک مقدار آبشاری وجود دارد.

از میان مقادیر اعلام‌شدهٔ ما، سبک‌های نویسنده بر سبک‌های عامل کاربر غلبه می‌کنند. در یک منبع (origin) واحد، سبک‌هایی با اختصاصی بودن (specificity) بالاتر بر سبک‌هایی با اختصاصی بودن پایین‌تر غلبه می‌کنند. در اینجا مقدار آبشاری `font-size: 2em` خواهد بود، از منبع نویسنده با اختصاصی بودن `0-1-1`:

```css
font-size: 2em;
```

اگر هیچ مقدار اعلام‌شده‌ای برای یک ویژگی وجود نداشته باشد، مقدار آبشاری‌ای هم وجود نخواهد داشت، یعنی [مقدار مشخص‌شده](#specified_value) برای آن ویژگی از طریق فرایند [پیش‌فرض‌گیری](#defaulting) تعیین می‌شود.

### مقدار مشخص‌شده (Specified value)

**مقدار مشخص‌شده** نتیجهٔ فرایند [پیش‌فرض‌گیری](#defaulting) است. تضمین می‌شود که برای هر ویژگی و هر عنصر وجود داشته باشد. مقدار مشخص‌شده به این ترتیب تعیین می‌شود:

1. اگر [مقدار آبشاری](#cascaded_value) وجود داشته باشد، همان مقدار آبشاری، مقدار مشخص‌شده است.
2. اگر مقدار آبشاری وجود _نداشته باشد_ و ویژگی [ارثی](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance) باشد، مقدار مشخص‌شده برابر با [مقدار محاسبه‌شده](#computed_value) عنصر والد است.
3. اگر مقدار آبشاری وجود _نداشته باشد_ و ویژگی _ارثی نباشد_، مقدار مشخص‌شده برابر با [مقدار اولیه](#initial_value) آن ویژگی است.

در مثال ما، چون یک [مقدار آبشاری](#cascaded_value) برابر با `2em` داریم، این مقدار به عنوان مقدار مشخص‌شده در نظر گرفته می‌شود:

```css
font-size: 2em;
```

برای ویژگی‌هایی که مقدار آبشاری ندارند، فرایند پیش‌فرض‌گیری مقدار را تعیین می‌کند. مثلاً اگر `color` مشخص نشده باشد، `color` از مقدار محاسبه‌شدهٔ والد به ارث می‌رسد، چون یک ویژگی ارثی است. اگر `margin` مشخص نشده باشد، مقدار اولیهٔ `0` استفاده می‌شود، چون `margin` یک [ویژگی غیرارثی](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance#inherited_properties) است:

```css
color: inherit;
margin: 0;
```

#### مقدار اولیه (Initial value)

**مقدار اولیه** یک ویژگی، مقدار پیش‌فرضی است که در جدول تعریف آن ویژگی در مشخصات (specification) ذکر شده است. این مقدار در پیش‌فرض‌گیری در موارد زیر استفاده می‌شود:

- برای [ویژگی‌های ارثی](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance#inherited_properties)، مقدار اولیه فقط روی _عنصر ریشه_ (که عنصر والد ندارد) استفاده می‌شود، وقتی که مقدار آبشاری‌ای وجود نداشته باشد.
- برای [ویژگی‌های غیرارثی](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance#non-inherited_properties)، مقدار اولیه روی _همهٔ عناصر_ استفاده می‌شود، وقتی که مقدار آبشاری‌ای وجود نداشته باشد.

می‌توانید با استفاده از کلیدواژهٔ `initial` مقدار اولیه را به صورت صریح تنظیم کنید.

> [!NOTE]
> مقدار اولیه را می‌توانید در بخش «نحو رسمی» (formal syntax) هر صفحهٔ مرجع ویژگی CSS پیدا کنید. مثلاً [مقدار اولیهٔ `font-size` برابر `medium` است](/en-US/docs/Web/CSS/Reference/Properties/font-size#formal_definition). مقدار اولیه را با مقداری که برگه‌ی استایل مرورگر تعیین کرده اشتباه نگیرید.

### Computed value (مقدار محاسبه‌شده)

**Computed value** یک ویژگی، مقداری است که در هنگام ارث‌بری از والد به فرزند منتقل می‌شود. این مقدار پس از تبدیل واحدهای نسبی و custom properties به مقادیر مطلق به دست می‌آید، اما هنوز اطلاعات مربوط به چیدمان (layout) در آن اعمال نشده است.

Computed value از [specified value](#specified_value) (مقدار مشخص‌شده) به این صورت محاسبه می‌شود:

1. مدیریت مقادیر ویژهٔ `inherit`، `initial`، `revert`، `revert-layer` و `unset`.
2. انجام محاسبات لازم برای رسیدن به مقداری که در خط «Computed value» جدول تعریف آن ویژگی نوشته شده است.

محاسبات لازم برای رسیدن به computed value معمولاً شامل تبدیل مقادیر نسبی (مثلاً واحدهای `em` یا درصدها) به مقادیر مطلق است. برای مثال، اگر یک المنت دارای specified values `font-size: 16px` و `padding-top: 2em` باشد، computed value برای `padding-top` برابر `32px` خواهد بود (دو برابر اندازه قلم).

اما برای برخی ویژگی‌ها (مانند `width`، `margin-right`، `text-indent` و `top` که درصدها به چیزی وابسته‌اند که نیاز به چیدمان دارد)، مقادیر درصدی به computed value‌های درصدی تبدیل می‌شوند. همچنین اعداد بدون واحد که برای ویژگی `line-height` مشخص می‌شوند، همان‌طور که هستند به computed value تبدیل می‌شوند. مقادیر نسبی‌ای که در computed value باقی می‌مانند، در زمان تعیین [used value](#used_value) (مقدار استفاده‌شده) مطلق می‌شوند.

### Used value (مقدار استفاده‌شده)

**Used value** یک ویژگی، مقداری است که پس از انجام تمام محاسبات روی [computed value](#computed_value) و اصلاح آن با جزئیات مربوط به چیدمان (مثلاً تبدیل درصدها به پیکسل واقعی) به دست می‌آید.

هر ویژگی CSS یک used value دارد. used value ابعاد (مثلاً {{cssxref("width")}} یا {{cssxref("line-height")}}) بر حسب پیکسل است. used value ویژگی‌های خلاصه‌نویس (shorthand) مانند {{cssxref("background")}} با used value ویژگی‌های تشکیل‌دهنده‌شان (مثلاً {{cssxref("background-color")}} یا {{cssxref("background-size")}}) و همچنین با {{cssxref("position")}} و {{cssxref("float")}} سازگار است.

used value برای {{cssxref("width")}} یا {{cssxref("inline-size")}} یک المنت، حتی اگر specified value با درصد یا کلمه‌های کلیدی مشخص شده باشد، به صورت پیکسل است.

اگر سه المنت کانتینر داشته باشیم که عرض آنها به ترتیب `auto`، `50%` و `inherit` تنظیم شده باشد:

```html hidden
<div id="no-width">
  <p>No explicit width.</p>
  <p class="show-used-width">..</p>

  <div id="width-50">
    <p>Explicit width: 50%.</p>
    <p class="show-used-width">..</p>

    <div id="width-inherit">
      <p>Explicit width: inherit.</p>
      <p class="show-used-width">..</p>
    </div>
  </div>
</div>
```

```css
#no-width {
  width: auto;
}

#width-50 {
  width: 50%;
}

#width-inherit {
  width: inherit;
}

/* Make results easier to see */
div {
  border: 1px solid red;
  padding: 8px;
}
```

```js hidden
function updateUsedWidth(id) {
  const div = document.getElementById(id);
  const par = div.querySelector(".show-used-width");
  const wid = window.getComputedStyle(div)["width"];
  par.textContent = `Used width: ${wid}.`;
}

function updateAllUsedWidths() {
  updateUsedWidth("no-width");
  updateUsedWidth("width-50");
  updateUsedWidth("width-inherit");
}

updateAllUsedWidths();
window.addEventListener("resize", updateAllUsedWidths);
```

با اینکه سه مقدار مشخص‌شده `auto`، `50%` و `inherit` از نوع کلمه کلیدی یا درصد هستند، دریافت `width` با `window.getComputedStyle(el)["width"]` یک مقدار طول مطلق (absolute length) بر حسب `px` برمی‌گرداند.

## مقادیر نهایی رندر (Rendered values)

مقدار نهایی رندر شده را **مقدار واقعی (actual value)** می‌نامند، در حالی که مقداری که از طریق اسکریپت به‌دست می‌آید **مقدار نهایی (resolved value)** نامیده می‌شود.

### مقدار واقعی (Actual value)

**مقدار واقعی** یک ویژگی برابر است با [مقدار استفاده‌شده (used value)](#used_value) آن ویژگی پس از اعمال هرگونه تقریب لازم. این مقدار نهایی رندر شده‌ای است که توسط مرورگر پیاده‌سازی می‌شود و شامل تنظیمات مربوط به محدودیت‌ها یا ویژگی‌های خاص رندر است. برای مثال، یک عامل کاربر (user agent) که فقط می‌تواند حاشیه‌ها را با ضخامت پیکسل صحیح رندر کند، ممکن است ضخامت حاشیه را به نزدیک‌ترین عدد صحیح گرد کند.

محاسبه شامل این مراحل است:

1. ابتدا [مقدار مشخص‌شده (specified value)](#specified_value) بر اساس نتیجه [آبشاری (cascading)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction)، [وراثت (inheritance)](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance)، یا استفاده از [مقدار اولیه (initial value)](#initial_value) تعیین می‌شود.
2. سپس [مقدار محاسبه‌شده (computed value)](#computed_value) مطابق با مشخصات محاسبه می‌شود (مثلاً یک `span` با `position: absolute` مقدار `display` محاسبه‌شده‌اش به `block` تغییر می‌کند).
3. پس از آن، layout محاسبه شده و [مقدار استفاده‌شده (used value)](#used_value) به‌دست می‌آید.
4. در نهایت، مقدار استفاده‌شده با توجه به محدودیت‌های محیط محلی تبدیل شده و مقدار واقعی حاصل می‌شود.

### مقدار نهایی (Resolved value)

**مقدار نهایی (resolved value)** یک ویژگی، مقداری است که پس از اعمال stylesheet‌های فعال و حل هرگونه محاسبه پایه‌ای که آن مقادیر ممکن است داشته باشند، به‌دست می‌آید. متد {{domxref("Window.getComputedStyle", "getComputedStyle()")}} یک شیء زنده از نوع {{domxref("CSSStyleDeclaration")}} برمی‌گرداند که شامل مقادیر نهایی تمام ویژگی‌های CSS اعمال‌شده روی یک عنصر مشخص است. هر مقدار نهایی یا [مقدار محاسبه‌شده (computed value)](#computed_value) است یا [مقدار استفاده‌شده (used value)](#used_value)، بسته به ویژگی.

در گذشته، `getComputedStyle()` مقدار محاسبه‌شده یک عنصر یا شبه‌عنصر را برمی‌گرداند. با تکامل CSS، مفهوم «مقدار محاسبه‌شده» نیز تغییر کرد، اما مقادیر بازگشتی از `getComputedStyle()` برای سازگاری با اسکریپت‌های موجود باید ثابت می‌ماند. این مقادیر همان «مقادیر نهایی» هستند.

برای اکثر ویژگی‌ها، مقدار نیمی برابر با مقدار محاسبه‌شده است، اما برای چند ویژگی قدیمی (از جمله {{cssxref("width")}} و {{cssxref("height")}})، مقدار نهایی برابر با مقدار استفاده‌شده است. [مشخصات CSSOM](https://drafts.csswg.org/cssom/#resolved_values) جزئیات مربوط به هر ویژگی را ارائه می‌دهد.

CSS 2.0 «مقدار محاسبه‌شده» را به عنوان آخرین مرحله در محاسبه یک ویژگی تعریف کرد. CSS 2.1 تعریف جداگانه‌ای برای «مقدار استفاده‌شده» معرفی نمود. یک عنصر می‌توانست به‌طور صریح عرض/ارتفاع والد خود را به ارث ببرد، در حالی که مقدار محاسبه‌شده آن یک درصد بود. برای ویژگی‌های CSS که به layout وابسته نیستند (مانند `display`، `font-size` یا `line-height`)، مقادیر محاسبه‌شده و استفاده‌شده یکسان هستند. فهرست زیر شامل ویژگی‌های CSS 2.1 است که به layout وابسته هستند و بنابراین مقدار محاسبه‌شده و استفاده‌شده متفاوتی دارند (برگرفته از [تغییرات CSS 2.1: مقادیر مشخص‌شده، محاسبه‌شده و واقعی](https://www.w3.org/TR/CSS2/changes.html#q21.36)):

- `background-position`
- `bottom`، `left`، `right`، `top`
- `height`، `width`
- `margin-bottom`، `margin-left`، `margin-right`، `margin-top`
- `min-height`، `min-width`
- `padding-bottom`، `padding-left`، `padding-right`، `padding-top`
- `text-indent`

## همچنین ببینید

- مقادیر CSS برای کنترل وراثت (inheritance): [`inherit`](/en-US/docs/Web/CSS/inherit)، [`initial`](/en-US/docs/Web/CSS/initial)، [`revert`](/en-US/docs/Web/CSS/revert)، [`revert-layer`](/en-US/docs/Web/CSS/revert-layer) و [`unset`](/en-US/docs/Web/CSS/unset)
- [ماژول آبشاری و وراثت CSS](/en-US/docs/Web/CSS/Guides/Cascade)
- [ماژول نحو CSS](/en-US/docs/Web/CSS/Guides/Syntax)