---
title: "text-align CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-align"
translated_by: "n8n + AI"
---

ویژگی `text-align` در CSS
تراز افقی محتوای `inline-level` را درون یک عنصر block یا سلول جدول تنظیم می‌کند. در حقیقت عملکردی مشابه `vertical-align` اما در جهت افقی دارد.

## نحو

```css
/* مقدارهای کلیدی */
text-align: start;
text-align: end;
text-align: left;
text-align: right;
text-align: center;
text-align: justify;
text-align: match-parent;

/* مقدارهای تراز بلوکی (نحو غیر استاندارد) */
text-align: -moz-center;
text-align: -webkit-center;

/* مقدارهای سراسری */
text-align: inherit;
text-align: initial;
text-align: revert;
text-align: revert-layer;
text-align: unset;
```

### مقادیر

این ویژگی با یکی از مقدارهای کلیدی زیر تعیین می‌شود:

- `start`
  - : معادل `left` اگر جهت متن چپ‌به‌راست باشد و `right` اگر جهت متن راست‌به‌چپ باشد.
- `end`
  - : معادل `right` اگر جهت متن چپ‌به‌راست باشد و `left` اگر جهت متن راست‌به‌چپ باشد.
- `left`
  - : محتوای inline در امتداد لبهٔ چپ خط تراز می‌شود.
- `right`
  - : محتوای inline در امتداد لبهٔ راست خط تراز می‌شود.
- `center`
  - : محتوای inline در مرکز خط قرار می‌گیرد.
- `justify`
  - : تراز دوطرفه. محتوا طوری توزیع می‌شود که لبه‌های چپ و راست متن با لبه‌های چپ و راست خط هم‌تراز شوند – به‌جز آخرین خط.
- `match-parent`
  - : مشابه `inherit`، با این تفاوت که مقدارهای `start` و `end` بر اساس ویژگی `direction` والد محاسبه شده و به مقدار مناسب `left` یا `right` تبدیل می‌شوند.

## دسترس‌پذیری

فاصله‌های ناهماهنگ میان واژه‌ها که در متن‌های `justify` ایجاد می‌شوند، ممکن است برای افراد دارای مشکلات شناختی مانند نارساخوانی دردسرساز شود.

- [مستندات MDN برای درک WCAG، توضیحات اصل ۱.۴](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [درک معیار موفقیت ۱.۴.۸ | درک WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-visual-presentation.html)

## مثال‌ها

### ترازبندی start

#### HTML

```html
<p class="example">
  Integer elementum massa at nulla placerat varius. Suspendisse in libero risus,
  in interdum massa. Vestibulum ac leo vitae metus faucibus gravida ac in neque.
  Nullam est eros, suscipit sed dictum quis, accumsan a ligula.
</p>
```

#### CSS

```css
.example {
  text-align: start;
  border: solid;
}
```

### متن وسط‌چین

#### HTML

```html
<p class="center">
  این یک متن نمونه برای نمایش تراز وسط است.
</p>
```

#### CSS

```css
.center {
  text-align: center;
  border: solid;
}
```

### مثال با center

```html
<p class="example">
  Integer elementum massa at nulla placerat varius. Suspendisse in libero risus,
  in interdum massa. Vestibulum ac leo vitae metus faucibus gravida ac in neque.
  Nullam est eros, suscipit sed dictum quis, accumsan a ligula.
</p>
```

#### CSS

```css
.example {
  text-align: center;
  border: solid;
}
```

### مثال با justify

```html
<p class="example">
  Integer elementum massa at nulla placerat varius. Suspendisse in libero risus,
  in interdum massa. Vestibulum ac leo vitae metus faucibus gravida ac in neque.
  Nullam est eros, suscipit sed dictum quis, accumsan a ligula.
</p>
```

#### CSS

```css
.example {
  text-align: justify;
  border: solid;
}
```

### ترازبندی جدول

این مثال استفاده از `text-align` را روی عناصر `<table>` نشان می‌دهد:

- عنصر `<caption>` به‌صورت راست‌چین تنظیم شده است.
- دو عنصر `<th>` اول، ترازبندی چپ را از `text-align: left` تعیین‌شده روی `<thead>` به ارث می‌برند، در حالی که عنصر سوم راست‌چین شده است.
- درون عنصر `<tbody>`، سطر اول راست‌چین، سطر دوم وسط‌چین و سطر سوم از ترازبندی پیش‌فرض (چپ) استفاده می‌کند.
- در هر سطر، برخی سلول‌ها (c12، c31) طوری تنظیم شده‌اند که ترازبندی سطر را لغو کنند.

#### HTML

```html
<table>
  <caption>
    Example table
  </caption>
  <thead>
    <tr>
      <th>Col 1</th>
      <th>Col 2</th>
      <th class="right">Col 3</th>
    </tr>
  </thead>
  <tbody>
    <tr class="right">
      <td>11</td>
      <td class="center">12</td>
      <td>13</td>
    </tr>
    <tr class="center">
      <td>21</td>
      <td>22</td>
      <td>23</td>
    </tr>
    <tr id="r3">
      <td class="right">31</td>
      <td>32</td>
      <td>33</td>
    </tr>
  </tbody>
</table>
```

#### CSS

```css
table {
  border-collapse: collapse;
  border: solid black 1px;
  width: 250px;
  height: 150px;
}

thead {
  text-align: left;
}

td,
th {
  border: solid 1px black;
}

.center {
  text-align: center;
}

.right,
caption {
  text-align: right;
}
```

## همچنین ببینید

- `margin: auto`
- `margin-left: auto`
- `vertical-align`