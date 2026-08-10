---
title: "background-color CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/background-color"
translated_by: "n8n + AI"
---

ویژگی **`background-color`** در [CSS](/en-US/docs/Web/CSS) رنگ پس‌زمینه یک element را تنظیم می‌کند.

## Syntax

```css
/* مقادیر کلیدواژه‌ای */
background-color: red;
background-color: indigo;

/* مقدار هگزادسیمال */
background-color: #bbff00; /* کاملاً مات */
background-color: #bf0; /* خلاصه‌شده کاملاً مات */
background-color: #11ffee00; /* کاملاً شفاف */
background-color: #1fe0; /* خلاصه‌شده کاملاً شفاف */
background-color: #11ffeeff; /* کاملاً مات */
background-color: #1fef; /* خلاصه‌شده کاملاً مات */

/* مقدار RGB */
background-color: rgb(255 255 128); /* کاملاً مات */
background-color: rgb(117 190 218 / 50%); /* ۵۰٪ شفاف */

/* مقدار HSL */
background-color: hsl(50 33% 25%); /* کاملاً مات */
background-color: hsl(50 33% 25% / 75%); /* ۷۵٪ مات، یعنی ۲۵٪ شفاف */

/* مقادیر کلیدواژه‌ای ویژه */
background-color: currentColor;
background-color: transparent;

/* مقادیر سراسری */
background-color: inherit;
background-color: initial;
background-color: revert;
background-color: revert-layer;
background-color: unset;
```

### Values

این ویژگی به‌صورت یک مقدار `<color>` مشخص می‌شود:

- {{cssxref("&lt;color&gt;")}}
  - : رنگ یکنواخت پس‌زمینه. این رنگ در پشت هر تصویر پس‌زمینه‌ای که با {{cssxref("background-image")}} مشخص شده باشد رسم می‌شود، با این حال اگر تصویر شفافیت داشته باشد، رنگ همچنان از میان آن دیده خواهد شد.

## Description

