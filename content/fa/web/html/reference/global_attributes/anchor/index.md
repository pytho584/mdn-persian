---
title: "anchor HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/anchor"
translated_by: "n8n + AI"
---

ویژگی سراسری `anchor` برای مرتبط کردن یک عنصر موقعیت‌یافته با یک عنصر لنگر استفاده می‌شود. مقدار این ویژگی، `id` عنصری است که می‌خواهید عنصر موقعیت‌یافته را به آن بچسبانید. سپس می‌توانید با استفاده از [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using) عنصر را موقعیت‌دهی کنید.

> **توجه:** همچنین می‌توانید از طریق CSS و با استفاده از ویژگی‌های `{{cssxref("anchor-name")}}` و `{{cssxref("position-anchor")}}` یک عنصر موقعیت‌یافته را به یک عنصر لنگر متصل کنید. اگر هر دو روش (HTML و CSS) روی یک عنصر استفاده شوند، روش CSS اولویت دارد.

## مثال‌ها

### استفادهٔ پایه از ویژگی `anchor`

در مثال زیر، از HTML برای مرتبط کردن یک عنصر موقعیت‌یافته با یک لنگر استفاده شده است. سپس با CSS، عنصر موقعیت‌یافته را به سمت راست لنگر متصل می‌کنیم.

#### HTML

یک عنصر `<div>` با `id` برابر `example-anchor` ایجاد می‌کنیم. این عنصر لنگر ماست. سپس یک `<div>` دیگر با ویژگی `anchor` تنظیم‌شده روی `example-anchor` قرار می‌دهیم. این کار، `<div>` اول را به عنوان لنگر `<div>` دوم تعیین می‌کند و آن‌ها را به هم مرتبط می‌سازد.

همچنین چند متن پرکننده در اطراف دو `<div>` اضافه کرده‌ایم تا `<body>` بلندتر شود و قابلیت اسکرول داشته باشد.

```html
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor" id="example-anchor">⚓︎</div>

<div class="infobox" anchor="example-anchor">
  <p>This is an information box.</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

#### CSS

```css hidden
body {
  width: 50%;
  margin: 0 auto;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

با CSS، عنصر `infobox` را به یک _عنصر موقعیت‌یافته با لنگر_ تبدیل کرده و نسبت به لنگرش آن را موقعیت‌دهی می‌کنیم. تنظیمات زیر را اعمال می‌کنیم:

- ویژگی `position` را `fixed` قرار می‌دهیم تا به یک عنصر موقعیت‌یافته تبدیل شود و بتوان نسبت به موقعیت لنگر آن را جابجا کرد.
- ویژگی `left` را به تابع `anchor()` با مقدار `right` تنظیم می‌کنیم. این کار عنصر موقعیت‌یافته را به لنگر خود متصل کرده و لبهٔ چپ آن را درست در لبهٔ راست لنگر قرار می‌دهد.
- ویژگی `align-self` را به `anchor-center` تنظیم می‌کنیم. این کار باعث می‌شود جعبهٔ اطلاعات در جهت inlin به مرکز لنگر تراز شود.
- یک `margin-left` به اندازه `10px` اضافه می‌کنیم تا بین عنصر موقعیت‌یافته و لنگر فاصله ایجاد شود.

```css
.infobox {
  position: fixed;
  left: anchor(right);
  align-self: anchor-center;
  margin-left: 10px;
}
```

#### نتیجه

نمونه را اسکرول کنید تا ببینید جعبه اطلاعات چگونه به لنگر (anchor) متصل شده است. وقتی ویژگی `anchor` پشتیبانی شود، جعبه اطلاعات در سمت راست لنگر ثابت می‌ماند. در غیر این صورت، جعبه اطلاعات نسبت به viewport ثابت می‌شود.

## مشخصات

این ویژگی در حال حاضر بخشی از مشخصات HTML نیست. بحث درباره افزودن ویژگی `anchor` را در [https://github.com/whatwg/html/pull/9144](https://github.com/whatwg/html/pull/9144) بخوانید.

## همچنین ببینید

- [ماژول CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning)