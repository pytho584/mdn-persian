---
title: "flex-direction CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/flex-direction"
translated_by: "n8n + AI"
---

# ویژگی `flex-direction` در CSS

ویژگی **`flex-direction`** در CSS نحوه چیدمان آیتم‌های flex درون یک flex container را مشخص می‌کند و محور اصلی (main axis) و جهت (عادی یا برعکس) را تعریف می‌کند.

## نحوه نوشتن

```css
/* مقدارهای کلیدی */
flex-direction: row;
flex-direction: row-reverse;
flex-direction: column;
flex-direction: column-reverse;

/* مقدارهای سراسری */
flex-direction: inherit;
flex-direction: initial;
flex-direction: revert;
flex-direction: revert-layer;
flex-direction: unset;
```

### مقادیر

این ویژگی یکی از مقدارهای کلیدی زیر را می‌پذیرد:

- `row`
  - : محور اصلی flex container را هم‌جهت با جهت نوشتار (text direction) قرار می‌دهد. این مقدار پیش‌فرض است.
- `row-reverse`
  - : مانند `row` عمل می‌کند، اما ترتیب آیتم‌ها برعکس می‌شود؛ اولین آیتم در لبه `inline-end` قرار می‌گیرد.
- `column`
  - : محور اصلی flex container را هم‌جهت با محور block (block-axis) تنظیم می‌کند.
- `column-reverse`
  - : مانند `column` عمل می‌کند، اما جهت محتوا برعکس می‌شود؛ اولین آیتم در لبه `block-end` قرار می‌گیرد.

## توضیحات

با استفاده از `flex-direction` می‌توانید محور اصلی container و جهت چیدمان آیتم‌های flex را مشخص کنید. این ویژگی فقط روی عناصری تأثیر دارد که ویژگی {{cssxref("display")}} آن‌ها روی `flex` یا `inline-flex` تنظیم شده باشد. بهتر است `flex-direction` را به‌همراه {{CSSXRef("flex-wrap")}} و از طریق ویژگی خلاصه {{CSSXRef("flex-flow")}} مقداردهی کنید.

وقتی `flex-direction` روی یک flex container تنظیم شود، تعیین می‌کند که آیتم‌های flex در همان جهت متن (هم‌راستا) یا عمود بر آن (در جهت block) چیده شوند و اینکه ترتیب آن‌ها عادی باشد یا برعکس.

مقدار پیش‌فرض `row` است. با این مقدار (چه صریحاً تنظیم شود یا به‌صورت پیش‌فرض)، محور اصلی flex container همان جهت نوشتار (متن) خواهد بود. اولین آیتم flex بر اساس ترتیب DOM در گوشه `inline-start` و `block-start` قرار می‌گیرد. آیتم‌های بعدی در لبه `inline-end` آیتم قبلی چیده می‌شوند. اگر container با `flex-wrap: wrap` تنظیم شده باشد، ردیف‌های اضافی در لبه `block-end` اضافه می‌شوند. نقاط **main-start** و **main-end** با جهت محتوا یکسان هستند؛ main-start برابر با لبه `inline-start` و main-end برابر با لبه `inline-end` است. نقاط **cross-start** و **cross-end** نیز به‌ترتیب لبه‌های `block-start` و `block-end` هستند.

مقدار `row-reverse` جهت inline را معکوس می‌کند و مانند `row` اما برعکس عمل می‌کند. اولین آیتم در لبه `inline-end` و `block-start` قرار می‌گیرد و آیتم‌های بعدی در لبه `inline-start` آیتم قبلی. ردیف‌های اضافی همچنان در لبه `block-end` اضافه می‌شوند. در این حالت main-start و main-end به‌ترتیب لبه‌های `inline-end` و `inline-start` هستند (برعکس حالت عادی) و cross-start و cross-end همان لبه‌های `block-start` و `block-end` باقی می‌مانند.

مقدار `column` محور اصلی را در راستای block (عمود بر جهت نوشتار) قرار می‌دهد. در این حالت اولین آیتم در گوشه `inline-start` و `block-start` قرار می‌گیرد و آیتم‌ها در راستای block (پایین صفحه در حالت عادی) چیده می‌شوند. اگر container قابلیت wrap داشته باشد، ستون‌های اضافی در راستای inline (معمولاً سمت راست) ایجاد می‌شوند.

مقدار `column-reverse` همان رفتار `column` را دارد، اما جهت block برعکس می‌شود: اولین آیتم در لبه `block-end` (پایین) قرار می‌گیرد و آیتم‌های بعدی به سمت بالا چیده می‌شوند.

