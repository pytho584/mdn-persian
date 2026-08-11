---
title: "<base> HTML document base URL element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/base"
translated_by: "n8n + AI"
---

عنصر `<base>` در HTML، آدرس پایه (base URL) را برای تمام URLهای نسبی داخل سند مشخص می‌کند. در یک سند فقط یک عنصر `<base>` می‌تواند وجود داشته باشد.

آدرس پایه‌ای که سند از آن استفاده می‌کند را می‌توان از طریق اسکریپت‌ها با `Node.baseURI` به دست آورد. اگر سند هیچ عنصر `<base>` نداشته باشد، `baseURI` برابر با `location.href` می‌شود.

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز می‌شود.

> [!WARNING]
> عنصر `<base>` باید حداقل یکی از ویژگی‌های `href` یا `target` را داشته باشد. اگر حداقل یکی از این ویژگی‌ها مشخص شده باشد، عنصر `<base>` **باید** قبل از سایر عناصری قرار بگیرد که مقادیر ویژگی آن‌ها URL هستند، مثل ویژگی `href` در یک {{HTMLElement("link")}}.

- `href`
  - : آدرس پایه‌ای که برای URLهای نسبی در سراسر سند استفاده می‌شود. آدرس‌های مطلق و نسبی مجاز هستند. اما آدرس‌های [`data:`](/en-US/docs/Web/URI/Reference/Schemes/data) و [`javascript:`](/en-US/docs/Web/URI/Reference/Schemes/javascript) مجاز نیستند.
- `target`
  - : یک **کلمه کلیدی** یا **نام اختصاصی** که context مرورگری پیش‌فرض را برای نمایش نتایج ناوبری از عناصر {{HTMLElement("a")}}، {{HTMLElement("area")}} یا {{HTMLElement("form")}} که ویژگی `target` ندارند، مشخص می‌کند. کلمات کلیدی زیر معانی خاصی دارند:
    - `_self` (پیش‌فرض): نتیجه را در همان context مرورگری فعلی نشان می‌دهد.
    - `_blank`: نتیجه را در یک context مرورگری جدید و بدون نام نمایش می‌دهد.
    - `_parent`: اگر صفحه فعلی داخل یک فریم باشد، نتیجه را در context مرورگری والد نمایش می‌دهد. اگر والد وجود نداشته باشد، مانند `_self` عمل می‌کند.
    - `_top`: نتیجه را در بالاترین context مرورگری (contextی که جد context فعلی است و والد ندارد) نمایش می‌دهد. اگر والدی نباشد، مانند `_self` عمل می‌کند.

## نکات استفاده

### چندین `<base>`

اگر چندین عنصر `<base>` استفاده شود، فقط اولین `href` و اولین `target` اعمال می‌شوند و بقیه نادیده گرفته می‌شوند.

### انکرهای درون صفحه‌ای

لینک‌هایی که به یک قطعه (fragment) درون سند اشاره می‌کنند (مثل `<a href="#some-id">`) با توجه به `<base>` حل می‌شوند و یک درخواست HTTP به آدرس پایه به همراه fragment ارسال می‌شود.

برای مثال، اگر `<base href="https://example.com/">` و این لینک: `<a href="#anchor">To anchor</a>` داشته باشیم، لینک به `https://example.com/#anchor` اشاره می‌کند.

### target نمی‌تواند شامل newline، tab یا `<` باشد

اگر ویژگی [`target`](#target) شامل کاراکتر newline، tab یا `<` باشد، مقدار آن به `_blank` بازنشانی می‌شود. این کار برای جلوگیری از حملات تزریق dangling markup است؛ حمله‌ای بدون اسکریپت که در آن یک ویژگی `target` ناقص به صفحه تزریق می‌شود تا هر متنی که بعد از آن می‌آید، تا زمانی که مرورگر به کاراکتری برسد که ویژگی را می‌بندد، ضبط شود.

### Open Graph

تگ‌های [Open Graph](https://ogp.me/) `<base>` را در نظر نمی‌گیرند و همیشه باید URLهای کامل مطلق داشته باشند. به عنوان مثال:

```html
<meta property="og:image" content="https://example.com/thumbnail.jpg" />
```

## مثال‌ها

```html
<base href="https://www.example.com/" />
<base target="_blank" />
<base target="_top" href="https://example.com/" />
```

## خلاصه فنی

> **توجه:** این بخش خلاصه فنی است. برای جزئیات بیشتر به مطالب بالا مراجعه کنید.

<table>
  <thead>
    <tr>
      <th>ویژگی</th>
      <th>مقدار</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا (Content categories)</a></td>
      <td>محتوای فراداده (Metadata content)</td>
    </tr>
    <tr>
      <td>محتوای مجاز</td>
      <td>هیچ؛ این یک عنصر خالی (void element) است</td>
    </tr>
    <tr>
      <td>حذف تگ</td>
      <td>باید تگ شروع داشته باشد و نباید تگ پایان داشته باشد</td>
    </tr>
    <tr>
      <td>والدین مجاز</td>
      <td>یک <code>&lt;head&gt;</code> که شامل عنصر <code>&lt;base&gt;</code> دیگری نباشد</td>
    </tr>
    <tr>
      <td>نقش ARIA ضمنی</td>
      <td><a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a></td>
    </tr>
    <tr>
      <td>نقش‌های ARIA مجاز</td>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <td>رابط DOM</td>
      <td><code>HTMLBaseElement</code></td>
    </tr>
  </tbody>
</table>

## Specifications

## Browser compatibility