---
title: "background CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/background"
translated_by: "n8n + AI"
---

## `background` ویژگی CSS

ویژگی **`background`** یک [کوتاه‌نویس](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) در [CSS](/en-US/docs/Web/CSS) است که تمام ویژگی‌های مربوط به پس‌زمینه را (مانند رنگ، تصویر، مبدأ، اندازه و شیوهٔ تکرار) به‌طور هم‌زمان تنظیم می‌کند.

```css interactive-example-choice
background: green;
```

```css interactive-example-choice
background: content-box radial-gradient(crimson, skyblue);
```

```css interactive-example-choice
background: no-repeat url("/shared-assets/images/examples/lizard.png");
```

```css interactive-example-choice
background: left 5% / 15% 60% repeat-x
  url("/shared-assets/images/examples/star.png");
```

```css interactive-example-choice
background:
  center / contain no-repeat
    url("/shared-assets/images/examples/firefox-logo.svg"),
  #eeeeee 35% url("/shared-assets/images/examples/lizard.png");
```

```html interactive-example
<section id="default-example">
  <div id="example-element"></div>
</section>
```

```css interactive-example
#example-element {
  min-width: 100%;
  min-height: 100%;
  padding: 10%;
}
```

## ویژگی‌های تشکیل‌دهنده

این ویژگی کوتاه‌نویسی برای ویژگی‌های زیر است:

- {{cssxref("background-attachment")}}
- {{cssxref("background-clip")}}
- {{cssxref("background-color")}}
- {{cssxref("background-image")}}
- {{cssxref("background-origin")}}
- {{cssxref("background-position")}}
- {{cssxref("background-repeat")}}
- {{cssxref("background-size")}}

## سینتکس

```css
/* استفاده از یک <background-color> */
background: green;

/* استفاده از یک <bg-image> و <repeat-style> */
background: url("test.jpg") repeat-y;

/* استفاده از یک <visual-box> و <'background-color'> */
background: border-box red;

/* یک تصویر، وسط‌چین شده و مقیاس‌بندی شده */
background: no-repeat center/80% url("../img/image.png");

/* مقادیر سراسری */
background: inherit;
background: initial;
background: revert;
background: revert-layer;
background: unset;
```

### مقادیر

- `<attachment>`
  - : نحوهٔ چسبیدن (پیوستگی) تصویر پس‌زمینه را مشخص می‌کند. به {{cssxref("background-attachment")}} مراجعه کنید. پیش‌فرض: `scroll`.
- `<visual-box>`
  - : ناحیه‌ای که عملیات برش (clip) و مبدأ (origin) پس‌زمینه را تعیین می‌کند. به {{cssxref("background-clip")}} و {{cssxref("background-origin")}} مراجعه کنید. مقادیر پیش‌فرض به ترتیب `border-box` و `padding-box` است.
- `<'background-color'>`
  - : رنگ پس‌زمینه را تعیین می‌کند. به {{cssxref("background-color")}} مراجعه کنید. پیش‌فرض: `transparent`.
- `<bg-image>`
  - : تصویر پس‌زمینه را مشخص می‌کند. به {{cssxref("background-image")}} مراجعه کنید. پیش‌فرض: `none`.
- `<bg-position>`
  - : موقعیت تصویر پس‌زمینه را تعیین می‌کند. به {{cssxref("background-position")}} مراجعه کنید. پیش‌فرض: `0% 0%`.
- `<repeat-style>`
  - : نحوهٔ تکرار تصویر پس‌زمینه را تعیین می‌کند. به {{cssxref("background-repeat")}} مراجعه کنید. پیش‌فرض: `repeat`.
- `<bg-size>`
  - : اندازهٔ تصویر پس‌زمینه را مشخص می‌کند. به {{cssxref("background-size")}} مراجعه کنید. پیش‌فرض: `auto`.

## توضیحات

ویژگی کوتاه‌نویس `background` به شما امکان می‌دهد تمام ویژگی‌های پس‌زمینه را در یک اعلان واحد مشخص کنید. پس‌زمینه در زیر محتوای یک عنصر قرار می‌گیرد. هنگامی که چند مقدار پس‌زمینه دارید که با ویرگول از هم جدا شده‌اند، هر کدام یک لایهٔ پس‌زمینه را تشکیل می‌دهند و لایه‌های بعدی روی لایه‌های قبلی رسم می‌شوند.

ویژگی `background` به‌صورت یک یا چند لایه (که با ویرگول جدا می‌شوند) مشخص می‌شود. هر لایه می‌تواند صفر، یک یا دو مؤلفهٔ `<visual-box>` و صفر یا یک مؤلفه از نوع `<attachment>`، `<bg-image>`، `<bg-position>`، `<bg-size>` و `<repeat-style>` داشته باشد. اگر دو مقدار برای `<bg-position>`، `<bg-size>` یا `<repeat-style>` داده شود، مقدار اول برای محور افقی و مقدار دوم برای محور عمودی در نظر گرفته می‌شود. اگر تنها یک مقدار بنویسید، همان مقدار برای هر دو بعد اعمال می‌شود.

مؤلفهٔ `<'background-color'>` فقط می‌تواند در آخرین لایهٔ پس‌زمینه ظاهر شود.

ویژگی‌های جزئی‌ای که در اعلان کوتاه‌نویس `background` مقداردهی نشده‌اند، به مقادیر پیش‌فرض خود بازمی‌گردند.

### ترتیب ویژگی‌های تشکیل‌دهنده

از آنجا که برخی از ویژگی‌های تشکیل‌دهنده نوع مقادیر مشترکی دارند، ترتیب آن‌ها در shorthand اهمیت پیدا می‌کند.

