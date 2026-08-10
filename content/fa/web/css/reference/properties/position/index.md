---
title: "position CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/position"
translated_by: "n8n + AI"
---

# `position` CSS property

ویژگی **`position`** در [CSS](/en-US/docs/Web/CSS) نحوه موقعیت‌دهی یک عنصر را در سند مشخص می‌کند. برای تعیین محل نهایی عناصر موقعیت‌دهی‌شده می‌توان از ویژگی‌های فیزیکی {{Cssxref("top")}}، {{Cssxref("right")}}، {{Cssxref("bottom")}} و {{Cssxref("left")}} و نیز ویژگی‌های منطقی مبتنی بر جریان مثل {{cssxref("inset-block-start")}}، {{cssxref("inset-block-end")}}، {{cssxref("inset-inline-start")}} و {{cssxref("inset-inline-end")}} استفاده کرد.

## Syntax

```css
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;

/* Global values */
position: inherit;
position: initial;
position: revert;
position: revert-layer;
position: unset;
```

### Values

این ویژگی با یکی از کلمات کلیدی زیر مقداردهی می‌شود:

- `static`
  - : موقعیت عنصر بر اساس [جریان عادی](/en-US/docs/Learn_web_development/Core/CSS_layout/Introduction#normal_layout_flow) (Normal Flow) سند تعیین می‌شود. ویژگی‌های {{cssxref("top")}}، {{cssxref("right")}}، {{cssxref("bottom")}}، {{cssxref("left")}} و {{cssxref("z-index")}} _هیچ تأثیری_ ندارند. این مقدار پیش‌فرض است.
- `relative`
  - : موقعیت عنصر ابتدا بر اساس جریان عادی سند مشخص می‌شود و سپس نسبت به خودش با استفاده از مقادیر `top`، `right`، `bottom` و `left` جابجا می‌گردد. این جابجایی بر محل قرارگیری سایر عناصر تأثیری نمی‌گذارد؛ بنابراین فضای اختصاص‌یافته به عنصر در چیدمان صفحه دقیقاً همان فضایی خواهد بود که اگر `position` برابر با `static` می‌بود.

این مقدار زمانی که `z-index` برابر با `auto` نباشد، یک [stacking context](/en-US/docs/Web/CSS/Guides/Positioned_layout/Stacking_context) جدید ایجاد می‌کند. تأثیر آن روی المنت‌های `table-*-group`، `table-row`، `table-column`، `table-cell` و `table-caption` تعریف‌نشده است.

- `absolute`
  - : المنت از جریان عادی سند خارج می‌شود و هیچ فضایی برای آن در چیدمان صفحه در نظر گرفته نمی‌شود. المنت نسبت به نزدیک‌ترین جد position‌دار (در صورت وجود) یا نسبت به [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block#identifying_the_containing_block) اولیه جای‌گذاری می‌شود. موقعیت نهایی آن با مقادیر `top`، `right`، `bottom` و `left` تعیین می‌شود.

    این مقدار زمانی که `z-index` برابر با `auto` نباشد، یک [stacking context](/en-US/docs/Web/CSS/Guides/Positioned_layout/Stacking_context) جدید ایجاد می‌کند. حاشیه‌های (margin) باکس‌های دارای position: absolute با حاشیه‌های دیگر [ادغام نمی‌شوند](/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing).

- `fixed`
  - : المنت از جریان عادی سند خارج می‌شود و هیچ فضایی برای آن در چیدمان صفحه در نظر گرفته نمی‌شود. المنت نسبت به [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block#identifying_the_containing_block) اولیه‌اش جای‌گذاری می‌شود که در رسانه‌های بصری همان viewport است. موقعیت نهایی آن با مقادیر `top`، `right`، `bottom` و `left` تعیین می‌شود.

    این مقدار همیشه یک [stacking context](/en-US/docs/Web/CSS/Guides/Positioned_layout/Stacking_context) جدید ایجاد می‌کند. در اسناد چاپی، المنت در _هر صفحه_ در همان موقعیت قرار می‌گیرد.

- `sticky`
  - : المنت ابتدا بر اساس جریان عادی سند جای‌گذاری می‌شود و سپس نسبت به _نزدیک‌ترین جد قابل پیمایش_ و [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block) (نزدیک‌ترین جد در سطح block) بر اساس مقادیر `top`، `right`، `bottom` و `left` جابه‌جا می‌شود. این جابه‌جایی روی موقعیت هیچ المنت دیگری تأثیر نمی‌گذارد.

    این مقدار همیشه یک [stacking context](/en-US/docs/Web/CSS/Guides/Positioned_layout/Stacking_context) جدید ایجاد می‌کند. دقت کنید که یک المنت sticky به نزدیک‌ترین جَدی که «مکانیزم پیمایش» داشته باشد (یعنی زمانی که `overflow` برابر با `hidden`، `scroll`، `auto` یا `overlay` باشد) می‌چسبد، حتی اگر آن جد، نزدیک‌ترین جَد واقعاً پیمایش‌شونده نباشد.

    > [!NOTE]
    > حداقل یکی از ویژگی‌های [inset](/en-US/docs/Web/CSS/Reference/Properties/inset) (مانند {{cssxref("top")}}, {{cssxref("inset-block-start")}}, {{cssxref("right")}}, {{cssxref("inset-inline-end")}} و غیره) باید برای محوری که المنت قرار است sticky شود، روی مقداری غیر از `auto` تنظیم شود. اگر هر دو ویژگی inset در یک محور روی `auto` باشند، در آن محور مقدار `sticky` همانند `relative` رفتار می‌کند.

## توضیحات

### انواع position

- یک **عنصر position‌دار (positioned element)** عنصری است که مقدار [محاسبه‌شده (computed)](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) ویژگی `position` در آن یکی از مقادیر `relative`، `absolute`، `fixed` یا `sticky` باشد. (به عبارت دیگر، هر چیزی غیر از `static`.)
- یک **عنصر با position نسبی (relatively positioned element)** عنصری است که مقدار [محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) ویژگی `position` در آن `relative` باشد. ویژگی‌های `top` و `bottom` جابه‌جایی عمودی نسبت به موقعیت عادی عنصر را مشخص می‌کنند؛ ویژگی‌های `left` و `right` نیز جابه‌جایی افقی را مشخص می‌کنند.
- یک **عنصر با position مطلق (absolutely positioned element)** عنصری است که مقدار [محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) ویژگی `position` در آن `absolute` یا `fixed` باشد. ویژگی‌های `top`، `right`، `bottom` و `left` فاصله از لبه‌های [بلوک دربرگیرنده](/en-US/docs/Web/CSS/Guides/Display/Containing_block) (containing block) را مشخص می‌کنند. (بلوک دربرگیرنده همان اجدادی است که عنصر نسبت به آن موقعیت‌دهی می‌شود.) اگر عنصر دارای margin باشد، مقدار آن به این فاصله اضافه می‌شود. این عنصر برای محتوای خود یک [بافتار قالب‌بندی بلوکی](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) (BFC) جدید ایجاد می‌کند.
- یک **عنصر با position چسبنده (stickily positioned element)** عنصری است که مقدار [محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) ویژگی `position` در آن `sticky` باشد. این عنصر تا زمانی که [بلوک دربرگیرنده](/en-US/docs/Web/CSS/Guides/Display/Containing_block)‌اش از یک آستانهٔ مشخص (مانند تنظیم `top` روی مقداری غیر از `auto`) در ریشهٔ جریان (flow root) (یا محفظه‌ای که در آن اسکرول می‌کند) عبور نکند، مانند یک عنصر با position نسبی رفتار می‌کند. پس از عبور از آن آستانه، تا زمانی که به لبهٔ مقابل بلوک دربرگیرنده‌اش برسد، در جای خود «چسبیده» می‌ماند.

در بیشتر مواقع، عناصر دارای position مطلق که ویژگی‌های `height` و `width` آنها روی `auto` تنظیم شده باشد، به‌گونه‌ای اندازه‌دهی می‌شوند که با محتوایشان متناسب باشند. با این حال، می‌توان عناصر position مطلقِ [غیر جایگزین](/en-US/docs/Glossary/Replaced_elements) (non-replaced) را با تعیین هم‌زمان `top` و `bottom` و تنظیم `height` روی `auto` (یا مشخص نکردن آن) وادار کرد که فضای عمودی موجود را پر کنند. به همین ترتیب، می‌توان با تعیین هم‌زمان `left` و `right` و رها کردن `width` روی `auto`، آنها را وادار به پر کردن فضای افقی موجود کرد.

به جز موردی که توضیح داده شد (پر کردن فضای موجود توسط عناصر position مطلق):

- اگر هر دو ویژگی `top` و `bottom` مشخص شده باشند (از نظر فنی، روی `auto` نباشند)، `top` اولویت دارد.
- اگر هر دو ویژگی `left` و `right` مشخص شده باشند، وقتی {{Cssxref("direction")}} برابر با `ltr` باشد (مانند انگلیسی، ژاپنی افقی و غیره) `left` اولویت دارد و وقتی `direction` برابر با `rtl` باشد (مانند فارسی، عربی، عبری و غیره) `right` اولویت دارد.

## دسترسی‌پذیری

اطمینان حاصل کنید که عناصری که با مقادیر `absolute` یا `fixed` موقعیت‌دهی شده‌اند، هنگام بزرگ‌نمایی صفحه برای افزایش اندازهٔ متن، محتوای دیگر را نپوشانند.

- [توضیحات MDN دربارهٔ درک WCAG، دستورالعمل 1.4](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Visual Presentation: Understanding SC 1.4.8 | Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-visual-presentation.html)

### کارایی و دسترسی‌پذیری

پیمایش (scroll) عناصری که محتوای `fixed` یا `sticky` دارند می‌تواند مشکلات عملکردی و دسترس‌پذیری ایجاد کند. هنگام اسکرول کاربر، مرورگر باید محتوای sticky یا fixed را در موقعیت جدیدی دوباره ترسیم (repaint) کند. بسته به میزان محتوایی که نیاز به بازترسیم دارد، عملکرد مرورگر و سرعت پردازش دستگاه، ممکن است مرورگر نتواند این بازترسیم‌ها را با نرخ ۶۰ فریم بر ثانیه انجام دهد. چنین وضعیتی می‌تواند به [jank](/en-US/docs/Glossary/Jank) (لرزش و کندی در اسکرول) و مهم‌تر از آن، مشکلات دسترس‌پذیری برای افراد حساس منجر شود. یکی از راه‌حل‌ها این است که با افزودن `will-change: transform` به عناصر position‌دار، آن‌ها را در لایهٔ اختصاصی خود رندر کنید تا سرعت بازترسیم را بهبود بخشد و در نتیجه عملکرد و دسترس‌پذیری را افزایش دهد.

## مثال‌ها

### موقعیت‌دهی نسبی (Relative positioning)

عناصری که با position: relative تنظیم شده‌اند، به اندازه‌ای مشخص از موقعیت عادی خود در سند جابجا می‌شوند، اما این جابجایی روی چیدمان سایر عناصر تأثیر نمی‌گذارد. در مثال زیر توجه کنید که سایر عناصر طوری قرار گرفته‌اند که انگار عنصر "Two" همچنان فضای موقعیت اصلی خود را اشغال کرده است.

#### HTML

```html
<div class="box" id="one">One</div>
<div class="box" id="two">Two</div>
<div class="box" id="three">Three</div>
<div class="box" id="four">Four</div>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

.box {
  display: inline-block;
  width: 100px;
  height: 100px;
  background: red;
  color: white;
}

#two {
  position: relative;
  top: 20px;
  left: 20px;
  background: blue;
}
```

### موقعیت‌دهی مطلق (Absolute positioning)

عناصر `position: relative` در جریان عادی سند باقی می‌مانند. در مقابل، عنصری که با `position: absolute` تنظیم شده باشد، از جریان عادی خارج می‌شود؛ به این معنی که سایر عناصر طوری چیده می‌شوند که انگار این عنصر اصلاً وجود ندارد. عنصر absolute نسبت به _نزدیک‌ترین عنصر والد دارای position_ (یعنی نزدیک‌ترین والدی که position آن `static` نیست) موقعیت‌دهی می‌شود. اگر چنین والدی وجود نداشته باشد، عنصر نسبت به ICB ([initial containing block](https://drafts.csswg.org/css-display/#initial-containing-block)) – بلوک دربرگیرندهٔ عنصر ریشهٔ سند – قرار می‌گیرد.

#### HTML

```html
<h1>Absolute positioning</h1>

<p>
  I am a basic block level element. My adjacent block level elements sit on new
  lines below me.
</p>

<p class="positioned">
  By default we span 100% of the width of our parent element, and we are as tall
  as our child content. Our total width and height is our content + padding +
  border width/height.
</p>

<p>
  We are separated by our margins. Because of margin collapsing, we are
  separated by the width of one of our margins, not both.
</p>

<p>
  inline elements <span>like this one</span> and <span>this one</span> sit on
  the same line as one another, and adjacent text nodes, if there is space on
  the same line. Overflowing inline elements
  <span>wrap onto a new line if possible — like this one containing text</span>,
  or just go on to a new line if not, much like this image will do:
  <img src="https://mdn.github.io/shared-assets/images/examples/long.jpg" />
</p>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

body {
  width: 500px;
  margin: 0 auto;
}

p {
  background: aqua;
  border: 3px solid blue;
  padding: 10px;
  margin: 10px;
}

span {
  background: red;
  border: 1px solid black;
}

.positioned {
  position: absolute;
  background: yellow;
  inset-block-start: 30px;
  inset-inline-start: 30px;
}
```

موقعیت‌دهی `fixed` شبیه به موقعیت‌دهی `absolute` است، با این تفاوت که [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block) عنصر، همان بلوک دربرگیرندهٔ اولیه‌ای است که توسط _viewport_ ایجاد می‌شود، مگر اینکه یکی از اجداد عنصر، ویژگی `transform`، `perspective` یا `filter` را روی مقداری غیر از `none` تنظیم کرده باشد (مشاهدهٔ [fixed positioning containing block](https://drafts.csswg.org/css-position/#fixed-positioning-containing-block)). در این صورت، آن جد جایگزین [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block) عنصر می‌شود. از این قابلیت می‌توان برای ساخت عنصری «شناور» استفاده کرد که بدون توجه به اسکرول، در یک جای ثابت باقی می‌ماند. در مثال زیر، جعبهٔ «One» در فاصلهٔ 80 پیکسل از بالای صفحه و 10 پیکسل از سمت چپ ثابت شده است. حتی پس از اسکرول، همچنان نسبت به viewport در همان مکان باقی می‌ماند. همچنین، زمانی که ویژگی `will-change` روی `transform` تنظیم شود، یک containing block جدید ایجاد می‌شود.

#### HTML

```html
<div class="outer">
  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam congue tortor
    eget pulvinar lobortis. Vestibulum ante ipsum primis in faucibus orci luctus
    et ultrices posuere cubilia Curae; Nam ac dolor augue. Pellentesque mi mi,
    laoreet et dolor sit amet, ultrices varius risus. Nam vitae iaculis elit.
    Aliquam mollis interdum libero. Sed sodales placerat egestas. Vestibulum ut
    arcu aliquam purus viverra dictum vel sit amet mi. Duis nisl mauris, aliquam
    sit amet luctus eget, dapibus in enim. Sed velit augue, pretium a sem
    aliquam, congue porttitor tortor. Sed tempor nisl a lorem consequat, id
    maximus erat aliquet. Sed sagittis porta libero sed condimentum. Aliquam
    finibus lectus nec ante congue rutrum. Curabitur quam quam, accumsan id
    ultrices ultrices, tempor et tellus.
  </p>
  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam congue tortor
    eget pulvinar lobortis. Vestibulum ante ipsum primis in faucibus orci luctus
    et ultrices posuere cubilia Curae; Nam ac dolor augue. Pellentesque mi mi,
    laoreet et dolor sit amet, ultrices varius risus. Nam vitae iaculis elit.
    Aliquam mollis interdum libero. Sed sodales placerat egestas. Vestibulum ut
    arcu aliquam purus viverra dictum vel sit amet mi. Duis nisl mauris, aliquam
    sit amet luctus eget, dapibus in enim. Sed velit augue, pretium a sem
    aliquam, congue porttitor tortor. Sed tempor nisl a lorem consequat, id
    maximus erat aliquet. Sed sagittis porta libero sed condimentum. Aliquam
    finibus lectus nec ante congue rutrum. Curabitur quam quam, accumsan id
    ultrices ultrices, tempor et tellus.
  </p>
  <div class="box" id="one">One</div>
</div>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

.box {
  width: 100px;
  height: 100px;
  background: red;
  color: white;
}

#one {
  position: fixed;
  top: 80px;
  left: 10px;
  background: blue;
}

.outer {
  width: 500px;
  height: 300px;
  overflow: scroll;
  padding-left: 150px;
}
```

### موقعیت‌دهی `sticky`

قانون CSS زیر عنصری با شناسهٔ `one` را به‌صورت نسبی در جای خود نگه می‌دارد تا زمانی که viewport به اندازه‌ای اسکرول شود که فاصلهٔ عنصر از بالای صفحه 10 پیکسل شود. پس از عبور از این آستانه، عنصر در فاصلهٔ 10 پیکسل از بالای viewport ثابت می‌ماند.

```css
#one {
  position: sticky;
  top: 10px;
}
```

#### فهرست با سرعنوان‌های `sticky`

یکی از کاربردهای رایج موقعیت‌دهی `sticky` برای سرعنوان‌ها در یک فهرست الفبایی است. سرعنوان «B» درست زیر مواردی که با «A» شروع می‌شوند نمایش داده می‌شود تا زمانی که آن موارد از صفحه خارج شوند. به جای اینکه این سرعنوان نیز همراه با سایر محتوا از صفحه خارج شود، در بالای viewport ثابت می‌ماند تا زمانی که تمام موارد «B» از دید خارج شوند؛ در این لحظه سرعنوان «C» جای آن را می‌پوشاند و این روند ادامه پیدا می‌کند.

برای اینکه sticky positioning مطابق انتظار عمل کند، باید حداقل یکی از مشخصه‌های `top`، `right`، `bottom` یا `left` را به‌عنوان آستانه (threshold) تعیین کنید. در غیر این صورت، تفاوتی با relative positioning نخواهد داشت.

#### لیستی با عناوین چسبنده

##### HTML

```html
<dl>
  <div>
    <dt>A</dt>
    <dd>Andrew W.K.</dd>
    <dd>Apparat</dd>
    <dd>Arcade Fire</dd>
    <dd>At The Drive-In</dd>
    <dd>Aziz Ansari</dd>
  </div>
  <div>
    <dt>C</dt>
    <dd>Chromeo</dd>
    <dd>Common</dd>
    <dd>Converge</dd>
    <dd>Crystal Castles</dd>
    <dd>Cursive</dd>
  </div>
  <div>
    <dt>E</dt>
    <dd>Explosions In The Sky</dd>
  </div>
  <div>
    <dt>T</dt>
    <dd>Ted Leo &amp; The Pharmacists</dd>
    <dd>T-Pain</dd>
    <dd>Thrice</dd>
    <dd>TV On The Radio</dd>
    <dd>Two Gallants</dd>
  </div>
</dl>
```

##### CSS

```css
* {
  box-sizing: border-box;
}

dl > div {
  background: white;
  padding-top: 24px;
}

dt {
  background: #b8c1c8;
  border-bottom: 1px solid #989ea4;
  border-top: 1px solid #717d85;
  color: white;
  font:
    bold 18px/21px "Helvetica",
    "Arial",
    sans-serif;
  margin: 0;
  padding: 2px 0 0 12px;
  position: -webkit-sticky;
  position: sticky;
  top: -1px;
}

dd {
  font:
    bold 20px/45px "Helvetica",
    "Arial",
    sans-serif;
  margin: 0;
  padding-left: 12px;
  white-space: nowrap;
}

dd + dd {
  border-top: 1px solid #cccccc;
}
```

##### نتیجه

#### موقعیت‌دهی چسبنده با تعیین تمام مرزهای inset

مثال زیر رفتار یک عنصر را وقتی تمام مرزهای inset تعیین شده‌اند نشان می‌دهد. در اینجا دو ایموجی لامپ (💡) در یک پاراگراف داریم. لامپ‌ها از موقعیت‌دهی چسبنده (sticky) استفاده می‌کنند و مرزهای inset به‌صورت ۵۰px از بالا و پایین و ۱۰۰px از چپ و راست مشخص شده‌اند. یک پس‌زمینه خاکستری روی عنصر والد div ناحیه inset را مشخص می‌کند.

##### HTML

```html
Use scrollbars to put the light bulbs(💡) in the right place in the following
text:
<div>
  <p>
    The representation of an idea by a light bulb(<span class="bulb">💡</span>)
    is a commonly used metaphor that symbolizes the moment of inspiration or the
    birth of a new idea. The association between a light bulb and an idea can be
    traced back to the invention of the incandescent light bulb(<span
      class="bulb"
      >💡</span
    >) by Thomas Edison in the late 19th century. The light bulb is a powerful
    symbol because it represents illumination, clarity, and the sudden
    brightening of one's thoughts or understanding. When someone has an idea, it
    is often described as a light bulb turning on in their mind, signifying a
    moment of insight or creativity. The image of a light bulb also suggests the
    idea of energy, power, and the potential for growth and development.
  </p>
</div>
```

##### CSS

```css hidden
div {
  width: 400px;
  height: 200px;
  overflow: scroll;
  scrollbar-width: thin;
  font-size: 16px;
  font-family: "Verdana";
  border: 1px solid;
}

p {
  width: 600px;
  user-select: none;
  margin: 0;
  border: 110px solid transparent;
}
```

```css
.bulb {
  position: sticky;
  inset: 50px 100px;
}

div {
  /* mark area defined by the inset boundaries using gray color */
  background: linear-gradient(#99999999, #99999999) 100px 50px / 192px 100px
    no-repeat;
}
```

##### نتیجه

وقتی هر دو لامپ را در جای مناسب خود قرار دهید، می‌بینید که درون ناحیه inset به‌صورت نسبی (relative) جای‌گذاری می‌شوند. اما به‌محض خروج از ناحیه inset، در همان جهت به مرز inset می‌چسبند (fixed/sticky).

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- [آموزش CSS: موقعیت‌‌دهی (Positioning)](/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning)
- [ویژگی‌های inset برای چیدمان موقعیت‌یافته](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values/Floating_and_positioning#example_inset_properties_for_positioned_layout)
- [چیدمان موقعیت‌یافته CSS](/en-US/docs/Web/CSS/Guides/Positioned_layout) ماژول‌ها