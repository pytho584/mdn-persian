---
title: "<figure> HTML figure with optional caption element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/figure"
translated_by: "n8n + AI"
---

# عنصر `<figure>`

عنصر **`<figure>`** [HTML](/en-US/docs/Web/HTML) محتوای مستقلی را نمایش می‌دهد که احتمالاً شامل یک توضیح (caption) اختیاری است؛ توضیح با استفاده از عنصر `<figcaption>` تعریف می‌شود. در ارجاع‌ها، `<figure>`، توضیح آن و محتویاتش به عنوان یک واحد در نظر گرفته می‌شوند.

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

- معمولاً `<figure>` برای تصویر، نگاره، نمودار، تکه‌کد و غیره استفاده می‌شود که در جریان اصلی سند به آن ارجاع داده می‌شود، اما می‌توان آن را بدون تأثیر بر جریان اصلی، به بخش دیگری از سند یا پیوست منتقل کرد.
- می‌توان با قرار دادن یک `<figcaption>` در داخل `<figure>` (به عنوان فرزند اول یا آخر)، یک توضیح به آن متصل کرد. اولین `<figcaption>` یافت‌شده در figure به عنوان توضیح آن نمایش داده می‌شود.
- `<figcaption>` نام قابل دسترس (accessible name) را برای `<figure>` والد فراهم می‌کند.

## مثال‌ها

### تصاویر

```html
<!-- Just an image -->
<figure>
  <img src="favicon-192x192.png" alt="The beautiful MDN logo." />
</figure>

<!-- Image with a caption -->
<figure>
  <img src="favicon-192x192.png" alt="The beautiful MDN logo." />
  <figcaption>MDN Logo</figcaption>
</figure>
```

### قطعه‌های کد

```html
<figure>
  <figcaption>Get browser details using <code>navigator</code>.</figcaption>
  <pre>
function NavigatorExample() {
  let txt = `Browser CodeName: ${navigator.appCodeName};\n`;
  txt += `Browser Name: ${navigator.appName};\n`;
  txt += `Browser Version: ${navigator.appVersion};\n`;
  txt += `Cookies Enabled: ${navigator.cookieEnabled};\n`;
  txt += `Platform: ${navigator.platform};\n`;
  txt += `User-agent header: ${navigator.userAgent};`;
  console.log("NavigatorExample", txt);
}
  </pre>
</figure>
```

### نقل‌قول‌ها

```html
<figure>
  <figcaption><b>Edsger Dijkstra:</b></figcaption>
  <blockquote>
    If debugging is the process of removing software bugs, then programming must
    be the process of putting them in.
  </blockquote>
</figure>
```

### شعرها

```html
<figure>
  <p>
    Bid me discourse, I will enchant thine ear,<br />
    Or like a fairy trip upon the green,<br />
    Or, like a nymph, with long dishevelled hair,<br />
    Dance on the sands, and yet no footing seen:<br />
    Love is a spirit all compact of fire,<br />
    Not gross to sink, but light, and will aspire.<br />
  </p>
  <figcaption><cite>Venus and Adonis</cite>, by William Shakespeare</figcaption>
</figure>
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی محتوا (Content categories)</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتویات جریانی (Flow content)</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content"
          >محتویات قابل لمس (palpable content)</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>
        یک عنصر <code>&lt;figcaption&gt;</code> و سپس
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتویات جریانی (Flow content)</a
        >؛ یا محتویات جریانی و سپس یک عنصر <code>&lt;figcaption&gt;</code>؛ یا فقط محتویات جریانی.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتویات جریانی (Flow content)</a
        > را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/figure_role"
          >figure</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>
        بدون فرزند
        <code>&lt;figcaption&gt;</code>:
        <a href="https://w3c.github.io/html-aria/#dfn-any-role">هر نقشی (any)</a>،
        در غیر این صورت هیچ نقش مجازی وجود ندارد.
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td><code>HTMLElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات (Specifications)

## سازگاری مرورگرها (Browser compatibility)

## همچنین ببینید (See also)

- عنصر `<figcaption>`