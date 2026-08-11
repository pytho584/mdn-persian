---
title: "<del> HTML deleted text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/del"
translated_by: "n8n + AI"
---

# `<del>`: element متن حذف‌شده در HTML

element **`<del>`** در [HTML](/en-US/docs/Web/HTML) محدوده‌ای از متن را نشان می‌دهد که از سند حذف شده است. این می‌تواند برای نمایش «ردگیری تغییرات» یا اطلاعات diff در کد منبع استفاده شود. element [`<ins>`](/en-US/docs/Web/HTML/Reference/Elements/ins) برای هدف برعکس استفاده می‌شود: نشان دادن متنی که به سند اضافه شده است.

## مثال تعاملی

```html interactive-example
<blockquote>
  There is <del>nothing</del> <ins>no code</ins> either good or bad, but
  <del>thinking</del> <ins>running it</ins> makes it so.
</blockquote>
```

```css interactive-example
del {
  text-decoration: line-through;
  background-color: #ffbbbb;
  color: #555555;
}

ins {
  text-decoration: none;
  background-color: #d4fcbc;
}

blockquote {
  padding-left: 15px;
  border-left: 3px solid #d7d7db;
  font-size: 1rem;
}
```

این element معمولاً (اما نه لزوماً) به صورت متن خط‌خورده (strikethrough) رندر می‌شود.

## Attribute ها

attribute های این element شامل [global attribute ها](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

- `cite`
  - : یک URI برای منبعی که تغییر را توضیح می‌دهد (مثلاً صورتجلسه).
- `datetime`
  - : این attribute زمان و تاریخ تغییر را نشان می‌دهد و باید یک رشته تاریخ معتبر (date string) همراه با زمان اختیاری باشد. اگر مقدار نتواند به عنوان تاریخ با زمان اختیاری parse شود، این element تایم‌استامپ مرتبط نخواهد داشت. برای قالب رشته بدون زمان، به [رشته‌های تاریخ](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#date_strings) مراجعه کنید. قالب رشته‌ای که هم تاریخ و هم زمان دارد در [رشته‌های تاریخ و زمان محلی](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#local_date_and_time_strings) پوشش داده شده است.

## دسترس‌پذیری

حضور element `del` به‌طور پیش‌فرض توسط بیشتر صفحه‌خوان‌ها اعلام نمی‌شود. می‌توان با استفاده از property `content` در CSS و شبه‌المان‌های `::before` و `::after` آن را قابل اعلام کرد.

```css
del::before,
del::after {
  clip-path: inset(100%);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}

del::before {
  content: " [deletion start] ";
}

del::after {
  content: " [deletion end] ";
}
```

برخی از کاربرانی که از صفحه‌خوان استفاده می‌کنند عمداً اعلام محتوایی که اطلاعات اضافی ایجاد می‌کند را غیرفعال می‌کنند. به همین دلیل، مهم است که از این تکنیک سوءاستفاده نشود و فقط در شرایطی به کار رود که نداشتن اطلاع از حذف‌شدن محتوا، درک مطلب را به‌طور نامطلوبی تحت تأثیر قرار دهد.

- [Short note on making your mark (more accessible) | Vispero](https://vispero.com/resources/short-note-on-making-your-mark-more-accessible/)
- [Tweaking Text Level Styles | Adrian Roselli](https://adrianroselli.com/2017/12/tweaking-text-level-styles.html)

## مثال‌ها

```html
<p><del>This text has been deleted</del>, here is the rest of the paragraph.</p>
<del><p>This paragraph has been deleted.</p></del>
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row"><a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌های محتوا</a></th>
      <td><a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای متنی</a>، <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a>.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td><a href="/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model">شفاف</a>.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هم تگ آغازین و هم تگ پایانی الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای متنی</a> را می‌پذیرد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td><code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">deletion</a></code></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLModElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- عنصر `<ins>` برای درج در متن
- عنصر `<s>` برای نمایش خط‌خوردگی؛ جدا از نمایش حذف متن