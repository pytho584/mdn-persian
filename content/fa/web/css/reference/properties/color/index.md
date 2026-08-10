---
title: "color CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/color"
translated_by: "n8n + AI"
---

ویژگی **`color`** در [CSS](/en-US/docs/Web/CSS) رنگ پیش‌زمینهٔ متن و [تزئینات متن](/en-US/docs/Web/CSS/Reference/Properties/text-decoration) یک عنصر را تعیین می‌کند و همچنین مقدار [`currentColor`](/en-US/docs/Web/CSS/Reference/Values/color_value#currentcolor_keyword) را تنظیم می‌کند. `currentColor` می‌تواند به‌عنوان یک مقدار غیرمستقیم در _سایر_ ویژگی‌ها استفاده شود و مقدار پیش‌فرض برای ویژگی‌های رنگی دیگر مانند {{cssxref("border-color")}} است.

برای یک نمای کلی از کار با رنگ در HTML، به [اعمال رنگ به عناصر HTML با استفاده از CSS](/en-US/docs/Web/CSS/Guides/Colors/Applying_color) مراجعه کنید.

```css interactive-example-choice
color: rebeccapurple;
```

```css interactive-example-choice
color: #00a400;
```

```css interactive-example-choice
color: rgb(214 122 127);
```

```css interactive-example-choice
color: hsl(30deg 82% 43%);
```

```css interactive-example-choice
color: hsl(237deg 74% 33% / 61%);
```

```css interactive-example-choice
color: hwb(152deg 0% 58% / 70%);
```

```html interactive-example
<section id="default-example">
  <div class="example-container">
    <p id="example-element">
      London. Michaelmas term lately over, and the Lord Chancellor sitting in
      Lincoln's Inn Hall. Implacable November weather.
    </p>
  </div>
</section>
```

```css interactive-example
#example-element {
  font-size: 1.5em;
}

.example-container {
  background-color: white;
  padding: 10px;
}
```

## نحوهٔ نوشتن

```css
/* مقادیر کلیدی */
color: currentColor;

/* مقادیر <named-color> */
color: red;
color: orange;
color: tan;
color: rebeccapurple;

/* مقادیر <hex-color> */
color: #090;
color: #009900;
color: #090a;
color: #009900aa;

/* مقادیر <rgb()> و نسخهٔ قدیمی <rgba()> */
color: rgb(34, 12, 64);
color: rgb(34, 12, 64, 0.6);
color: rgba(34, 12, 64, 0.6);
color: rgb(34 12 64 / 0.6);
color: rgba(34 12 64 / 0.6);
color: rgb(34.6 12 64 / 60%);
color: rgba(34.6 12 64 / 60%);

/* مقادیر <hsl()> و نسخهٔ قدیمی <hsla()> */
color: hsl(30, 100%, 50%);
color: hsl(30, 100%, 50%, 0.6);
color: hsla(30, 100%, 50%, 0.6);
color: hsl(30 100% 50% / 0.6);
color: hsla(30 100% 50% / 0.6);
color: hsl(30.2 100% 50% / 60%);
color: hsla(30.2 100% 50% / 60%);

/* مقادیر <hwb()> */
color: hwb(90 10% 10%);
color: hwb(90 10% 10% / 0.5);
color: hwb(90deg 10% 10%);
color: hwb(1.5708rad 60% 0%);
color: hwb(0.25turn 0% 40% / 50%);

/* مقادیر سراسری */
color: inherit;
color: initial;
color: revert;
color: revert-layer;
color: unset;
```

ویژگی `color` به‌صورت یک مقدار تکی از نوع {{cssxref("&lt;color&gt;")}} تعیین می‌شود.

توجه کنید که مقدار باید یک رنگ یکنواخت باشد. نمی‌تواند یک {{cssxref("gradient")}} باشد که در واقع نوعی {{cssxref("image")}} محسوب می‌شود.

### مقادیر

- {{cssxref("&lt;color&gt;")}}
  - : رنگ قسمت‌های متنی و تزئینی عنصر را تنظیم می‌کند.
- [`currentColor`](/en-US/docs/Web/CSS/Reference/Values/color_value#currentcolor_keyword)
  - : رنگ را به مقدار ویژگی `color` خود عنصر تنظیم می‌کند. اما اگر به‌عنوان مقدار `color` استفاده شود، `currentColor` مانند `inherit` رفتار می‌کند.

## دسترسی‌پذیری

اطمینان از اینکه نسبت کنتراست بین رنگ متن و پس‌زمینه‌ای که متن روی آن قرار دارد به‌اندازهٔ کافی بالا باشد، بسیار مهم است تا افرادی که دچار کم‌بینایی هستند بتوانند محتوای صفحه را بخوانند.

نسبت کنتراست رنگ با مقایسهٔ درخشندگی مقادیر رنگ متن و پس‌زمینه تعیین می‌شود. برای مطابقت با [راهنمای دسترسی به محتوای وب (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/)، نسبت ۴.۵:۱ برای محتوای متنی و ۳:۱ برای متن‌های بزرگ مانند عنوان‌ها الزامی است. متن بزرگ به‌عنوان ۱۸.۶۶ پیکسل و [پررنگ](/en-US/docs/Web/CSS/Reference/Properties/font-weight) یا بزرگ‌تر، یا ۲۴ پیکسل یا بزرگ‌تر تعریف می‌شود.

- [WebAIM: بررسی‌کننده کنتراست رنگ](https://webaim.org/resources/contrastchecker/)
- [راهنمای MDN برای درک WCAG، توضیحات معیار 1.4](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [درک معیار موفقیت 1.4.3 | W3C درک WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)

## تعریف رسمی

## نحو رسمی

## مثال‌ها

### قرمز کردن متن

روش‌های زیر همگی باعث قرمز شدن متن پاراگراف می‌شوند:

```css
p {
  color: red;
}
p {
  color: #f00;
}
p {
  color: #ff0000;
}
p {
  color: rgb(255 0 0);
}
p {
  color: rgb(100% 0% 0%);
}
p {
  color: hsl(0 100% 50%);
}

/* ۵۰٪ نیمه‌شفاف */
p {
  color: #ff000080;
}
p {
  color: rgb(255 0 0 / 50%);
}
p {
  color: hsl(0 100% 50% / 50%);
}
```

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- نوع داده {{cssxref("&lt;color&gt;")}}
- ویژگی‌های دیگر مرتبط با رنگ: {{cssxref("background-color")}}، {{cssxref("border-color")}}، {{cssxref("outline-color")}}، {{cssxref("text-decoration-color")}}، {{cssxref("text-emphasis-color")}}، {{cssxref("text-shadow")}}، {{cssxref("caret-color")}}، {{cssxref("column-rule-color")}} و {{cssxref("print-color-adjust")}}
- صفت SVG {{SVGAttr("color")}}
- تابع {{CSSXref("color_value/color")}}
- [اعمال رنگ به عناصر HTML با استفاده از CSS](/en-US/docs/Web/CSS/Guides/Colors/Applying_color)
- [WCAG: کنتراست رنگ](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast)