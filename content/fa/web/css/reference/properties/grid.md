---
title: "grid CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid"
translated_by: "n8n + AI"
---

The **`grid`** CSS property یک [shorthand property](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) است که تمام خصوصیات شبکه (explicit و implicit) را در یک اعلام واحد تنظیم می‌کند.

با استفاده از `grid` شما یک محور را با `grid-template-rows` یا `grid-template-columns` مشخص می‌کنید، سپس مشخص می‌کنید که محتوا در محور دیگر چگونه به‌صورت خودکار تکرار شود با استفاده از خصوصیات شبکهٔ ضمنی: `grid-auto-rows`، `grid-auto-columns`، و `grid-auto-flow`.

```css interactive-example-choice
grid: auto-flow / 1fr 1fr 1fr;
```

```css interactive-example-choice
grid: auto-flow dense / 40px 40px 1fr;
```

```css interactive-example-choice
grid: repeat(3, 80px) / auto-flow;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="example-container">
    <div class="transition-all" id="example-element">
      <div>One</div>
      <div>Two</div>
      <div>Three</div>
    </div>
  </div>
</section>
```

```css interactive-example
#example-element {
  border: 1px solid #c5c5c5;
  display: grid;
  grid-gap: 10px;
  width: 200px;
}

#example-element :nth-child(1) {
  background-color: rgb(0 0 255 / 0.2);
  border: 3px solid blue;
}

#example-element :nth-child(2) {
  background-color: rgb(255 0 200 / 0.2);
  border: 3px solid rebeccapurple;
  grid-column: auto / span 3;
  grid-row: auto / span 2;
}

#example-element :nth-child(3) {
  background-color: rgb(94 255 0 / 0.2);
  border: 3px solid green;
  grid-column: auto / span 2;
}
```

> [!NOTE]
> زیر-خصوصیات (sub-properties) که مشخص نکنید طبق معمول شورت‌هنگ‌ها به مقدار اولیهٔ خود بازگردانده می‌شوند. همچنین، خصوصیات گاتر (gutter) توسط این شورت‌هنگ بازنشانی (reset) نمی‌شوند.

## Constituent properties

این خصوصیت یک شورت‌هنگ برای خصوصیات CSS زیر است:

- `grid-auto-columns`
- `grid-auto-flow`
- `grid-auto-rows`
- `grid-template-areas`
- `grid-template-columns`
- `grid-template-rows`

## Syntax

```css
/* <'grid-template'> values */
grid: none;
grid: "a" 100px "b" 1fr;
grid: [line-name1] "a" 100px [line-name2];
grid: "a" 200px "b" min-content;
grid: "a" minmax(100px, max-content) "b" 20%;
grid: 100px / 200px;
grid: minmax(400px, min-content) / repeat(auto-fill, 50px);

/* <'grid-template-rows'> /
   [ auto-flow && dense? ] <'grid-auto-columns'>? values */
grid: 200px / auto-flow;
grid: 30% / auto-flow dense;
grid: repeat(3, 200px) / auto-flow 300px;
grid: [line1] minmax(20em, max-content) / auto-flow dense 40%;

/* [ auto-flow && dense? ] <'grid-auto-rows'>? /
   <'grid-template-columns'> values */
grid: auto-flow / 200px;
grid: auto-flow dense / 30%;
grid: auto-flow 300px / repeat(3, 200px);
grid: auto-flow dense 40% / [line1] minmax(20em, max-content);

/* Global values */
grid: inherit;
grid: initial;
grid: revert;
grid: revert-layer;
grid: unset;
```

### Values

- `<'grid-template'>`
  - : تعریف‌کنندهٔ `grid-template` شامل `grid-template-columns`، `grid-template-rows` و `grid-template-areas`.
- `<'grid-template-rows'> / [ auto-flow && dense? ] <'grid-auto-columns'>?`
  - : یک auto-flow را راه‌اندازی می‌کند با تنظیم مسیرهای ردیف به‌صورت صریح از طریق `grid-template-rows` (و تنظیم `grid-template-columns` به `none`) و مشخص کردن چگونگی تکرار خودکار مسیرهای ستون از طریق `grid-auto-columns` (و تنظیم `grid-auto-rows` به `auto`). همچنین `grid-auto-flow` مطابقاً به `column` تنظیم می‌شود، و اگر `dense` مشخص شده باشد همراه با آن خواهد بود.

    تمام زیر-خصوصیات دیگر `grid` به مقادیر اولیهٔ خود بازنشانی می‌شوند.

- `[ auto-flow && dense? ] <'grid-auto-rows'>? / <'grid-template-columns'>`
  - : با تعیین صریح ترک‌های ستون از طریق `grid-template-columns` (و تعیین `grid-template-rows` به `none`) و مشخص کردن چگونگی تکرار خودکار ترک‌های ردیف از طریق `grid-auto-rows` (و تنظیم `grid-auto-columns` به `auto`)، یک جریان خودکار (auto-flow) راه‌اندازی می‌کند. `grid-auto-flow` نیز مطابقاً روی `row` تنظیم می‌شود، و اگر مشخص شده باشد، `dense` نیز اعمال می‌گردد.

    همهٔ زیر‌ویژگی‌های دیگر `grid` به مقادیر اولیهٔ خود بازنشانی می‌شوند.

## Formal definition

## Formal syntax

## Examples

### Creating a grid layout

#### HTML

```html
<div id="container">
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
#container {
  display: grid;
  grid: repeat(2, 60px) / auto-flow 80px;
}

#container > div {
  background-color: #8ca0ff;
  width: 50px;
  height: 50px;
}
```

#### Result

## Specifications

## Browser compatibility

## See also

- `grid-template`
- `grid-template-rows`
- `grid-template-columns`
- `grid-template-areas`
- `grid-auto-columns`
- `grid-auto-rows`
- `grid-auto-flow`
- [Line-based placement with CSS grid](/en-US/docs/Web/CSS/Guides/Grid_layout/Line-based_placement)
- [Grid template areas: grid definition shorthands](/en-US/docs/Web/CSS/Guides/Grid_layout/Grid_template_areas#grid_definition_shorthands)