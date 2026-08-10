---
title: "padding CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/padding"
translated_by: "n8n + AI"
---

# padding

ویژگی **`padding`** در [CSS](/en-US/docs/Web/CSS) یک [ویژگی خلاصه‌نویس (shorthand property)](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) است که فضای داخلی ([padding area](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#padding_area)) چهار طرف یک عنصر را به‌طور هم‌زمان تنظیم می‌کند.

ناحیهٔ padding در یک عنصر، فضای بین محتوای آن و مرز (border) آن است.

> [!NOTE]
> `padding` فضای اضافی را **داخل** عنصر ایجاد می‌کند. در مقابل، {{cssxref("margin")}} فضای اضافی را **دور** عنصر به‌وجود می‌آورد.

## ویژگی‌های سازنده

این ویژگی خلاصه‌ای از ویژگی‌های CSS زیر است:

- {{cssxref("padding-top")}}
- {{cssxref("padding-right")}}
- {{cssxref("padding-bottom")}}
- {{cssxref("padding-left")}}

## نحوهٔ نوشتار (Syntax)

```css
/* اعمال به هر چهار طرف */
padding: 1em;

/* بالا و پایین | چپ و راست */
padding: 5% 10%;

/* بالا | چپ و راست | پایین */
padding: 1em 2em 2em;

/* بالا | راست | پایین | چپ */
padding: 5px 1em 0 2em;

/* مقادیر سراسری */
padding: inherit;
padding: initial;
padding: revert;
padding: revert-layer;
padding: unset;
```

ویژگی `padding` را می‌توان با یک، دو، سه یا چهار مقدار مشخص کرد. هر مقدار می‌تواند از نوع {{cssxref("&lt;length&gt;")}} یا {{cssxref("&lt;percentage&gt;")}} باشد. مقادیر منفی معتبر نیستند.

- اگر **یک** مقدار داده شود، همان مقدار `padding` به **هر چهار طرف** اعمال می‌شود.
- اگر **دو** مقدار داده شود، مقدار اول برای **بالا و پایین** و مقدار دوم برای **چپ و راست** استفاده می‌شود.
- اگر **سه** مقدار داده شود، مقدار اول برای **بالا**، مقدار دوم برای **چپ و راست** و مقدار سوم برای **پایین** به‌کار می‌رود.
- اگر **چهار** مقدار داده شود، ترتیب آن **بالا**، **راست**، **پایین** و **چپ** (جهت عقربه‌های ساعت) خواهد بود.

### مقادیر

- {{cssxref("&lt;length&gt;")}}
  - : اندازهٔ padding به‌صورت یک مقدار ثابت.
- {{cssxref("&lt;percentage&gt;")}}
  - : اندازهٔ padding به‌صورت درصدی نسبت به اندازهٔ درون‌خطی (inline size) [بلوک شامل‌شونده](/en-US/docs/Web/CSS/Guides/Display/Containing_block) (در زبان‌های افقی همان `width` است که توسط {{cssxref("writing-mode")}} تعریف می‌شود).

## مثال‌ها

### تنظیم padding با پیکسل

#### HTML

```html
<h4>این عنصر padding متوسطی دارد.</h4>
<h3>padding در این عنصر بسیار زیاد است!</h3>
```

#### CSS

```css
h4 {
  background-color: lime;
  padding: 20px 50px;
}

h3 {
  background-color: cyan;
  padding: 110px 50px 50px 110px;
}
```

### تنظیم padding با پیکسل و درصد

```css
padding: 5%; /* همه طرف: ۵٪ padding */

padding: 10px; /* همه طرف: ۱۰px padding */

padding: 10px 20px; /* بالا و پایین: ۱۰px padding */
/* چپ و راست: ۲۰px padding   */

padding: 10px 3% 20px; /* بالا:               ۱۰px padding */
/* چپ و راست:         ۳٪ padding   */
/* پایین:             ۲۰px padding */
```

```
padding: 1em 3px 30px 5px; /* top:    1em padding  */
/* right:  3px padding  */
/* bottom: 30px padding */
/* left:   5px padding  */
```

## همچنین ببینید

- [`padding-top`](/en-US/docs/Web/CSS/padding-top)، [`padding-right`](/en-US/docs/Web/CSS/padding-right)، [`padding-bottom`](/en-US/docs/Web/CSS/padding-bottom)، و [`padding-left`](/en-US/docs/Web/CSS/padding-left)
- [`padding-block-start`](/en-US/docs/Web/CSS/padding-block-start)، [`padding-block-end`](/en-US/docs/Web/CSS/padding-block-end)، [`padding-inline-start`](/en-US/docs/Web/CSS/padding-inline-start)، و [`padding-inline-end`](/en-US/docs/Web/CSS/padding-inline-end)
- خلاصه‌نویسی‌های [`padding-block`](/en-US/docs/Web/CSS/padding-block) و [`padding-inline`](/en-US/docs/Web/CSS/padding-inline)
- راهنمای [آشنایی با مدل جعبه‌ای CSS](/en-US/docs/Web/CSS/Guides/Box_model/Introduction)
- ماژول [مدل جعبه‌ای CSS](/en-US/docs/Web/CSS/Guides/Box_model)