وقتی `flex-direction` برابر با `column` باشد، محور اصلی (main axis) همان محور بلوکی (block axis) است. مثل حالت `row`، اولین آیتم در لبهٔ `inline-start` و `block-start` قرار می‌گیرد، اما آیتم‌های بعدی به‌جای کنار هم چیده شدن، زیر آیتم قبلی (در لبهٔ `block-end`) جای می‌گیرند. اگر امکان شکستن خط (wrap) وجود داشته باشد، ستون‌های اضافی در سمت `inline-end` افزوده می‌شوند. نقاط **main-start** و **main-end** بر اساس جهت بلوکی مد نوشتاری تعیین می‌شوند: main-start همان لبهٔ `block-start` و main-end همان لبهٔ `block-end` است. همچنین cross-start و cross-end به ترتیب لبه‌های `inline-start` و `inline-end` هستند.

با مقدار `column-reverse` محور اصلی همچنان بلوکی است، اما ترتیب از لبهٔ `block-end` شروع می‌شود. اولین آیتم در لبهٔ `inline-start` و `block-end` قرار می‌گیرد و آیتم‌های بعدی بالای آیتم قبلی (لبهٔ `block-start`) چیده می‌شوند. اگر شکستن خط فعال باشد، ستون‌های جدید در سمت `inline-end` اضافه می‌شوند. در این حالت **main-start** همان `block-end` و **main-end** همان `block-start` است؛ cross-start و cross-end نیز به ترتیب `inline-start` و `inline-end` هستند.

مقادیر `row` و `row-reverse` تحت تأثیر جهت‌دار بودن flex container قرار می‌گیرند. اگر ویژگی [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir) برابر با `ltr` باشد، `row` محور افقی از چپ به راست و `row-reverse` از راست به چپ را نشان می‌دهد. اگر `dir` برابر با `rtl` باشد، `row` محور افقی از راست به چپ و `row-reverse` از چپ به راست خواهد بود.

## دسترسی‌پذیری

استفاده از مقادیر `row-reverse` یا `column-reverse` برای ویژگی `flex-direction` باعث ایجاد ناهماهنگی میان چیدمان بصری و ترتیب DOM می‌شود. این موضوع تجربهٔ کاربران کم‌بینا را که با فناوری‌های کمکی مثل screen reader صفحه را مرور می‌کنند، تحت تأثیر منفی قرار می‌دهد. اگر ترتیب بصری (CSS) مهم باشد، کاربران screen reader به ترتیب درست خوانش دسترسی نخواهند داشت.

- [Source Order Matters](https://adrianroselli.com/2015/09/source-order-matters.html) نوشتهٔ Adrian Roselli (2015)
- [Flexbox & the keyboard navigation disconnect](https://tink.uk/flexbox-the-keyboard-navigation-disconnect/) نوشتهٔ Léonie Watson (2016)
- [Understanding SC 1.3.2: Meaningful Sequence](https://www.w3.org/WAI/WCAG22/Understanding/meaningful-sequence) از طریق WCAG 2.2 (2023)

## مثال‌ها

### معکوس کردن ستون‌ها و ردیف‌های flex container

#### HTML

```html
<h4>This is a Column-Reverse</h4>
<div id="col-rev" class="content">
  <div class="box red">A</div>
  <div class="box lightblue">B</div>
  <div class="box yellow">C</div>
</div>
<h4>This is a Row-Reverse</h4>
<div id="row-rev" class="content">
  <div class="box red">A</div>
  <div class="box lightblue">B</div>
  <div class="box yellow">C</div>
</div>
```

#### CSS

```css
.content {
  width: 200px;
  height: 200px;
  border: 1px solid #c3c3c3;
  display: flex;
}

.box {
  width: 50px;
  height: 50px;
}

#col-rev {
  flex-direction: column-reverse;
}

#row-rev {
  flex-direction: row-reverse;
}

.red {
  background-color: red;
}

.lightblue {
  background-color: lightblue;
}

.yellow {
  background-color: yellow;
}
```

## همچنین ببینید

- کوتاه‌نوشت `flex-flow`
- `flex-wrap`
- `gap`
- [مفاهیم پایه‌ای flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [مرتب‌سازی آیتم‌های flex](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Ordering_items)
- [ماژول چیدمان جعبهٔ انعطاف‌پذیر CSS](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)