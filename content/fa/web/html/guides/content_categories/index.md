---
title: Content categories
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories
translated_by: n8n + AI
---

# Content categories

بیشتر عناصر [HTML](../../../../../../en-US/docs/Web/HTML/) عضو یک یا چند **دسته محتوا** (content categories) هستند — این دسته‌ها عناصری را گروه‌بندی می‌کنند که ویژگی‌های مشترک دارند. این گروه‌بندی چندان رسمی نیست (در واقع رابطه‌ای بین عناصر این دسته‌ها ایجاد نمی‌کند)، اما به تعریف و توصیف رفتار مشترک دسته‌ها و قوانین مرتبط با آن‌ها کمک می‌کند. همچنین ممکن است [عناصری وجود داشته باشند که عضو _هیچ‌کدام_ از این دسته‌ها نیستند](index.md#elements_without_a_category).

دسته‌های محتوا برای تعریف _مدل محتوا_ (content model) عناصر استفاده می‌شوند؛ به عبارت دیگر، مشخص می‌کنند هر عنصر چه فرزندانی می‌تواند داشته باشد. برای مثال، عنصر `<p>` فقط می‌تواند _محتوای متنی_ (phrasing content) داشته باشد، در حالی که عنصر `<div>` می‌تواند _محتوای جریانی_ (flow content) را در خود جای دهد. برخی عناصر مانند `<ins>` دارای _مدل محتوای شفاف_ ([transparent](index.md#transparent_content_model)) هستند.

هفت دسته محتوای اصلی وجود دارد که می‌توان آن‌ها را با نمودار ون زیر خلاصه کرد:

> \[!NOTE] بحث دقیق‌تر درباره این دسته‌های محتوا و مقایسه عملکرد آن‌ها از حوصله این مقاله خارج است؛ برای این کار می‌توانید [بخش‌های مرتبط در مشخصات HTML](https://html.spec.whatwg.org/multipage/dom.html#kinds-of-content) را مطالعه کنید.

### محتوای فراداده

عناصری که در دسته _محتوای فراداده_ قرار می‌گیرند، نمایش یا رفتار بقیه سند را تغییر می‌دهند، پیوندهایی به اسناد دیگر ایجاد می‌کنند، یا اطلاعات _برون‌باندی_ (out-of-band) دیگری را منتقل می‌کنند. هر چیزی که داخل `<head>` قرار می‌گیرد، از جمله `<title>`، `<link>`، `<script>`، `<style>` و `<base>` که کمتر استفاده می‌شود، محتوای فراداده محسوب می‌شود. عنصر `<meta>` نیز برای فراداده‌ای به کار می‌رود که نمی‌توان با این عناصر دیگر نمایش داد.

عناصر فراداده عبارت‌اند از:

* `<base>`
* `<link>`
* `<meta>`
* `<noscript>`
* `<script>`
* `<style>`
* `<template>`
* `<title>`

برخی از این عناصر به بیش از یک دسته محتوا تعلق دارند. برای مثال، `<script>` عضو دسته‌های فراداده، محتوای جریانی و محتوای متنی است و همچنین یک عنصر پشتیبان اسکریپت (script-supporting) محسوب می‌شود؛ `<script>` را می‌توان در جاهایی استفاده کرد که محتوای فراداده، محتوای متنی یا عناصر پشتیبان اسکریپت انتظار می‌رود.

### محتوای جریانی

محتوای جریانی دسته‌ای گسترده است که بیشتر عناصری را در بر می‌گیرد که می‌توانند داخل عنصر `<body>` قرار بگیرند؛ از جمله عناصر عنوان، عناصر بخش‌بندی، عناصر متنی (phrasing)، عناصر جاسازی (embedding)، عناصر تعاملی و عناصر مرتبط با فرم. این دسته همچنین گره‌های متنی را شامل می‌شود (به جز گره‌هایی که فقط از کاراکترهای فاصله (whitespace) تشکیل شده‌اند).

عناصر جریانی عبارت‌اند از:

* `<a>`
* `<abbr>`
* `<address>`
* `<article>`
* `<aside>`
* `<audio>`
* `<b>`
* `<bdi>`
* `<bdo>`
* `<blockquote>`
* `<br>`
* `<button>`
* `<canvas>`
* `<cite>`
* `<code>`
* `<data>`
* `<datalist>`
* `<del>`
* `<details>`
* `<dfn>`
* `<dialog>`
* `<div>`
* `<dl>`
* `<em>`
* `<embed>`
* `<fieldset>`
* `<figure>`
* `<footer>`
* `<form>`
* `<geolocation>`
* `<h1>`-`<h6>`
* `<header>`
* `<hgroup>`
* `<hr>`
* `<i>`
* `<iframe>`
* `<img>`
* `<input>`
* `<ins>`
* `<kbd>`
* `<label>`
* `<main>`
* `<map>`
* `<mark>`
* `<math>`
* `<menu>`
* `<meter>`
* `<nav>`
* `<noscript>`
* `<object>`
* `<ol>`
* `<output>`
* `<p>`
* `<picture>`
* `<pre>`
* `<progress>`
* `<q>`
* `<ruby>`
* `<s>`
* `<samp>`
* `<script>`
* `<search>`
* `<section>`
* `<select>`
* `<slot>`
* `<small>`
* `<span>`
* `<strong>`
* `<sub>`
* `<sup>`
* `<svg>`
* `<table>`
* `<template>`
* `<textarea>`
* `<time>`
* `<u>`
* `<ul>`
* `<var>`
* `<video>`
* `<wbr>`
* [المان‌های سفارشی خودمختار](../../../../../../en-US/docs/Web/API/Web_components/Using_custom_elements/)
* متن ساده

چند المان دیگر نیز جزو این دسته‌اند، اما فقط در صورتی که شرط خاصی برقرار باشد:

* `<area>`، اگر داخل یک المان `<map>` قرار بگیرد
* `<link>`، اگر attribute [`itemprop`](../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/itemprop/) وجود داشته باشد
* `<meta>`، اگر attribute [`itemprop`](../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/itemprop/) وجود داشته باشد

### محتوای بخش‌بندی

محتوای بخش‌بندی، زیرمجموعه‌ای از محتوای جریانی است که یک [بخش در طرح کلی فعلی](../../../../../../en-US/docs/Web/HTML/Reference/Elements/Heading_Elements/) ایجاد می‌کند و محدودهٔ المان‌های `<header>` و `<footer>` را تعریف می‌کند.

المان‌های بخش‌بندی عبارت‌اند از:

* `<article>`
* `<aside>`
* `<nav>`
* `<section>`

### محتوای عنوان

محتوای عنوان، زیرمجموعه‌ای از محتوای جریانی، عنوان یک بخش را تعریف می‌کند. این تعریف هم برای بخش‌هایی که با یک المان [محتوای بخش‌بندی](index.md#sectioning_content) صریح مشخص شده‌اند و هم برای بخش‌هایی که به‌صورت ضمنی توسط خود محتوای عنوان تعریف می‌شوند، کاربرد دارد.

المان‌های عنوان عبارت‌اند از:

* `<h1>`-`<h6>`
* `<hgroup>`

> \[!NOTE] اگرچه احتمال دارد `<header>` شامل محتوای عنوان باشد، اما خودش محتوای عنوان نیست.

### محتوای عبارتی

محتوای عبارتی، زیرمجموعه‌ای از محتوای جریانی، به متن و نشانه‌گذاری (markup) درون یک سند اشاره دارد. دنباله‌هایی از محتوای عبارتی، پاراگراف‌ها را می‌سازند.

المان‌های عبارتی عبارت‌اند از:

* \{{HTMLElement("abbr")\}}
* \{{HTMLElement("audio")\}}
* \{{HTMLElement("b")\}}
* \{{HTMLElement("bdi")\}}
* \{{HTMLElement("bdo")\}}
* \{{HTMLElement("br")\}}
* \{{HTMLElement("button")\}}
* \{{HTMLElement("canvas")\}}
* \{{HTMLElement("cite")\}}
* \{{HTMLElement("code")\}}
* \{{HTMLElement("data")\}}
* \{{HTMLElement("datalist")\}}
* \{{HTMLElement("dfn")\}}
* \{{HTMLElement("em")\}}
* \{{HTMLElement("embed")\}}
* \{{HTMLElement("i")\}}
* \{{HTMLElement("iframe")\}}
* \{{HTMLElement("img")\}}
* \{{HTMLElement("input")\}}
* \{{HTMLElement("kbd")\}}
* \{{HTMLElement("label")\}}
* \{{HTMLElement("mark")\}}
* \{{MathMLElement("math")\}}
* \{{HTMLElement("meter")\}}
* \{{HTMLElement("noscript")\}}
* \{{HTMLElement("object")\}}
* \{{HTMLElement("output")\}}
* \{{HTMLElement("picture")\}}
* \{{HTMLElement("progress")\}}
* \{{HTMLElement("q")\}}
* \{{HTMLElement("ruby")\}}
* \{{HTMLElement("s")\}}
* \{{HTMLElement("samp")\}}
* \{{HTMLElement("script")\}}
* \{{HTMLElement("select")\}}
* \{{HTMLElement("slot")\}}
* \{{HTMLElement("small")\}}
* \{{HTMLElement("span")\}}
* \{{HTMLElement("strong")\}}
* \{{HTMLElement("sub")\}}
* \{{HTMLElement("sup")\}}
* \{{SVGElement("svg")\}}
* \{{HTMLElement("template")\}}
* \{{HTMLElement("textarea")\}}
* \{{HTMLElement("time")\}}
* \{{HTMLElement("u")\}}
* \{{HTMLElement("var")\}}
* \{{HTMLElement("video")\}}
* \{{HTMLElement("wbr")\}}
* [عناصر سفارشی مستقل (Autonomous custom elements)](../../../../../../en-US/docs/Web/API/Web_components/Using_custom_elements/)
* متن ساده (Plain text)

چند عنصر دیگر نیز تنها در صورت برآورده شدن یک شرط خاص به این دسته تعلق دارند:

* \{{HTMLElement("a")\}}، اگر فقط شامل محتوای عبارتی (phrasing content) باشد
* \{{HTMLElement("area")\}}، اگر از نوادگان یک عنصر \{{HTMLElement("map")\}} باشد
* \{{HTMLElement("del")\}}، اگر فقط شامل محتوای عبارتی (phrasing content) باشد
* \{{HTMLElement("ins")\}}، اگر فقط شامل محتوای عبارتی (phrasing content) باشد
* \{{HTMLElement("link")\}}، اگر ویژگی [`itemprop`](../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/itemprop/) وجود داشته باشد
* \{{HTMLElement("map")\}}، اگر فقط شامل محتوای عبارتی (phrasing content) باشد
* \{{HTMLElement("meta")\}}، اگر ویژگی [`itemprop`](../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/itemprop/) وجود داشته باشد

### Embedded content

محتوای توکار (embedded content) زیرمجموعه‌ای از محتوای جریان (flow content) است که یک منبع دیگر را وارد می‌کند یا محتوایی از یک زبان نشانه‌گذاری یا فضای نام دیگر را در سند قرار می‌دهد.

عناصر محتوای توکار عبارتند از:

* \{{HTMLElement("audio")\}}
* \{{HTMLElement("canvas")\}}
* \{{HTMLElement("embed")\}}
* \{{HTMLElement("iframe")\}}
* \{{HTMLElement("img")\}}
* \{{MathMLElement("math")\}}
* \{{HTMLElement("object")\}}
* \{{HTMLElement("picture")\}}
* \{{SVGElement("svg")\}}
* \{{HTMLElement("video")\}}

### Interactive content

محتوای تعاملی (interactive content) زیرمجموعه‌ای از محتوای جریان (flow content) است که شامل عناصری می‌شود که به‌طور خاص برای تعامل کاربر طراحی شده‌اند.

عناصر محتوای تعاملی عبارتند از:

* \{{HTMLElement("button")\}}
* \{{HTMLElement("details")\}}
* \{{HTMLElement("embed")\}}
* \{{HTMLElement("iframe")\}}
* \{{HTMLElement("label")\}}
* \{{HTMLElement("select")\}}
* \{{HTMLElement("textarea")\}}

برخی عناصر تنها تحت شرایط خاصی به این دسته تعلق دارند:

* \{{HTMLElement("a")\}}، اگر ویژگی [`href`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/a/#href) وجود داشته باشد
* \{{HTMLElement("audio")\}}، اگر ویژگی [`controls`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/audio/#controls) وجود داشته باشد
* \{{HTMLElement("img")\}}، اگر ویژگی [`usemap`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/img/#usemap) وجود داشته باشد
* \{{HTMLElement("input")\}}، اگر ویژگی [`type`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#type) در حالت hidden نباشد
* \{{HTMLElement("object")\}}، اگر ویژگی [`usemap`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/object/#usemap) وجود داشته باشد
* \{{HTMLElement("video")\}}، اگر ویژگی [`controls`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/video/#controls) وجود داشته باشد

### Palpable content

محتواهای قابل لمس (Palpable content) محتوایی هستند که نه خالی‌اند و نه پنهان؛ یعنی محتوایی که رندر می‌شود و ماهیت محتوایی دارد. Palpable content برای تعریف مدل محتوا (content model) استفاده نمی‌شود، بلکه برای تعریف یک قانون کلی به کار می‌رود: عناصری که مدل محتوایی‌شان اجازهٔ هر نوع flow content یا phrasing content را می‌دهد، باید حداقل یک گره (node) در محتویاتشان داشته باشند که palpable content باشد و attribute `hidden` نیز روی آن تنظیم نشده باشد.

عناصر palpable عبارت‌اند از:

* `<a>`
* `<abbr>`
* `<address>`
* `<article>`
* `<aside>`
* `<b>`
* `<bdi>`
* `<bdo>`
* `<blockquote>`
* `<button>`
* `<canvas>`
* `<cite>`
* `<code>`
* `<data>`
* `<del>`
* `<details>`
* `<dfn>`
* `<div>`
* `<em>`
* `<embed>`
* `<fieldset>`
* `<footer>`
* `<figure>`
* `<form>`
* `<iframe>`
* `<img>`
* `<ins>`
* `<kbd>`
* `<label>`
* `<main>`
* `<map>`
* `<mark>`
* `<math>`
* `<meter>`
* `<nav>`
* `<object>`
* `<p>`
* `<picture>`
* `<pre>`
* `<progress>`
* `<q>`
* `<ruby>`
* `<s>`
* `<samp>`
* `<search>`
* `<section>`
* `<select>`
* `<small>`
* `<span>`
* `<strong>`
* `<sub>`
* `<sup>`
* `<svg>`
* `<table>`
* `<textarea>`
* `<time>`
* `<u>`
* `<var>`
* `<video>`
* [Autonomous custom elements](../../../../../../en-US/docs/Web/API/Web_components/Using_custom_elements/)
* متن ساده‌ای که whitespace بین عناصر (inter-element whitespace) نباشد.

بعضی عناصر فقط در شرایط خاصی در این دسته قرار می‌گیرند:

* `<audio>`، اگر attribute [`controls`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/audio/#controls) حضور داشته باشد.
* `<dl>`، اگر فرزندان عنصر شامل حداقل یک گروه نام-مقدار باشند.
* `<input>`، اگر attribute [`type`](../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#type) در حالت hidden نباشد.
* `<ol>`، اگر فرزندانش شامل حداقل یک عنصر `<li>` باشند.
* `<ul>`، اگر فرزندانش شامل حداقل یک عنصر `<li>` باشند.

### عناصر بدون دسته

چند عنصر عضو هیچ دستهٔ محتوایی نیستند. این عناصر عبارت‌اند از:

* `<caption>`
* `<col>`
* `<colgroup>`
* `<dd>`
* `<dt>`
* `<figcaption>`
* `<head>`
* `<html>`
* `<legend>`
* `<li>`
* `<optgroup>`
* `<option>`
* `<param>`
* `<rb>`
* `<rp>`
* `<rt>`
* `<rtc>`
* `<source>`
* `<tbody>`
* `<tfoot>`
* `<th>`
* `<thead>`
* `<tr>`
* `<track>`

### عناصر پشتیبان اسکریپت (Script-supporting elements)

**عناصر پشتیبان اسکریپت (Script-supporting elements)** عناصری هستند که مستقیماً در خروجی رندر شدهٔ سند مشارکت ندارند. در عوض، برای پشتیبانی از اسکریپت‌ها عمل می‌کنند؛ یا با دربرگیری یا مشخص کردن مستقیم کد اسکریپت، یا با مشخص کردن داده‌هایی که توسط اسکریپت‌ها استفاده می‌شوند. تقریباً همهٔ عناصر، از جمله آن‌هایی که فقط عناصر خاصی را می‌پذیرند (مانند `<ul>` که عناصر `<li>` می‌پذیرد)، می‌توانند حاوی عناصر پشتیبان اسکریپت باشند.

المان‌های پشتیبانی‌کنندهٔ اسکریپت عبارتند از:

* `<script>`
* `<template>`

### محتوای وابسته به فرم (Form-associated content)

محتوای وابسته به فرم زیرمجموعه‌ای از «محتوای جریان» (flow content) است که شامل المان‌هایی می‌شود که یک «مالک فرم» (form owner) دارند و می‌توانند در هر جایی که محتوای جریان انتظار می‌رود استفاده شوند. مالک فرم یا همان المان `<form>` والد است، یا `<form>`ای که `id` آن در ویژگی `form` المان مشخص شده است.

المان‌های وابسته به فرم عبارتند از:

* `<button>`
* `<fieldset>`
* `<input>`
* `<object>`
* `<output>`
* `<select>`
* `<textarea>`
* `<img>`

این دسته خود چند زیردسته دارد:

* **listed** – المان‌هایی که در مجموعه‌های `HTMLFormElement.elements` و `HTMLFieldSetElement.elements` فهرست می‌شوند. شامل `<button>`، `<fieldset>`، `<input>`، `<object>`، `<output>`، `<select>` و `<textarea>`.
* **submittable** – المان‌هایی که می‌توانند برای ساختن مجموعه داده‌های فرم هنگام ارسال استفاده شوند. شامل `<button>`، `<input>`، `<select>` و `<textarea>`.
* **resettable** – المان‌هایی که با بازنشانی (reset) فرم تحت تأثیر قرار می‌گیرند. شامل `<input>`، `<output>`، `<select>` و `<textarea>`.
* **autocapitalize-and-autocorrect-inheriting** – المان‌هایی که ویژگی‌های `autocapitalize` و `autocorrect` را از مالک فرم خود به ارث می‌برند. شامل `<button>`، `<fieldset>`، `<input>`، `<output>`، `<select>` و `<textarea>`.
* **labelable** – المان‌هایی که می‌توانند با `<label>` مرتبط شوند. شامل `<button>`، `<input>` (همهٔ types به جز `hidden`)، `<meter>`، `<output>`، `<progress>`، `<select>` و `<textarea>`.

### مدل محتوای شفاف (Transparent content model)

علاوه بر دسته‌بندی‌های محتوایی بالا، مدل محتوای یک المان ممکن است «شفاف» (transparent) تعریف شود. اگر محتوای مجاز المان X «شفاف» باشد، به والد X نگاه می‌کنیم. محتوای مجاز والد X را با دسته‌بندی‌های محتوایی X اشتراک می‌گیریم؛ نتیجه همان چیزی است که «شفاف» در این زمینه معنی می‌دهد. اگر والد X هم مدل محتوای شفاف داشته باشد، تا جایی که به یک مدل محتوای غیرشفاف برسیم، درخت را بالا می‌رویم. وقتی چنین والدی وجود نداشته باشد، «شفاف» به معنی «محتوای جریان» (flow content) است.

مثلاً المان `<ruby>` محتوای متنی (phrasing content) می‌پذیرد. المان `<ins>` وقتی فقط محتوای متنی داشته باشد، در دسته‌بندی محتوای متنی قرار می‌گیرد. بنابراین یک `<ins>` می‌تواند داخل `<ruby>` قرار بگیرد. محتوای مجاز `<ins>` «شفاف» است، که وقتی داخل `<ruby>` قرار می‌گیرد، یعنی «محتوای متنی». اما المان‌های `<rt>` محتوای متنی نیستند. بنابراین `<rt>` نمی‌تواند داخل این `<ins>` قرار بگیرد، حتی اگر هم `<rt>` و هم `<ins>` بتوانند داخل `<ruby>` باشند و `<ins>` «شفاف» باشد.

```html
<ruby>
  Text before
  <ins>
    <!-- Invalid: rt cannot be placed inside ins here -->
    <rt>Pronunciation</rt>
  </ins>
</ruby>
```

```html
<ruby>
  Text before
  <!-- Valid: ins can be inside ruby, and rt can be inside ruby -->
  <ins>Inserted text</ins>
  <rt>Pronunciation</rt>
</ruby>
```

```html
<ruby>
  Text before
  <!-- Valid: rt can be inside ruby, and ins can be inside rt -->
  <rt><ins>Pronunciation</ins></rt>
</ruby>
```

Transparent یک _content model_ است، نه یک _content category_. بنابراین فقط مشخص می‌کند که یک عنصر می‌تواند چه فرزندانی داشته باشد، نه این‌که خودش در کجا باید قرار بگیرد. یعنی هنگام تعیین اعتبار (مجاز بودن) فرزندان یک عنصر، نمی‌توانید از فرزندان transparent «عبور» کنید و به محتوای لایه‌های پایین‌تر نگاه کنید. مثلاً یک عنصر `<ul>` فقط `<li>` و عناصر پشتیبان اسکریپت (script-supporting elements) را می‌پذیرد و `<del>` یا `<ins>` را حتی اگر فقط شامل `<li>` باشند، قبول نمی‌کند.

```html
<ul>
  <del>
    <li>Oranges</li>
    <li>Toilet paper</li>
  </del>
  <li>Toothpaste</li>
</ul>
```

```html
<ul>
  <li><del>Oranges</del></li>
  <li><del>Toilet paper</del></li>
  <li>Toothpaste</li>
</ul>
```
