---
title: "border CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/border"
translated_by: "n8n + AI"
---

ویژگی **`border`** یک [shorthand](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) در CSS است که حاشیهٔ یک عنصر را مشخص می‌کند. این ویژگی مقادیر `border-width`, `border-style` و `border-color` را در خود جای می‌دهد.

## ویژگی‌های زیرمجموعه

این ویژگی خلاصه‌ای از ویژگی‌های زیر است:

- `border-width`
- `border-style`
- `border-color`

## نحوهٔ نوشتن

```css
/* فقط سبک */
border: solid;

/* عرض | سبک */
border: 2px dotted;

/* سبک | رنگ */
border: outset #ff3333;

/* عرض | سبک | رنگ */
border: medium dashed green;

/* مقادیر سراسری */
border: inherit;
border: initial;
border: revert;
border: revert-layer;
border: unset;
```

ویژگی `border` را می‌توان با یک، دو یا سه مقدار از فهرست زیر تعیین کرد. ترتیب این مقادیر مهم نیست.

> [!NOTE]
> اگر سبک (style) حاشیه تعریف نشود، حاشیه دیده نخواهد شد، زیرا مقدار پیش‌فرض سبک `none` است.

### مقادیر

- `<line-width>`
  - : ضخامت حاشیه را مشخص می‌کند. اگر ذکر نشود، مقدار پیش‌فرض `medium` در نظر گرفته می‌شود. به `border-width` مراجعه کنید.
- `<line-style>`
  - : سبک حاشیه را مشخص می‌کند. اگر ذکر نشود، مقدار پیش‌فرض `none` است. به `border-style` مراجعه کنید.
- `<color>`
  - : رنگ حاشیه را مشخص می‌کند. اگر ذکر نشود، از `currentColor` استفاده می‌شود. به `border-color` مراجعه کنید.

## توضیحات

مانند همهٔ ویژگی‌های shorthand، هر مقدار فرعی که حذف شود، به [مقدار اولیهٔ](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#initial_value) خود تنظیم می‌شود. نکتهٔ مهم اینکه `border` نمی‌تواند برای مشخص کردن یک مقدار سفارشی برای `border-image` استفاده شود، بلکه آن را به مقدار اولیه‌اش یعنی `none` بازمی‌گرداند.

ویژگی shorthand `border` به‌ویژه وقتی مفید است که بخواهید هر چهار حاشیه یکسان باشند. اما اگر می‌خواهید حاشیه‌ها با یکدیگر تفاوت داشته باشند، می‌توانید از ویژگی‌های منفرد `border-width`, `border-style` و `border-color` استفاده کنید که برای هر طرف مقدار جداگانه‌ای می‌پذیرند. همچنین می‌توانید با ویژگی‌های فیزیکی (مانند `border-top`) و منطقی (مانند `border-block-start`) حاشیه، یک حاشیه را به‌تنهایی هدف قرار دهید.

### تفاوت حاشیه و outline

حاشیه‌ها و [outline](/en-US/docs/Web/CSS/Reference/Properties/outline)ها بسیار شبیه‌اند، اما outlineها تفاوت‌های زیر را دارند:

- outlineها هیچ فضایی اشغال نمی‌کنند، زیرا بیرون از محتوای عنصر رسم می‌شوند.
- طبق مشخصات، outlineها ملزم به مستطیلی بودن نیستند، هرچند معمولاً مستطیلی‌اند.

## مثال‌ها

### یک حاشیهٔ بیرون‌آمدهٔ صورتی

#### HTML

```html
<div>I have a border, an outline, and a box shadow! Amazing, isn't it?</div>
```

#### CSS

```css
div {
  border: 0.5rem outset pink;
  outline: 0.5rem solid khaki;
  box-shadow: 0 0 0 2rem skyblue;
  border-radius: 12px;
  font: bold 1rem sans-serif;
  margin: 2rem;
  padding: 1rem;
  outline-offset: 0.5rem;
}
```

#### نتیجه

## مشخصات

برای مشاهدهٔ جزئیات دقیق مشخصات فنی این ویژگی، به مستندات اصلی MDN مراجعه کنید.

## سازگاری با مرورگرها

اطلاعات مربوط به پشتیبانی مرورگرها در جدول سازگاری مستندات اصلی MDN در دسترس است.

## همچنین ببینید

- [border-width](/en-US/docs/Web/CSS/border-width)
- [border-style](/en-US/docs/Web/CSS/border-style)
- [border-color](/en-US/docs/Web/CSS/border-color)
- [outline](/en-US/docs/Web/CSS/outline)
- [Backgrounds and borders](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders)
- [Learn CSS: Backgrounds and borders](/en-US/docs/Learn_web_development/Core/Styling_basics/Backgrounds_and_borders)