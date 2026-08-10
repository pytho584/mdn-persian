---
title: "width CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/width"
translated_by: "n8n + AI"
---

ویژگی `width` در CSS
========================

ویژگی **`width`** در [CSS](/en-US/docs/Web/CSS) عرض یک عنصر را تعیین می‌کند. به‌طور پیش‌فرض، عرض [ناحیهٔ محتوا](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#content_area) را مشخص می‌کند؛ اما اگر مقدار {{cssxref("box-sizing")}} را برابر با `border-box` قرار دهید، آن‌گاه عرض [ناحیهٔ حاشیه](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#border_area) تعیین می‌شود.

مقدار مشخص‌شده برای `width` تا زمانی که در محدودهٔ تعریف‌شده توسط {{cssxref("min-width")}} و {{cssxref("max-width")}} باقی بماند، روی ناحیهٔ محتوا اعمال می‌شود.

- اگر مقدار `width` از `min-width` کوچک‌تر باشد، `min-width` آن را لغو می‌کند.
- اگر مقدار `width` از `max-width` بزرگ‌تر باشد، `max-width` آن را لغو می‌کند.

> [!NOTE]
> از آنجا که `width` یک ویژگی هندسی است، روی عناصر SVG مانند {{SVGElement("svg")}}، {{SVGElement("rect")}}، {{SVGElement("image")}} و {{SVGElement("foreignObject")}} نیز اعمال می‌شود. برای `<svg>` مقدار `auto` معادل `100%` و برای سایر عناصر معادل `0` در نظر گرفته می‌شود. همچنین مقادیر درصدی برای `<rect>` نسبت به عرض viewport SVG محاسبه می‌شوند. مقدار CSS مربوط به `width` هر مقدار مشخصهٔ SVG ({{SVGAttr("width")}}) روی آن عنصر را بازنویسی می‌کند.

## سینتکس

```css
/* <length> values */
width: 300px;
width: 25em;

/* <percentage> value */
width: 75%;

/* Keyword values */
width: max-content;
width: min-content;
width: fit-content;
width: auto;
width: stretch;

/* function values */
width: fit-content(20em);
width: anchor-size(width);
width: anchor-size(--my-anchor inline, 120%);
width: calc-size(max-content, size / 2);

/* Global values */
width: inherit;
width: initial;
width: revert;
width: revert-layer;
width: unset;
```

### مقادیر

- {{cssxref("&lt;length&gt;")}}
  - : عرض را به‌عنوان یک مقدار طولی مشخص می‌کند.
- {{cssxref("&lt;percentage&gt;")}}
  - : عرض را به‌عنوان درصدی از عرض [بلوک دربرگیرنده (containing block)](/en-US/docs/Web/CSS/Guides/Display/Containing_block) تعریف می‌کند.
- `auto`
  - : مرورگر عرض را برای عنصر موردنظر محاسبه و انتخاب می‌کند.
- {{cssxref("max-content")}}
  - : عرض ترجیحی ذاتی (intrinsic preferred width).
- {{cssxref("min-content")}}
  - : عرض حداقل ذاتی (intrinsic minimum width).
- {{cssxref("fit-content")}}
  - : از فضای موجود استفاده می‌کند، اما نه بیشتر از [max-content](/en-US/docs/Web/CSS/Reference/Values/max-content)؛ یعنی `min(max-content, max(min-content, stretch))`.
- {{cssxref("anchor-size()")}}
  - : عرض را نسبت به یک بعد از عنصر لنگر (anchor) تنظیم می‌کند. برای عنصری که با لنگر موقعیت‌دهی شده، پارامتر اول به‌طور پیش‌فرض عرض لنگر مرتبط را می‌گیرد. اگر روی عنصری غیر از آن اعمال شود، عرض را به مقدار fallback تنظیم می‌کند. اگر fallback تعریف نشده باشد، این اعلان نادیده گرفته می‌شود.
- {{cssxref("calc-size()")}}
  - : عرض را به یک اندازه ذاتی اصلاح‌شده تنظیم می‌کند.
- [`fit-content(<length-percentage>)`](/en-US/docs/Web/CSS/Reference/Values/fit-content_function)
  - : از فرمول fit-content استفاده می‌کند، با این تفاوت که فضای موجود با آرگومان مشخص‌شده جایگزین می‌شود و عرض را طبق فرمول `min(maximum size, max(minimum size, <length-percentage>))` محدود می‌کند.
- `stretch`
  - : عرض [margin box](/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model#parts_of_a_box) عنصر را برابر عرض [بلوک دربرگیرنده (containing block)](/en-US/docs/Web/CSS/Guides/Display/Containing_block#identifying_the_containing_block) تنظیم می‌کند. این مقدار سعی می‌کند margin box فضای در دسترس بلوک دربرگیرنده را پر کند، بنابراین به‌نوعی شبیه `100%` عمل می‌کند اما اندازه نهایی را به margin box اعمال می‌کند نه به جعبه‌ای که توسط [box-sizing](/en-US/docs/Web/CSS/Reference/Properties/box-sizing) تعیین می‌شود.

## دسترسی‌پذیری

اطمینان حاصل کنید که عناصری که `width` برای آنها تنظیم شده، هنگام بزرگنمایی صفحه برای افزایش اندازه متن، بریده نشوند و محتوای دیگر را نپوشانند.

- [MDN Understanding WCAG, Guideline 1.4 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.4 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)

## مثال‌ها

### عرض پیش‌فرض

این مثال کاربرد پایه و مقدار پیش‌فرض `auto` را نشان می‌دهد.

#### HTML

دو پاراگراف قرار می‌دهیم؛ یکی با یک نام کلاس.

```html
<p>The MDN community writes really great documentation.</p>
<p class="has-width">The MDN community writes really great documentation.</p>
```

#### CSS

همه پاراگراف‌ها را با پس‌زمینه طلایی تنظیم می‌کنیم و به‌صراحت `width` پاراگراف دوم را `auto` می‌کنیم.

```css
p {
  background: gold;
}
p.has-width {
  width: auto;
}
```

#### نتیجه

از آنجا که مقدار پیش‌فرض `width` برابر `auto` است، هر دو پاراگراف عرض یکسانی دارند.

### استفاده از واحدهای طول

این مثال مقادیر طولی عرض را نشان می‌دهد.

#### HTML

دو عنصر {{htmlelement("div")}} همراه با کمی متن قرار می‌دهیم.

```html
<div class="px_length">Width measured in px</div>
<div class="em_length">Width measured in em</div>
```

#### CSS

عرض عنصر `px_length` برابر `200px` و عنصر `em_length` برابر `20em` تنظیم می‌شود. همچنین هر دو عنصر مقادیر متفاوتی برای `background-color`، `color` و `border` دارند تا هنگام نمایش بتوان آنها را از هم تشخیص داد.

```css
.px_length {
  width: 200px;

  background-color: red;
  color: white;
  border: 1px solid black;
}

.em_length {
  width: 20em;

  background-color: white;
  color: red;
  border: 1px solid black;
}
```

#### نتیجه

عنصر `px_length` همیشه ۲۰۰ پیکسل عرض خواهد داشت. عرض رندر شدهٔ عنصر `em_length` به اندازه فونت بستگی دارد.

### استفاده از مقادیر درصدی

این مثال نحوه استفاده از مقادیر درصدی را نشان می‌دهد.

#### HTML

یک عنصر `<div>` به همراه متنی درون آن قرار می‌دهیم.

```html
<div class="percent">Width in percentage</div>
```

#### CSS

عرض (`width`) عنصر را برابر با `۲۰٪` عرض والدش تنظیم می‌کنیم.

```css
.percent {
  width: 20%;

  background-color: silver;
  border: 1px solid red;
}
```

#### نتیجه

### استفاده از اندازه‌های ذاتی

این مثال `max-content` و `min-content` را مقایسه می‌کند و `calc-size` را معرفی می‌کند.

#### HTML

سه پاراگراف با محتوای یکسان قرار می‌دهیم؛ فقط نام کلاس‌ها متفاوت است.

```html
<p class="max-green">The MDN community writes really great documentation.</p>
<p class="min-blue">The MDN community writes really great documentation.</p>
<p class="min-pink">The MDN community writes really great documentation.</p>
```

#### CSS

عرض (`width`) یک پاراگراف را `max-content`، دیگری را `min-content` و سومی را با استفاده از تابع `calc-size()` دو برابر `min-content` تنظیم می‌کنیم. به هر کدام `background-color` و `border-style` متفاوتی می‌دهیم تا قابل تشخیص باشند.

```css
p.max-green {
  width: max-content;

  background-color: lightgreen;
  border-style: dotted;
}

p.min-blue {
  width: min-content;

  background-color: lightblue;
  border-style: dashed;
}

p.min-pink {
  width: calc-size(min-content, size * 2);

  background-color: pink;
  border-style: solid;
}
```

```css hidden
@supports not (width: calc-size(min-content, size * 2)) {
  body::before {
    content: "Your browser doesn't support the calc-size() function yet.";
    background-color: wheat;
    display: block;
    text-align: center;
    padding: 1rem 0;
  }
}
```

#### نتیجه

مثال `max-content` به اندازهٔ پهنای متن کشیده می‌شود. مثال `min-content` به اندازهٔ پهنای بلندترین کلمه است. مقدار `calc-size()` طوری تنظیم شده که دو برابر `min-content` باشد.

### استفاده از کلمه کلیدی `stretch`

این مثال مقدار `stretch` را درون یک ظرف [flex](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) نشان می‌دهد.

#### HTML

یک والد به همراه دو فرزند قرار می‌دهیم.

```html
<div class="parent">
  <div class="child">text</div>
  <div class="child stretch">stretch</div>
</div>
```

#### CSS

با استفاده از ویژگی `display` والد را به یک ظرف flex تبدیل کرده و عرض فرزند دوم را برابر `stretch` قرار می‌دهیم.

```css
.parent {
  border: solid;
  margin: 1rem;
  display: flex;
}

.child {
  background: #00999999;
  margin: 1rem;
}

.stretch {
  width: stretch;
}
```

```css hidden
@supports not (width: stretch) {
  body::before {
    content: "Your browser doesn't support the stretch value yet.";
    background-color: wheat;
    display: block;
    text-align: center;
    padding: 1rem 0;
  }
}
```

#### نتیجه

به طور پیش‌فرض، آیتم‌های flex به اندازهٔ محتوای خود عریض هستند. مقدار `stretch` باعث می‌شود عنصر تا جایی که فضای موجود اجازه می‌دهد عریض شود، در غیر این صورت باکس margin آن محدود به عرض بلوک دربرگیرنده‌اش می‌ماند.

### استفاده از تابع `anchor-size()`

این مثال استفاده از تابع `anchor-size()` برای تعریف عرض یک عنصر position شده با anchor را نشان می‌دهد؛ عرض را چند برابر ارتفاع anchor تنظیم کرده‌ایم.

#### HTML

دو عنصر `<div>` تعریف می‌کنیم: یک عنصر `anchor` و یک عنصر `infobox` که نسبت به anchor موقعیت‌دهی می‌شود.

```html
<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>Infobox.</p>
</div>
```

#### CSS

مقادیر `anchor-name` و `position` را مشخص کرده و سپس از تابع `anchor-size()` درون مقدار `width` استفاده می‌کنیم.

```css
.anchor {
  anchor-name: --my-anchor;
  width: fit-content;
  border: 1px solid;
}

.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  left: anchor(right);
  top: anchor(top);
  width: calc(anchor-size(height) * 2);
  border: 1px solid;
}
```

ما عنصر `anchor` را که یک `<div>` است، با اختصاص دادن {{cssxref("anchor-name")}} به عنوان عنصر anchor معرفی می‌کنیم. عنصر موقعیت‌دهی‌شده، ویژگی {{cssxref("position")}} خود را روی `absolute` تنظیم کرده و از طریق ویژگی {{cssxref("position-anchor")}} به عنصر anchor مرتبط می‌شود. همچنین ابعاد `height` و `width` مطلق را برای anchor تعیین می‌کنیم و عرض عنصر anchor-positioned را با استفاده از تابع `anchor-size()` به‌عنوان مقدار ویژگی `width`، برابر با عرض anchor قرار می‌دهیم. به‌عنوان یک ویژگی اضافه، از تابع `anchor-size()` برای تعیین موقعیت {{cssxref("left")}} infobox هم استفاده می‌کنیم تا فاصلهٔ بین anchor و infobox، یک‌چهارم ارتفاع anchor شود.

```css hidden
.anchor {
  anchor-name: --my-anchor;
  width: 120px;
  height: 60px;

  font-size: 2rem;
  background-color: lightpink;
  text-align: center;
  align-content: center;
  outline: 1px solid black;
}

.infobox {
  position-anchor: --my-anchor;
  position: absolute;
  position-area: right;
  width: anchor-size(width);

  left: calc( anchor-size(height) / 4 )

  align-content: center;
  color: darkblue;
  background-color: azure;
  outline: 1px solid #dddddd;
}
```

```css hidden
body {
  padding: 5em;
}

@supports not (width: anchor-size(width)) {
  body::before {
    content: "Your browser doesn't support the anchor-size() function value.";
    background-color: wheat;
    display: block;
    text-align: center;
    padding: 1rem 0;
  }
}
```

#### نتایج

توجه کنید که عرض infobox همیشه با عرض عنصر anchor یکسان است.

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- {{cssxref("height")}}
- {{cssxref("box-sizing")}}
- {{cssxref("min-width")}}, {{cssxref("max-width")}}
- {{cssxref("block-size")}}, {{cssxref("inline-size")}}
- ویژگی SVG {{SVGAttr("width")}}
- [معرفی مدل جعبه‌ای CSS](/en-US/docs/Web/CSS/Guides/Box_model/Introduction) راهنما
- ماژول [مدل جعبه‌ای CSS](/en-US/docs/Web/CSS/Guides/Box_model)
- ماژول [موقعیت‌دهی با anchor در CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning)
- ماژول [مقادیر و واحدهای CSS](/en-US/docs/Web/CSS/Guides/Values_and_units)