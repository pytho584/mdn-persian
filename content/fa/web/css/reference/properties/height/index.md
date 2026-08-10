---
title: "height CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/height"
translated_by: "n8n + AI"
---

```markdown
خاصیت **`height`** در CSS، ارتفاع یک عنصر را مشخص می‌کند. به‌طور پیش‌فرض، این خاصیت ارتفاع [ناحیه محتوا (content area)](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#content_area) را تعیین می‌کند. اما اگر {{cssxref("box-sizing")}} روی `border-box` تنظیم شده باشد، ارتفاع [ناحیه حاشیه (border area)](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#border_area) را مشخص می‌کند.

```css interactive-example-choice
height: 150px;
```

```css interactive-example-choice
height: 6em;
```

```css interactive-example-choice
height: 75%;
```

```css interactive-example-choice
height: auto;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="transition-all" id="example-element">
    This is a box where you can change the height.
  </div>
</section>
```

```css interactive-example
#example-element {
  display: flex;
  flex-direction: column;
  background-color: #5b6dcd;
  justify-content: center;
  color: white;
}
```

خاصیت‌های {{cssxref("min-height")}} و {{cssxref("max-height")}} بر `height` اولویت دارند.

> **نکته:** به‌عنوان یک خاصیت هندسی، `height` روی عناصر SVG مانند {{SVGElement("svg")}}، {{SVGElement("rect")}}، {{SVGElement("image")}} و {{SVGElement("foreignObject")}} نیز اعمال می‌شود. در این موارد مقدار `auto` به `0` تبدیل می‌شود و مقادیر درصدی نسبت به ارتفاع viewport SVG برای `<rect>` محاسبه می‌شوند. مقدار خاصیت CSS `height` بر هر مقدار از ویژگی SVG {{SVGAttr("height")}} که روی عنصر SVG تنظیم شده باشد، اولویت دارد.

## Syntax

```css
/* مقادیر <length> */
height: 120px;
height: 10em;
height: 100vh;
height: anchor-size(height);
height: anchor-size(--my-anchor self-block, 250px);
height: clamp(200px, anchor-size(width));

/* مقدار <percentage> */
height: 75%;

/* مقادیر کلیدواژه‌ای */
height: max-content;
height: min-content;
height: fit-content;
height: fit-content(20em);
height: auto;
height: stretch;

/* مقادیر سراسری */
height: inherit;
height: initial;
height: revert;
height: revert-layer;
height: unset;
```

### مقادیر

- {{cssxref("&lt;length&gt;")}}
  - : ارتفاع را با یک مقدار طولی (مانند px, em) مشخص می‌کند.
- {{cssxref("&lt;percentage&gt;")}}
  - : ارتفاع را به‌صورت درصدی از ارتفاع [بلوک محتوا (containing block)](/en-US/docs/Web/CSS/Guides/Display/Containing_block) تعیین می‌کند.
- `auto`
  - : مرورگر به‌صورت خودکار ارتفاع مناسبی برای عنصر محاسبه و انتخاب می‌کند.
- {{cssxref("max-content")}}
  - : ارتفاع ذاتی ترجیحی (preferred intrinsic height) عنصر.
- {{cssxref("min-content")}}
  - : حداقل ارتفاع ذاتی (minimum intrinsic height) عنصر.
- {{cssxref("fit-content")}}
  - : از فضای موجود استفاده می‌کند، اما بیش از [max-content](/en-US/docs/Web/CSS/Reference/Values/max-content) نیست؛ یعنی `min(max-content, max(min-content, stretch))`.
- [`fit-content(<length-percentage>)`](/en-US/docs/Web/CSS/Reference/Values/fit-content_function)
  - : از فرمول `fit-content` استفاده می‌کند با این تفاوت که فضای موجود با آرگومان داده‌شده جایگزین می‌شود: `min(max-content, max(min-content, <length-percentage>))`.
- `stretch`
  - : ارتفاع [margin box](/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model#parts_of_a_box) عنصر را برابر ارتفاع [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block#identifying_the_containing_block) آن قرار می‌دهد. تلاش می‌کند تا margin box تمام فضای موجود در containing block را پر کند؛ بنابراین رفتاری مشابه `100%` دارد اما اندازه حاصل روی margin box اعمال می‌شود، نه روی جعبه‌ای که توسط [box-sizing](/en-US/docs/Web/CSS/Reference/Properties/box-sizing) تعیین می‌شود.

## دسترسی‌پذیری (Accessibility)

اطمینان حاصل کنید که عناصری که با `height` تنظیم شده‌اند، در هنگام بزرگ‌نمایی صفحه برای افزایش اندازه متن، بریده نشوند یا محتوای دیگر را نپوشانند.
```

- [MDN Understanding WCAG, Guideline 1.4 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.4 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)

## مثال‌ها

### تنظیم ارتفاع با پیکسل و درصد

#### HTML

```html
<div id="taller">I'm 50 pixels tall.</div>
<div id="shorter">I'm 25 pixels tall.</div>
<div id="parent">
  <div id="child">I'm half the height of my parent.</div>
</div>
```

#### CSS

```css
div {
  width: 250px;
  margin-bottom: 5px;
  border: 2px solid blue;
}

#taller {
  height: 50px;
}

#shorter {
  height: 25px;
}

#parent {
  height: 100px;
}

#child {
  height: 50%;
  width: 75%;
}
```

### کشیدن ارتفاع برای پر کردن بلوک دربرگیرنده

#### HTML

```html
<div class="parent">
  <div class="child">text</div>
</div>

<div class="parent">
  <div class="child stretch">stretch</div>
</div>
```

#### CSS

```css hidden
@supports not (height: stretch) {
  body::before {
    content: "Your browser doesn't support the `stretch` value yet.";
    background-color: wheat;
    display: block;
    text-align: center;
    padding: 1rem 0;
  }
}
```

```css
.parent {
  height: 150px;
  margin: 1rem;
  border: solid;
}

.child {
  margin: 1rem;
  background: #00999999;
}

.stretch {
  height: stretch;
}
```

## همچنین ببینید

- {{cssxref("width")}}
- {{cssxref("box-sizing")}}
- {{cssxref("min-height")}}, {{cssxref("max-height")}}
- {{cssxref("block-size")}}, {{cssxref("inline-size")}}
- {{cssxref("anchor-size()")}}
- {{cssxref("clamp()")}}
- {{cssxref("minmax()")}}
- SVG {{SVGAttr("height")}} attribute
- [Introduction to the CSS box model](/en-US/docs/Web/CSS/Guides/Box_model/Introduction)
- [CSS box model](/en-US/docs/Web/CSS/Guides/Box_model) module