---
title: "<meta> HTML metadata element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta"
translated_by: "n8n + AI"
---

عنصر `<meta>` یک متاداده (metadata) را مشخص می‌کند که نمی‌تواند توسط عناصر مرتبط با متاداده مانند `<base>`، `<link>`، `<script>`، `<style>` یا `<title>` ارائه شود.

نوع متاداده‌ای که عنصر `<meta>` فراهم می‌کند می‌تواند یکی از موارد زیر باشد:

- اگر attribute `name` تنظیم شده باشد، `<meta>` یک _متاداده در سطح سند_ فراهم می‌کند که برای کل صفحه اعمال می‌شود.
- اگر attribute `http-equiv` تنظیم شده باشد، `<meta>` به عنوان یک _pragma directive_ عمل می‌کند تا دستورالعمل‌هایی را شبیه‌سازی کند که معمولاً توسط یک HTTP header داده می‌شوند.
- اگر attribute `charset` تنظیم شده باشد، `<meta>` یک _اعلام charset_ (encoding نویسه‌ها) است که encoding نویسه‌های سند را مشخص می‌کند.
- اگر attribute `itemprop` تنظیم شده باشد، `<meta>` یک _متاداده تعریف‌شده توسط کاربر_ ارائه می‌دهد.

## Attributes

این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) (ویژگی‌های سراسری) نیز می‌شود.

> [!NOTE]
> attribute `name` برای عنصر `<meta>` معنای خاصی دارد. attribute `itemprop` نباید روی یک عنصر `<meta>` که شامل `name`، `http-equiv` یا `charset` است تنظیم شود.

- `charset`
  - : این attribute encoding نویسه‌های سند را اعلام می‌کند. اگر این attribute وجود داشته باشد، مقدار آن باید به‌طور دقیق (با حساسیت به حروف کوچک و بزرگ در ASCII) برابر با `"utf-8"` باشد، زیرا UTF-8 تنها encoding معتبر برای اسناد HTML5 است. عناصر `<meta>` که encoding نویسه‌ها را اعلام می‌کنند باید کاملاً در ۱۰۲۴ بایت اول سند قرار گیرند.
- [`content`](/en-US/docs/Web/HTML/Reference/Attributes/content)
  - : این attribute مقدار مربوط به attribute `http-equiv` یا `name` را در خود نگه می‌دارد (بسته به اینکه کدام یک استفاده شده است).
- [`http-equiv`](/en-US/docs/Web/HTML/Reference/Elements/meta/http-equiv)
  - : یک pragma directive تعریف می‌کند که دستورالعمل‌هایی برای مرورگر جهت پردازش سند هستند. نام این attribute مخفف `http-equivalent` است، زیرا مقادیر مجاز، نام‌های HTTP headerهای معادل هستند.
- `media`
  - : attribute `media` مشخص می‌کند که رنگ تم (theme color) تعریف‌شده در attribute `content` برای کدام رسانه (media) اعمال شود. مقدار آن یک [media query](/en-US/docs/Web/CSS/Guides/Media_queries/Using) است که اگر attribute وجود نداشته باشد، مقدار پیش‌فرض `all` است. این attribute فقط زمانی معنا دارد که attribute `name` عنصر روی `theme-color` تنظیم شده باشد. در غیر این صورت تأثیری ندارد و نباید گنجانده شود.
- [`name`](/en-US/docs/Web/HTML/Reference/Elements/meta/name)
  - : از attribute‌های `name` و `content` می‌توان با هم استفاده کرد تا متاداده سند را به صورت جفت‌های نام-مقدار ارائه دهند؛ `name` نام متاداده و `content` مقدار آن را مشخص می‌کند.

## Examples

### تنظیم توضیحات متا

تگ `<meta>` زیر یک `description` به عنوان متاداده برای صفحه وب فراهم می‌کند:

```html
<meta
  name="description"
  content="The HTML reference describes all elements and attributes of HTML, including global attributes that apply to all elements." />
```

### تنظیم یک صفحه‌گردانی (page redirect)

مثال زیر از `http-equiv="refresh"` برای هدایت مرورگر به انجام یک redirect استفاده می‌کند.  
ویژگی `content="3;url=https://www.mozilla.org"` صفحه را بعد از ۳ ثانیه به `https://www.mozilla.org` هدایت می‌کند:

```html
<meta http-equiv="refresh" content="3;url=https://www.mozilla.org" />
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی‌های محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content">Metadata content (محتوای فراداده)</a>. اگر <a href="/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop"><code>itemprop</code></a> وجود داشته باشد:
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">flow content (محتوای جریانی)</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content (محتوای عبارتی)</a>.
      </td>
    </tr>
    <tr>
      <th>محتوای مجاز</th>
      <td>هیچ؛ این یک عنصر void (بدون محتوا) است.</td>
    </tr>
    <tr>
      <th>حذف تگ</th>
      <td>باید تگ شروع داشته باشد و نباید تگ پایان داشته باشد.</td>
    </tr>
    <tr>
      <th>والدین مجاز</th>
      <td>
        <ul>
          <li>
            <code>&#x3C;meta charset></code>،
            <code>&#x3C;meta http-equiv></code>: یک عنصر <code>&#x3C;head&gt;</code>. اگر <a href="/en-US/docs/Web/HTML/Reference/Elements/meta/http-equiv"><code>http-equiv</code></a> یک اعلان encoding نباشد، می‌تواند داخل یک عنصر <code>&#x3C;noscript&gt;</code> که خود داخل <code>&#x3C;head&gt;</code> است نیز قرار گیرد.
          </li>
          <li>
            <code>&#x3C;meta name></code>: هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content">metadata content</a> را می‌پذیرد.
          </li>
          <li>
            <code>&#x3C;meta itemprop></code>: هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content">metadata content</a> یا <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">flow content</a> را می‌پذیرد.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">هیچ نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th>رابط DOM</th>
      <td><code>HTMLMetaElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- [نام‌های استاندارد metadata](/en-US/docs/Web/HTML/Reference/Elements/meta/name)
- [یادگیری: `<meta>`](/en-US/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata#metadata_the_meta_element)