مقدار `<bg-size>` باید بلافاصله بعد از `<bg-position>` و با جداکنندهٔ `/` بیاید. برای نمونه: `10px 10px / 80% 80%` یعنی تصویر پس‌زمینه ۸۰٪ ارتفاع و ۸۰٪ عرض element را می‌پوشاند و در فاصلهٔ `10px` از بالا و `10px` از چپ گوشهٔ بالا-چپ element قرار می‌گیرد. در `<bg-position>`، اگر هر دو مقدار طول باشند، یا یکی طول و دیگری `center`، اولین مقدار موقعیت افقی و دومی موقعیت عمودی را تعیین می‌کند.

هر لایهٔ پس‌زمینه می‌تواند صفر، یک یا دو مقدار [`<visual-box>`](/en-US/docs/Web/CSS/Reference/Values/box-edge#visual-box) داشته باشد. اگر فقط یک مقدار بیاید، هم {{cssxref("background-origin")}} و هم {{cssxref("background-clip")}} را تنظیم می‌کند. اگر دو مقدار وجود داشته باشد، اولی `background-origin` و دومی `background-clip` را مشخص می‌کند. اگر هیچ مقدار `<visual-box>`ای نباشد، `background-origin` به `padding-box` و `background-clip` به `border-box` پیش‌فرض می‌شود.

برای دیگر ویژگی‌های پس‌زمینه الزامی در ترتیب وجود ندارد، اما ترتیب زیر برای یکدستی و خوانایی توصیه می‌شود؛ به خاطر داشته باشید که هیچ‌کدام از این مقادیر اجباری نیستند:

`<bg-image> <bg-position> / <bg-size> <repeat-style> <attachment> <bg-clip> <bg-origin> <'background-color'>`

`background` زیر دقیقاً تمام مقادیر پیش‌فرض را با همین ترتیب مشخص می‌کند:

```css
background: none 0% 0% / auto auto repeat scroll border-box padding-box
  transparent;
```

سه خط CSS زیر با خط بالا معادل هستند، حتی اگر ترتیب متفاوت باشد:

```css
background: none;
background: transparent;
background: repeat scroll 0% 0% / auto padding-box border-box none transparent;
```

### ترتیب نمایش تصاویر

اگر چند پس‌زمینه که با ویرگول جدا شده‌اند تعریف شوند، چند لایهٔ پس‌زمینه روی هم ایجاد می‌کنند. اولین پس‌زمینه در لیست، لایهٔ بالایی را می‌سازد. اگر لایهٔ بالایی ناحیهٔ شفافی نداشته باشد، تنها همان لایه دیده خواهد شد.

آخرین لایه، لایهٔ زیرین است. رنگ پس‌زمینه همواره در این لایه قرار می‌گیرد.

### اعمال پس‌زمینهٔ body روی کل سند

اگر مقدار محاسبه‌شدهٔ `background-image` برای عنصر {{htmlelement("html")}} (ریشه `:root`) برابر با `none` و `background-color` آن `transparent` باشد، مرورگر استایل‌های `background` تنظیم‌شده روی {{htmlelement("body")}} را به `:root` منتقل می‌کند و با `<body>` چنان رفتار می‌کند که گویی `background: initial` تنظیم شده است. به عبارت دیگر، عنصر `<html>` تمام استایل‌های `background` مربوط به `<body>` را دریافت می‌کند و ویژگی‌های پس‌زمینهٔ `<body>` به مقادیر اولیهٔ خود بازمی‌گردند.

به همین دلیل، نویسندگان مشخصه توصیه می‌کنند استایل‌های پس‌زمینهٔ سند را در بلوک `body` تنظیم کنید، نه در `html`. با این حال توجه داشته باشید که استفاده از containment این رفتار را غیرفعال می‌کند. وقتی ویژگی {{cssxref("contain")}} روی `<html>` یا `<body>` مقداری غیر از `none` داشته باشد، ویژگی `background` و تمام زیرویژگی‌های آن از `<body>` به عنصر ریشه `<html>` انتشار نمی‌یابند.

## Accessibility

مرورگرها اطلاعات خاصی دربارهٔ تصاویر پس‌زمینه در اختیار فناوری‌های کمکی قرار نمی‌دهند. این موضوع به‌ویژه برای صفحه‌خوان‌ها اهمیت دارد، زیرا صفحه‌خوان حضور تصویر را اعلام نمی‌کند و در نتیجه چیزی به کاربر منتقل نمی‌شود. اگر تصویر حاوی اطلاعاتی است که برای درک هدف کلی صفحه ضروری است، بهتر است آن را به‌صورت مفهومی درون سند توصیف کنید.

- [توضیحات راهنمای ۱.۱ درک WCAG از MDN](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.1_%E2%80%94_providing_text_alternatives_for_non-text_content)
- [Understanding Success Criterion 1.1.1 | درک WCAG 2.0 از W3C](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)

## نمونه‌ها

### تنظیم پس‌زمینه با کلمات کلیدی رنگی و تصاویر

#### HTML

```html
<p class="top-banner">
  Starry sky<br />
  Twinkle twinkle<br />
  Starry sky
</p>
<p class="warning">Here is a paragraph</p>
<p></p>
```

#### CSS

```css
.warning {
  background: pink;
}

.top-banner {
  background: url("star-solid.gif") #9999ff repeat-y fixed;
}
```

## همچنین ببینید

- {{cssxref("box-decoration-break")}}
- [Using gradients](/en-US/docs/Web/CSS/Guides/Images/Using_gradients)
- [Using multiple backgrounds](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Using_multiple_backgrounds)