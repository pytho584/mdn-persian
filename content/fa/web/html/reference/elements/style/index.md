---
title: "<style> HTML style information element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/style"
translated_by: "n8n + AI"
---

عنصر `<style>` در HTML حاوی اطلاعات استایل برای یک سند یا بخشی از آن است. این عنصر شامل CSS می‌شود که روی محتوای سند حاوی `<style>` اعمال می‌گردد.

در مثال زیر، یک استایل‌شیت ساده به یک سند اعمال می‌کنیم:

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Test page</title>
    <style>
      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <p>This is my paragraph.</p>
  </body>
</html>
```

#### نتیجه

{{EmbedLiveSample('A_basic_stylesheet', '100%', '100')}}

عنصر `<style>` معمولاً درون `<head>` سند قرار می‌گیرد. همچنین می‌توان آن را در هرجایی که محتوای metadata مجاز است، مثلاً درون `<template>` قرار داد.

اگر چندین عنصر `<style>` و `<link>` در سند خود داشته باشید، به ترتیبی که در سند قرار گرفته‌اند روی DOM اعمال می‌شوند — مطمئن شوید آن‌ها را به ترتیب درست قرار داده‌اید تا از مشکلات cascade غیرمنتظره جلوگیری شود.

همانند عناصر `<link>`، عناصر `<style>` می‌توانند دارای attribute `media` باشند که شامل [media queries](/en-US/docs/Web/CSS/Guides/Media_queries) می‌شود. این امکان را می‌دهد که استایل‌شیت‌های داخلی را به‌صورت انتخابی بر اساس ویژگی‌های media مانند عرض viewport به سند اعمال کنید.

## Attributes

این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `blocking`
  - : این attribute به‌طور صریح مشخص می‌کند که برخی عملیات‌ها باید تا زمان دریافت منابع فرعی حیاتی (critical subresources) و اعمال استایل‌شیت به سند مسدود شوند. استایل‌شیت‌های import شده با {{cssxref("@import")}} معمولاً به‌عنوان منابع فرعی حیاتی در نظر گرفته می‌شوند، درحالی که {{cssxref("background-image")}} و فونت‌ها این‌طور نیستند. عملیات‌هایی که باید مسدود شوند، باید به‌صورت فهرست جدا شده با فاصله از توکن‌های blocking زیر باشند. در حال حاضر فقط یک توکن وجود دارد:
    - `render`: رندر محتوا روی صفحه مسدود می‌شود.

    > [!NOTE]
    > فقط عناصر `style` درون `<head>` سند می‌توانند رندر را مسدود کنند. به‌طور پیش‌فرض، یک عنصر `style` در `<head>` زمانی که مرورگر در حین تجزیه آن را کشف می‌کند، رندر را مسدود می‌کند. اگر چنین عنصر `style`ای به‌صورت پویا از طریق اسکریپت اضافه شود، باید `blocking = "render"` را نیز تنظیم کنید تا رندر را مسدود کند.

- `media`
  - : این attribute مشخص می‌کند که استایل در کدام media اعمال شود. مقدار آن یک [media query](/en-US/docs/Web/CSS/Guides/Media_queries/Using) است که اگر attribute وجود نداشته باشد، مقدار پیش‌فرض `all` خواهد بود.
- `nonce`
  - : یک nonce رمزنگاری (عدد یک‌بار مصرف) که برای اجازه دادن به استایل‌های inline در [style-src Content-Security-Policy](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/style-src) استفاده می‌شود. سرور باید هر بار که یک policy را ارسال می‌کند، یک مقدار nonce یکتا تولید کند. ارائه یک nonce که قابل حدس نباشد حیاتی است، زیرا در غیر این صورت دور زدن policy منبع ساده است.
- `title`
  - : این attribute مجموعه‌های [alternative style sheet](/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet) را مشخص می‌کند.

### Attributes منسوخ

- `type` {{deprecated_inline}}
  - : این attribute نباید ارائه شود: اگر ارائه شود، تنها مقادیر مجاز عبارت‌اند از رشته خالی یا تطبیق case-insensitive با `text/css`.

## مثال‌ها

### یک استایل‌شیت پایه

در مثال زیر، یک استایل‌شیت کوتاه را به یک سند اعمال می‌کنیم:

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Test page</title>
    <style>
      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <p>This is my paragraph.</p>
  </body>
</html>
```

#### نتیجه

{{EmbedLiveSample('A_basic_stylesheet', '100%', '100')}}

### استفاده از `<style>` درون `<template>`

یک عنصر `<style>` را می‌توان درون عنصر {{HTMLElement("template")}} قرار داد. استایل‌ها تا زمانی که محتوای template نمونه‌سازی و به سند اضافه نشود، غیرفعال باقی می‌مانند.

```html
<template id="card-template">
  <style>
    .card {
      border: 1px solid #cccccc;
      padding: 1rem;
      border-radius: 0.5rem;
    }
  </style>

  <div class="card">Template content</div>
</template>
```

### چندین عنصر style

در این مثال دو عنصر `<style>` قرار داده‌ایم — توجه کنید که اعلان‌های متضاد در عنصر `<style>` بعدی، اعلان‌های قبلی را override می‌کنند (اگر [specificity](/en-US/docs/Web/CSS/Guides/Cascade/Specificity) یکسانی داشته باشند).

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Test page</title>
    <style>
      p {
        color: white;
        background-color: blue;
        padding: 5px;
        border: 1px solid black;
      }
    </style>
    <style>
      p {
        color: blue;
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <p>This is my paragraph.</p>
  </body>
</html>
```

#### نتیجه

### شامل کردن یک media query

در این مثال روی مثال قبلی بنا می‌کنیم و یک ویژگی `media` به عنصر `<style>` دوم اضافه می‌کنیم تا فقط زمانی که viewport عرض کمتر از ۵۰۰px داشته باشد اعمال شود.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Test page</title>
    <style>
      p {
        color: white;
        background-color: blue;
        padding: 5px;
        border: 1px solid black;
      }
    </style>
    <style media="(width < 500px)">
      p {
        color: blue;
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <p>This is my paragraph.</p>
  </body>
</html>
```

#### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content">محتوای متادیتا</a>
      </td>
    </tr>
    <tr>
      <th>محتوای مجاز</th>
      <td>
        محتوای متنی که با ویژگی <code>type</code> مطابقت دارد، یعنی <code>text/css</code>.
      </td>
    </tr>
    <tr>
      <th>حذف تگ</th>
      <td>هیچ‌کدام از تگ‌ها قابل حذف نیستند.</td>
    </tr>
    <tr>
      <th>والدین مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content">محتوای متادیتا</a> را قبول کند.
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
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th>رابط DOM</th>
      <td>HTMLStyleElement</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- عنصر `<link>` که به ما امکان اعمال شیوه‌نامه‌های خارجی به سند را می‌دهد.
- [شیوه‌نامه‌های جایگزین](/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet)