---
title: "margin CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/margin"
translated_by: "n8n + AI"
---

**`margin`** یک ویژگی خلاصه‌شده (shorthand) در CSS است که [ناحیه حاشیه](/en-US/docs/Web/CSS/Guides/Box_model/Introduction#margin_area) را در چهار طرف یک عنصر تنظیم می‌کند.

## ویژگی‌های تشکیل‌دهنده

این ویژگی خلاصه‌ای از چهار ویژگی زیر است:

- {{cssxref("margin-top")}}
- {{cssxref("margin-right")}}
- {{cssxref("margin-bottom")}}
- {{cssxref("margin-left")}}

## نحوه نگارش

```css
/* اعمال به هر چهار طرف */
margin: 1em;
margin: -3px;

/* بالا و پایین | چپ و راست */
margin: 5% auto;

/* بالا | چپ و راست | پایین */
margin: 1em auto 2em;

/* بالا | راست | پایین | چپ */
margin: 2px 1em 0 auto;

/* مقادیر anchor-size() */
margin: 5% anchor-size(width);
margin: calc(anchor-size(width) / 4) 1em 0
  anchor-size(--my-anchor self-inline, 50px);

/* مقدار کلیدی */
margin: auto;

/* مقادیر سراسری */
margin: inherit;
margin: initial;
margin: revert;
margin: revert-layer;
margin: unset;
```

ویژگی `margin` را می‌توان با یک، دو، سه یا چهار مقدار مشخص کرد. هر مقدار می‌تواند یک {{cssxref("&lt;length&gt;")}}، یک {{cssxref("&lt;percentage&gt;")}} یا کلمه کلیدی `auto` باشد. مقادیر منفی باعث می‌شوند عنصر نسبت به حالت پیش‌فرض به همسایه‌هایش نزدیک‌تر شود.

- اگر **یک** مقدار داده شود، همان اندازه حاشیه به **هر چهار طرف** اعمال می‌شود.
- اگر **دو** مقدار داده شود، مقدار اول برای **بالا و پایین** و مقدار دوم برای **چپ و راست** به‌کار می‌رود.
- اگر **سه** مقدار داده شود، مقدار اول برای **بالا**، دومی برای **چپ و راست** و سومی برای **پایین** استفاده می‌شود.
- اگر **چهار** مقدار داده شود، مقادیر به ترتیب برای **بالا**، **راست**، **پایین** و **چپ** (در جهت عقربه‌های ساعت) اعمال می‌شوند.

### مقادیر

- {{cssxref("length")}}
  - : اندازه حاشیه به‌صورت یک مقدار ثابت.
    - برای _عناصر جای‌گذاری‌شده با anchor_، تابع {{cssxref("anchor-size()")}} مقداری از نوع {{cssxref("&lt;length&gt;")}} را نسبت به عرض یا ارتفاع _عنصر anchor_ مرتبط برمی‌گرداند (ببینید [تنظیم حاشیه عنصر بر اساس اندازه anchor](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using#setting_element_margin_based_on_anchor_size)).
- {{cssxref("percentage")}}
  - : اندازه حاشیه به‌صورت درصدی از اندازه درون‌خطی (_width_ در زبان‌های افقی، که توسط {{cssxref("writing-mode")}} تعیین می‌شود) [بلوک دربرگیرنده](/en-US/docs/Web/CSS/Guides/Display/Containing_block).
- `auto`
  - : مرورگر یک حاشیه مناسب را انتخاب می‌کند. برای نمونه، در برخی موارد از این مقدار برای وسط‌چین کردن یک عنصر استفاده می‌شود.

## توضیحات

با این ویژگی می‌توان حاشیه هر چهار طرف یک عنصر را تنظیم کرد. حاشیه‌ها فضای اضافی را در _بیرون_ عنصر ایجاد می‌کنند، برخلاف {{cssxref("padding")}} که فضای اضافی را در _داخل_ عنصر به‌وجود می‌آورد.

حاشیه‌های بالا و پایین روی عناصر inline از نوع non-replaced (مثل {{HTMLElement("span")}} یا {{HTMLElement("code")}}) تأثیری ندارند.

### مرکز کردن افقی

می‌توانید با تنظیم `margin: 0 auto;` یک عنصر را به‌صورت افقی درون والدش مرکز کنید.

روش رایج‌تر برای مرکز کردن افقی، تنظیم `display: flex;` و [`justify-content: center;`](/en-US/docs/Web/CSS/Reference/Properties/justify-content) روی یک container است که [فرزندان flex آن را مرکز می‌کند](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items).

### ادغام margin

گاهی حاشیه‌های بالا و پایین عناصر در یک حاشیهٔ واحد ادغام می‌شوند که برابر با بزرگ‌ترین مقدار از آن دو است. برای اطلاعات بیشتر [تسلط بر ادغام margin](/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing) را ببینید.

## مثال‌ها

### مثال پایه

#### HTML

```html
<div class="center">This element is centered.</div>

<div class="outside">This element is positioned outside of its container.</div>
```

#### CSS

```css
.center {
  margin: auto;
  background: lime;
  width: 66%;
}

.outside {
  margin: 3rem 0 0 -3rem;
  background: cyan;
  width: 66%;
}
```

### مثال‌های بیشتر

```css
margin: 5%; /* تمام طرفین: حاشیه ۵٪ */

margin: 10px; /* تمام طرفین: حاشیه ۱۰px */

margin: 1.6em 20px; /* بالا و پایین: 1.6em حاشیه */
/* چپ و راست: ۲۰px حاشیه */

margin: 10px 3% -1em; /* بالا:       ۱۰px حاشیه */
/* چپ و راست: ۳٪ حاشیه   */
/* پایین:      -1em حاشیه */

margin: 10px 3px 30px 5px; /* بالا:    ۱۰px حاشیه */
/* راست:   ۳px حاشیه  */
/* پایین: ۳۰px حاشیه */
/* چپ:    ۵px حاشیه  */

margin: 2em auto; /* بالا و پایین: ۲em حاشیه   */
/* جعبه به صورت افقی مرکز می‌شود */

margin: auto; /* بالا و پایین: ۰ حاشیه     */
/* جعبه به صورت افقی مرکز می‌شود */
```

## همچنین ببینید

- {{cssxref("margin-top")}}, {{cssxref("margin-right")}}, {{cssxref("margin-bottom")}} و {{cssxref("margin-left")}}
- {{cssxref("margin-block-start")}}, {{cssxref("margin-block-end")}}, {{cssxref("margin-inline-start")}} و {{cssxref("margin-inline-end")}}
- خلاصه‌نویسی‌های {{cssxref("margin-block")}} و {{cssxref("margin-inline")}}
- [تسلط بر ادغام margin](/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing)
- راهنمای [مقدمه‌ای بر مدل جعبه‌ای CSS](/en-US/docs/Web/CSS/Guides/Box_model/Introduction)
- ماژول [مدل جعبه‌ای CSS](/en-US/docs/Web/CSS/Guides/Box_model)