ویژگی `background-color` رنگ پس‌زمینه یک باکس element را تنظیم می‌کند. رنگ در پشت هر تصویر پس‌زمینه رسم می‌شود. به‌طور پیش‌فرض، رنگ پس‌زمینه درون [border-box](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#border_area) رسم می‌شود، به این معنی که پشت border رسم می‌شود و تا لبه بیرونی border-box ادامه می‌یابد.

برش ناحیه رسم `background-color` توسط ویژگی {{cssxref("background-clip")}} کنترل می‌شود. اگر چندین تصویر پس‌زمینه تنظیم شده باشد، برش رنگ پس‌زمینه بر اساس مقدار `background-clip` مربوط به پایین‌ترین تصویر پس‌زمینه تعیین می‌شود.

## Accessibility

اطمینان از اینکه نسبت کنتراست بین رنگ پس‌زمینه و رنگ متنی که روی آن قرار می‌گیرد به اندازه کافی بالا باشد، اهمیت دارد تا افرادی که دچار کم‌بینایی هستند بتوانند محتوای صفحه را بخوانند. نسبت کنتراست بالا همچنین دسترسی‌پذیری محتوا را برای کاربران دستگاه‌های همراه با صفحه‌نمایش براق در محیط‌های روشن مانند نور خورشید بهبود می‌بخشد.

نسبت کنتراست رنگ با مقایسه درخشندگی (luminance) مقادیر رنگ متن و پس‌زمینه تعیین می‌شود. برای مطابقت با [رهنمودهای دسترسی‌پذیری محتوای وب (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/)، نسبت ۴.۵:۱ برای محتوای متنی و ۳:۱ برای متن‌های بزرگتر مانند عناوین الزامی است. متن بزرگ به متنی با اندازه ۱۸.۶۶ پیکسل و [bold](/en-US/docs/Web/CSS/Reference/Properties/font-weight) یا بزرگتر، یا ۲۴ پیکسل یا بزرگتر تعریف می‌شود.

- [درک WCAG: راهنمای 1.4.3 قابل درک](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [درک کنتراست رنگ](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast)
- [درک کنتراست رنگ](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast)
- [WebAIM: بررسی‌کننده کنتراست رنگ](https://webaim.org/resources/contrastchecker/)
- [درک معیار موفقیت 1.4.3 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)

## مثال‌ها

### مثال ساده

این مثال نحوه اعمال `background-color` به عنصر HTML `<p>` را با استفاده از مقدارهای مختلف `<color>` در CSS نشان می‌دهد.

#### HTML

```html
<p class="example-one">Lorem ipsum dolor sit amet, consectetuer</p>

<p class="example-two">Lorem ipsum dolor sit amet, consectetuer</p>

<p class="example-three">Lorem ipsum dolor sit amet, consectetuer</p>
```

#### CSS

هر پاراگراف یک رنگ پس‌زمینه متفاوت می‌گیرد؛ از جمله تنظیم صریح پیش‌فرض `transparent`، تابع رنگی `rgb()` و یک `hex-color`. همچنین برای اطمینان از کنتراست کافی بین متن و پس‌زمینه، ویژگی `color` را هم مقداردهی کرده‌ایم.

```css
.example-one {
  background-color: transparent;
}

.example-two {
  background-color: rgb(153 102 153);
  color: rgb(255 255 204);
}

.example-three {
  background-color: #777799;
  color: white;
}
```

#### نتیجه

با اعمال این کدها، سه پاراگراف با رنگ پس‌زمینه شفاف، ارغوانی روشن با متن نخودی، و طوسی مایل به بنفش با متن سفید نمایش داده می‌شوند.

### جداول رنگی

این مثال نحوه به‌کارگیری `background-color` روی عناصر `<table>`، ردیف‌های `<tr>` و سلول‌های `<td>` را نشان می‌دهد. همچنین مشخص می‌کند که رنگ پس‌زمینه چگونه پشت حاشیه‌ها کشیده می‌شود.

#### HTML

```html
<table>
  <tbody>
    <tr id="r1">
      <td id="c11">11</td>
      <td id="c12">12</td>
      <td id="c13">13</td>
    </tr>
    <tr id="r2">
      <td id="c21">21</td>
      <td id="c22">22</td>
      <td id="c23">23</td>
    </tr>
    <tr id="r3">
      <td id="c31">31</td>
      <td id="c32">32</td>
      <td id="c33">33</td>
    </tr>
  </tbody>
</table>
```

#### CSS

با CSS چندین مقدار `named-color` را تنظیم می‌کنیم. همچنین یک حاشیه خط‌چین ضخیم برای جدول و هر سلول تعریف کرده‌ایم تا نشان دهیم `background-color` تا لبه بیرونی border-box رنگ می‌شود.

```css
table {
  border-collapse: collapse;
  border: dashed black 5px;
  width: 250px;
  height: 150px;
}
td {
  border: dashed 5px black;
}
#r1 {
  background-color: lightblue;
}
#c12 {
  background-color: cyan;
}
#r2 {
  background-color: grey;
}
#r3 {
  background-color: olive;
}
```

#### نتیجه

خروجی جدولی است که ردیف اول آن آبی روشن شده و سلول میانی آن فیروزه‌ای است؛ ردیف دوم طوسی و ردیف سوم زیتونی دیده می‌شود. رنگ پس‌زمینه تا زیر حاشیه‌های خط‌چین ادامه دارد.

## همچنین ببینید

- [`background-clip`](/en-US/docs/Web/CSS/background-clip)
- [پس‌زمینه‌های چندگانه](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Using_multiple_backgrounds)
- نوع داده `<color>`
- سایر ویژگی‌های مرتبط با رنگ: [`color`](/en-US/docs/Web/CSS/color), [`border-color`](/en-US/docs/Web/CSS/border-color), [`outline-color`](/en-US/docs/Web/CSS/outline-color), [`text-decoration-color`](/en-US/docs/Web/CSS/text-decoration-color), [`text-emphasis-color`](/en-US/docs/Web/CSS/text-emphasis-color), [`text-shadow`](/en-US/docs/Web/CSS/text-shadow), [`caret-color`](/en-US/docs/Web/CSS/caret-color), و [`column-rule-color`](/en-US/docs/Web/CSS/column-rule-color)