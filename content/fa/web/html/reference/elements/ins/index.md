---
title: "<ins> HTML inserted text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/ins"
translated_by: "n8n + AI"
---

## `<ins>` عنصر متن درج‌شده در HTML

عنصر `<ins>` در HTML، محدوده‌ای از متن را نشان می‌دهد که به سند اضافه شده است. برای نمایش متنی که از سند حذف شده، می‌توانید از عنصر `<del>` استفاده کنید.

```html
<p>&ldquo;You're late!&rdquo;</p>
<del>
  <p>&ldquo;I apologize for the delay.&rdquo;</p>
</del>
<ins cite="../how-to-be-a-wizard.html" datetime="2018-05">
  <p>&ldquo;A wizard is never late &hellip;&rdquo;</p>
</ins>
```

```css
del,
ins {
  display: block;
  text-decoration: none;
  position: relative;
}

del {
  background-color: #ffbbbb;
}

ins {
  background-color: #d4fcbc;
}

del::before,
ins::before {
  position: absolute;
  left: 0.5rem;
  font-family: monospace;
}

del::before {
  content: "−";
}

ins::before {
  content: "+";
}

p {
  margin: 0 1.8rem;
  font-family: "Georgia", serif;
  font-size: 1rem;
}
```

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `cite`
  - : این ویژگی یک URI از منبعی را تعریف می‌کند که تغییر را توضیح می‌دهد؛ مانند پیوند به صورتجلسه یا یک تیکت در سیستم پشتیبانی.
- `datetime`
  - : این ویژگی زمان و تاریخ تغییر را نشان می‌دهد و باید یک تاریخ معتبر، همراه با رشته زمان اختیاری باشد. اگر مقدار قابل تجزیه به‌عنوان تاریخ با رشته زمان اختیاری نباشد، عنصر برچسب زمانی مرتبطی نخواهد داشت. برای قالب رشته بدون زمان، [قالب رشته تاریخ معتبر](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#date_strings) را ببینید. قالب رشته‌ای که هم تاریخ و هم زمان را شامل می‌شود، در [قالب رشته تاریخ و زمان محلی معتبر](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#local_date_and_time_strings) پوشش داده شده است.

## دسترس‌پذیری

وجود عنصر `<ins>` به‌صورت پیش‌فرض توسط بسیاری از فناوری‌های صفحه‌خوان اعلام نمی‌شود. می‌توانید با استفاده از ویژگی CSS {{cssxref("content")}} و شبه‌عنصرهای {{cssxref("::before")}} و {{cssxref("::after")}} آن را قابل اعلام کنید.

```css
ins::before,
ins::after {
  clip-path: inset(100%);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}

ins::before {
  content: " [insertion start] ";
}

ins::after {
  content: " [insertion end] ";
}
```

برخی از کاربران صفحه‌خوان به‌طور عمدی اعلام محتوایی که باعث طولانی‌شدن کلام می‌شود را غیرفعال می‌کنند. به همین دلیل، مهم است که از این تکنیک سوءاستفاده نکنید و فقط در شرایطی آن را به کار ببرید که ندانستن درج‌شدن محتوا، درک مطلب را به‌طور منفی تحت تأثیر قرار دهد.

- [یادداشت کوتاه درباره قابل‌دسترس‌تر کردن نشانه‌گذاری | Vispero](https://vispero.com/resources/short-note-on-making-your-mark-more-accessible/)
- [تنظیم استایل متن در سطح خط | Adrian Roselli](https://adrianroselli.com/2017/12/tweaking-text-level-styles.html)

## مثال‌ها

```html
<ins>This text has been inserted</ins>
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">flow content</a>
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model">Transparent</a>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هم تگ شروع و هم تگ پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>
        را قبول می‌کند.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">insertion</a></code>
      </td>
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

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- عنصر `<del>` برای علامت‌گذاری حذف در سند