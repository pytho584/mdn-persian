---
title: "grid CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid"
translated_by: "n8n + AI"
---

ویژگی **`grid`** [CSS](/en-US/docs/Web/CSS) یک [ویژگی خلاصه (shorthand property)](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) است که تمام ویژگی‌های grid صریح و ضمنی را در یک اعلان مشخص می‌کند.

با استفاده از `grid` می‌توانید یک محور را با {{cssxref("grid-template-rows")}} یا {{cssxref("grid-template-columns")}} مشخص کنید و سپس نحوه تکرار خودکار محتوا در محور دیگر را با استفاده از ویژگی‌های ضمنی grid یعنی {{cssxref("grid-auto-rows")}}، {{cssxref("grid-auto-columns")}} و {{cssxref("grid-auto-flow")}} تعیین کنید.

### نمونه تعاملی

```css
grid: auto-flow / 1fr 1fr 1fr;
```

```css
grid: auto-flow dense / 40px 40px 1fr;
```

```css
grid: repeat(3, 80px) / auto-flow;
```

```html
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

```css
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
> ویژگی‌های فرعی که مشخص نکنید، مانند معمول برای shorthandها، به مقدار اولیه خود تنظیم می‌شوند. همچنین، ویژگی‌های فاصله (gutter) با این shorthand بازنشانی نمی‌شوند.

## ویژگی‌های تشکیل‌دهنده

این ویژگی برای ویژگی‌های زیر shorthand محسوب می‌شود:

- {{cssxref("grid-auto-columns")}}
- {{cssxref("grid-auto-flow")}}
- {{cssxref("grid-auto-rows")}}
- {{cssxref("grid-template-areas")}}
- {{cssxref("grid-template-columns")}}
- {{cssxref("grid-template-rows")}}

## Syntax

```css
/* مقادیر <'grid-template'> */
grid: none;
grid: "a" 100px "b" 1fr;
grid: [line-name1] "a" 100px [line-name2];
grid: "a" 200px "b" min-content;
grid: "a" minmax(100px, max-content) "b" 20%;
grid: 100px / 200px;
grid: minmax(400px, min-content) / repeat(auto-fill, 50px);

/* مقادیر <'grid-template-rows'> /
   [ auto-flow && dense? ] <'grid-auto-columns'>? */
grid: 200px / auto-flow;
grid: 30% / auto-flow dense;
grid: repeat(3, 200px) / auto-flow 300px;
grid: [line1] minmax(20em, max-content) / auto-flow dense 40%;

/* مقادیر [ auto-flow && dense? ] <'grid-auto-rows'>? /
   <'grid-template-columns'> */
grid: auto-flow / 200px;
grid: auto-flow dense / 30%;
grid: auto-flow 300px / repeat(3, 200px);
grid: auto-flow dense 40% / [line1] minmax(20em, max-content);

/* مقادیر سراسری */
grid: inherit;
grid: initial;
grid: revert;
grid: revert-layer;
grid: unset;
```

### Values

- `<'grid-template'>`
  - : ویژگی {{cssxref("grid-template")}} شامل {{cssxref("grid-template-columns")}}، {{cssxref("grid-template-rows")}} و {{cssxref("grid-template-areas")}} را تعریف می‌کند.
- `<'grid-template-rows'> / [ auto-flow && dense? ] <'grid-auto-columns'>?`
  - : با مشخص‌کردن صریح مسیرهای ردیف از طریق ویژگی {{cssxref("grid-template-rows")}} (و تنظیم {{cssxref("grid-template-columns")}} روی `none`) و مشخص‌کردن نحوه تکرار خودکار مسیرهای ستون از طریق {{cssxref("grid-auto-columns")}} (و تنظیم {{cssxref("grid-auto-rows")}} روی `auto`) یک جریان خودکار ایجاد می‌کند. همچنین {{cssxref("grid-auto-flow")}} متناسباً روی `column` تنظیم می‌شود و اگر `dense` مشخص شده باشد، آن نیز لحاظ می‌شود.

    سایر ویژگی‌های فرعی `grid` به مقادیر اولیه خود بازنشانی می‌شوند.

- `[ auto-flow && dense? ] <'grid-auto-rows'>? / <'grid-template-columns'>`
  - : با مشخص‌کردن صریح مسیرهای ستون از طریق ویژگی {{cssxref("grid-template-columns")}} (و تنظیم {{cssxref("grid-template-rows")}} روی `none`) و مشخص‌کردن نحوه تکرار خودکار مسیرهای ردیف از طریق {{cssxref("grid-auto-rows")}} (و تنظیم {{cssxref("grid-auto-columns")}} روی `auto`) یک جریان خودکار ایجاد می‌کند. همچنین {{cssxref("grid-auto-flow")}} متناسباً روی `row` تنظیم می‌شود و اگر `dense` مشخص شده باشد، آن نیز لحاظ می‌شود.

    سایر ویژگی‌های فرعی `grid` به مقادیر اولیه خود بازنشانی می‌شوند.

- `[ auto-flow && dense? ] <'grid-auto-rows'>? / <'grid-template-columns'>`
  - : با تنظیم صریح مسیرهای ستونی از طریق پراپرتی `grid-template-columns` (و پراپرتی `grid-template-rows` روی `none`) و مشخص‌سازی نحوۀ تکرار خودکار مسیرهای سطری با `grid-auto-rows` (و تنظیم `grid-auto-columns` روی `auto`)، یک جریان خودکار (auto-flow) ایجاد می‌کند. همچنین مطابق انتظار `grid-auto-flow` روی `row` تنظیم می‌شود و در صورت مشخص‌شدن، `dense` نیز اعمال می‌شود.

    تمام زیرپراپرتی‌های دیگر `grid` به مقادیر اولیه‌شان بازنشانی می‌شوند.

## مثال‌ها

### ایجاد یک طرح‌بندی گرید

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

#### نتیجه

## همچنین ببینید

- [قرارگیری مبتنی بر خط با CSS Grid](/en-US/docs/Web/CSS/Guides/Grid_layout/Line-based_placement)
- [نواحی الگوی گرید: شورت‌هندهای تعریف گرید](/en-US/docs/Web/CSS/Guides/Grid_layout/Grid_template_areas#grid_definition_shorthands)