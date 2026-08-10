---
title: "<p> HTML paragraph element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/p"
translated_by: "n8n + AI"
---

The **`<p>`** [HTML](/en-US/docs/Web/HTML) element نمایانگر یک پاراگراف است. پاراگراف‌ها در رسانه‌های دیداری معمولاً به‌صورت بلوک‌های متنی جدا از هم با خطوط خالی و/یا تورفتگی خط اول نمایش داده می‌شوند، اما پاراگراف‌های HTML می‌توانند هر گروه‌بندی ساختاری از محتوای مرتبط باشند، مثل تصاویر یا فیلدهای فرم.

پاراگراف‌ها از انواع [block-level elements](/en-US/docs/Glossary/Block-level_content) هستند و نکتهٔ قابل توجه این است که اگر قبل از تگ بسته شدن `</p>` یک عنصر block-level دیگر پارس شود، مرورگر به‌صورت خودکار پاراگراف را خواهد بست. بخش «حذف تگ» (Tag omission) را ببینید.

```html interactive-example
<p>
  Geckos are a group of usually small, usually nocturnal lizards. They are found
  on every continent except Antarctica.
</p>

<p>
  Some species live in houses where they hunt insects attracted by artificial
  light.
</p>
```

```css interactive-example
p {
  margin: 10px 0;
  padding: 5px;
  border: 1px solid #999999;
}
```

## Attributes

این عنصر تنها شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

> [!NOTE]
> صفت `align` در تگ‌های `<p>` منسوخ شده و نباید استفاده شود.

## Accessibility

تقسیم محتوا به پاراگراف‌ها به قابل‌دسترس‌تر شدن صفحه کمک می‌کند. صفحه‌خوان‌ها و سایر فناوری‌های کمکی میانبرهایی ارائه می‌دهند تا کاربر بتواند به پاراگراف بعدی یا قبلی برود و متن را به‌صورت سریع مرور کند، مشابه اینکه فاصلهٔ سفید (white space) به کاربران دیداری امکان می‌دهد مرتب متن را پیمایش کنند.

استفاده از پاراگراف‌های خالی `<p>` برای ایجاد فاصله بین پاراگراف‌ها برای افرادی که با صفحه‌خوان‌ها ناوبری می‌کنند مشکل‌ساز است. صفحه‌خوان ممکن است وجود پاراگراف را اعلام کند اما محتوایی درون آن اعلام نکند — چون محتوایی وجود ندارد. این می‌تواند کاربر صفحه‌خوان را سردرگم یا ناراحت کند.

اگر فضای اضافی لازم است، از ویژگی‌های CSS مانند margin استفاده کنید تا همین اثر ایجاد شود:

```css
p {
  margin-bottom: 2em; /* increase white space after a paragraph */
}
```

## Examples

### HTML

```html
<p>
  This is the first paragraph of text. This is the first paragraph of text. This
  is the first paragraph of text. This is the first paragraph of text.
</p>
<p>
  This is the second paragraph. This is the second paragraph. This is the second
  paragraph. This is the second paragraph.
</p>
```

### Result

## Styling paragraphs

به‌طور پیش‌فرض، مرورگرها بین پاراگراف‌ها یک خط خالی قرار می‌دهند. روش‌های جایگزین جداسازی، مثل تورفتگی خط اول، را می‌توان با CSS اعمال کرد:

### HTML

```html
<p>
  Separating paragraphs with blank lines is easiest for readers to scan, but
  they can also be separated by indenting their first lines. This is often used
  to take up less space, such as to save paper in print.
</p>

<p>
  Writing that is intended to be edited, such as school papers and rough drafts,
  uses both blank lines and indentation for separation. In finished works,
  combining both is considered redundant and amateurish.
</p>

<p>
  In very old writing, paragraphs were separated with a special character: ¶,
  the <i>pilcrow</i>. Nowadays, this is considered claustrophobic and hard to
  read.
</p>

<p>
  How hard to read? See for yourself:
  <button data-toggle-text="Oh no! Switch back!">
    Use pilcrow for paragraphs
  </button>
</p>
```

### CSS

```css
p {
  margin: 0;
  text-indent: 3ch;
}

p.pilcrow {
  text-indent: 0;
  display: inline;
}
p.pilcrow + p.pilcrow::before {
  content: " ¶ ";
}
```

### JavaScript

```js
document.querySelector("button").addEventListener("click", (event) => {
  document.querySelectorAll("p").forEach((paragraph) => {
    paragraph.classList.toggle("pilcrow");
  });
});
```

```js
  [event.target.innerText, event.target.dataset.toggleText] = [
    event.target.dataset.toggleText,
    event.target.innerText,
  ];
});
```

### نتیجه

## خلاصه‌ی فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >، palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        تگ شروع اجباری است. تگ پایان می‌تواند حذف شود اگر عنصر <code>&lt;p&gt;</code> مستقیماً توسط
        <code>&lt;address&gt;</code>،
        <code>&lt;article&gt;</code>، <code>&lt;aside&gt;</code>، <code>&lt;blockquote&gt;</code>، <code>&lt;details&gt;</code>، <code>&lt;div&gt;</code>،
        <code>&lt;dl&gt;</code>، <code>&lt;fieldset&gt;</code>،
        <code>&lt;figcaption&gt;</code>، <code>&lt;figure&gt;</code>،
        <code>&lt;footer&gt;</code>، <code>&lt;form&gt;</code>،
        <code>&lt;h1&gt;</code>، <code>&lt;h2&gt;</code>،
        <code>&lt;h3&gt;</code>، <code>&lt;h4&gt;</code>،
        <code>&lt;h5&gt;</code>، <code>&lt;h6&gt;</code>،
        <code>&lt;header&gt;</code>، <code>&lt;hgroup&gt;</code>، <code>&lt;hr&gt;</code>،
        <code>&lt;main&gt;</code>، <code>&lt;menu&gt;</code>، <code>&lt;nav&gt;</code>،
        <code>&lt;ol&gt;</code>، <code>&lt;pre&gt;</code>، <code>&lt;search&gt;</code>،
        <code>&lt;section&gt;</code>، <code>&lt;table&gt;</code>،
        <code>&lt;ul&gt;</code> یا یک عنصر دیگر <code>&lt;p&gt;</code>
        باشد، یا اگر در والد هیچ محتوای بیشتری وجود نداشته باشد و عنصر والد یک
        <code>&lt;a&gt;</code>، <code>&lt;audio&gt;</code>،
        <code>&lt;del&gt;</code>، <code>&lt;ins&gt;</code>، <code>&lt;map&gt;</code>،
        <code>&lt;noscript&gt;</code> یا <code>&lt;video&gt;</code> نباشد،
        یا یک autonomous custom element.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        > را می‌پذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles"
          >paragraph</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هرکدام</td>
    </tr>
    <tr>
      <th scope="row">اینترفیس DOM</th>
      <td><code>HTMLParagraphElement</code></td>
    </tr>
  </tbody>
</table>

## Specifications

## Browser compatibility

## همچنین ببینید

- <code>&lt;hr&gt;</code>
- <code>&lt;br&gt;</code>