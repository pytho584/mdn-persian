---
title: "<br> HTML line break element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/br"
translated_by: "n8n + AI"
---

عنصر **`<br>`** در [HTML](/en-US/docs/Web/HTML) یک خط‌شکن (line break) در متن ایجاد می‌کند. برای نوشتن شعر یا آدرس مفید است، جایی که تقسیم خطوط اهمیت دارد.

```html interactive-example
<p>
  O'er all the hilltops<br />
  Is quiet now,<br />
  In all the treetops<br />
  Hearest thou<br />
  Hardly a breath;<br />
  The birds are asleep in the trees:<br />
  Wait, soon like these<br />
  Thou too shalt rest.
</p>
```

```css interactive-example
p {
  font-size: 1rem;
  font-family: sans-serif;
  margin: 20px;
}
```

همان‌طور که در مثال بالا می‌بینید، یک عنصر `<br>` در هر نقطه‌ای که بخواهیم متن شکسته شود قرار می‌گیرد. متن بعد از `<br>` از ابتدای خط بعدی بلوک متن شروع می‌شود.

> [!NOTE]
> از `<br>` برای ایجاد فاصله بین پاراگراف‌ها استفاده نکنید؛ آن‌ها را در عناصر `<p>` قرار دهید و از ویژگی CSS `margin` برای کنترل اندازه‌شان استفاده کنید.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

### ویژگی‌های منسوخ

- `clear`
  - : مشخص می‌کند که خط بعدی پس از شکستن از کجا شروع شود.

## استایل‌دهی با CSS

عنصر `<br>` یک هدف مشخص و واحد دارد — ایجاد خط‌شکن در یک بلوک متن. به همین دلیل، هیچ ابعاد یا خروجی بصری مستقلی ندارد و کار زیادی برای استایل‌دادن به آن نمی‌توانید انجام دهید.

می‌توانید روی خود عناصر `<br>` یک `margin` تنظیم کنید تا فاصله بین خطوط متن در بلوک افزایش یابد، اما این کار روش درستی نیست — باید از ویژگی `line-height` استفاده کنید که برای این منظور طراحی شده است.

## دسترس‌پذیری

ایجاد پاراگراف‌های جداگانه متن با `<br>` نه‌تنها روش بدی است، بلکه برای افرادی که با فناوری صفحه‌خوان (screen reader) مرور می‌کنند مشکل ایجاد می‌کند. صفحه‌خوان‌ها ممکن است وجود عنصر را اعلام کنند، اما محتوای داخل `<br>`ها را نمی‌خوانند. این می‌تواند تجربه‌ای گیج‌کننده و خسته‌کننده برای کاربر صفحه‌خوان باشد.

از عناصر `<p>` استفاده کنید و از ویژگی‌های CSS مانند `margin` برای کنترل فاصله آن‌ها بهره ببرید.

## مثال‌ها

### مثال پایه

در مثال زیر از عناصر `<br>` برای ایجاد خط‌شکن بین خطوط مختلف یک نشانی پستی استفاده کرده‌ایم:

```html
Mozilla<br />
331 E. Evelyn Avenue<br />
Mountain View, CA<br />
94041<br />
USA<br />
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌های محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>هیچ؛ یک عنصر void است.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        باید تگ شروع داشته باشد و تگ پایانی نداشته باشد. در اسناد XHTML، این عنصر را به شکل <code>&#x3C;br /></code> بنویسید.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی</a> را می‌پذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLBRElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- عنصر `<address>`
- عنصر `<p>`
- عنصر `<wbr>`