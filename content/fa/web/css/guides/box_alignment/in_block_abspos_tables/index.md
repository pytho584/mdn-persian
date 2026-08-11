---
title: "Box alignment for block, absolutely positioned, and table layouts"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_alignment/In_block_abspos_tables"
translated_by: "n8n + AI"
---

ماژول **CSS box alignment** نحوه‌ی تراز شدن در روش‌های مختلف چیدمان را مشخص می‌کند. در این راهنما، بررسی می‌کنیم که box alignment در چیدمان بلوکی (block layout) چطور کار می‌کند – شامل عناصر شناور (floated)، موقعیت‌یاب (positioned) و جدول. از آنجا که این راهنما به جزئیات مختص block layout و box alignment می‌پردازد، توصیه می‌شود آن را همراه با راهنمای [box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview) بخوانید که ویژگی‌های مشترک بین روش‌های مختلف چیدمان را توضیح می‌دهد.

## align-content و justify-content

خاصیت {{cssxref("justify-content")}} روی ظروف بلوکی (block containers) و سلول‌های جدول (table cells) اعمال نمی‌شود.

خاصیت {{cssxref("align-content")}} روی محور بلوکی (block axis) کار می‌کند تا محتویات جعبه را درون ظرفش تراز کند. اگر از روش‌های توزیع محتوا مثل `space-between`، `space-around` یا `space-evenly` استفاده شود، از fallback alignment (تراز جایگزین) استفاده می‌شود، چون محتوا به‌عنوان یک [موضوع تراز (alignment subject)](/en-US/docs/Glossary/Alignment_Subject) واحد در نظر گرفته می‌شود.

## justify-self

خاصیت {{cssxref("justify-self")}} برای تراز کردن یک آیتم درون ظرف‌اش (containing block) روی محور درون‌خطی (inline axis) استفاده می‌شود.

این خاصیت روی عناصر شناور (floated) و سلول‌های جدول اعمال نمی‌شود.

## align-self

خاصیت {{cssxref("align-self")}} روی جعبه‌های سطح بلوکی (block-level boxes) – از جمله floats – اعمال نمی‌شود، چون در محور بلوکی بیش از یک آیتم وجود دارد. همچنین روی سلول‌های جدول هم اعمال نمی‌شود.

### عناصر موقعیت‌یاب مطلق (Absolutely positioned elements)

ظرف تراز (alignment container) همان بلوک موقعیت‌یاب (positioned block) است که مقادیر offset بالا، چپ، پایین و راست را در نظر می‌گیرد. کلمه‌ی کلیدی `normal` به `stretch` تبدیل می‌شود، مگر اینکه آیتم موقعیت‌یاب یک عنصر replaced باشد که در آن صورت به `start` تبدیل می‌شود.

## تراز کردن در این روش‌های چیدمان امروز

از آنجایی که هنوز مرورگرها از box alignment در block layout پشتیبانی نمی‌کنند، گزینه‌های شما برای تراز کردن عبارتند از: استفاده از روش‌های موجود تراز، یا تبدیل یک آیتم داخل ظرف به یک آیتم flex (flex item) تا بتوان از ویژگی‌های alignment مربوط به flexbox استفاده کرد.

پیش از flexbox، تراز افقی بلوک‌ها معمولاً با تنظیم حاشیه‌ی خودکار (auto margin) روی بلوک انجام می‌شد. یک {{cssxref("margin")}} با مقدار `auto` تمام فضای موجود در آن بعد را جذب می‌کند؛ بنابراین با تنظیم `margin-left` و `margin-right` روی `auto`، می‌توان یک بلوک را در مرکز قرار داد:

```css
.container {
  width: 20em;
  margin-left: auto;
  margin-right: auto;
}
```

در چیدمان جدول، خاصیت {{cssxref("vertical-align")}} برای تراز محتویات یک سلول درون آن سلول در دسترس است.

برای بسیاری از موارد استفاده، تبدیل ظرف بلوکی به یک ظرف flex (flex container) قابلیت تراز مورد نظر شما را فراهم می‌کند. در مثال زیر، یک ظرف با یک آیتم درون‌اش به یک flex container تبدیل شده تا بتوان از ویژگی‌های alignment استفاده کرد.

```html live-sample___intro
<div class="box">
  <div></div>
</div>
```

```css live-sample___intro
.box {
  height: 300px;
  border: 2px dotted rgb(96 139 168);
}

.box > * {
  border: 2px solid rgb(96 139 168);
  border-radius: 5px;
  background-color: rgb(96 139 168 / 0.2);
}
.box {
  display: flex;
  align-items: center;
  justify-content: center;
}

.box div {
  width: 100px;
  height: 100px;
}
```

{{EmbedLiveSample("intro", "", "320px")}}

## همچنین ببینید

- ماژول [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment)
- [مرور کلی box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview)
- [Box alignment در flexbox](/en-US/docs/Web/CSS/Guides/Box_alignment/In_flexbox)
- [Box alignment در CSS grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [Box alignment در چیدمان چندستونه](/en-US/docs/Web/CSS/Guides/Box_alignment/In_multi-column_layout)