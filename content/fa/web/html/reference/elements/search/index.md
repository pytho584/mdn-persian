---
title: "<search> HTML generic search element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/search"
translated_by: "n8n + AI"
---

المان `<search>` HTML (element) یک کانتینر است که بخش‌هایی از سند یا برنامه را شامل می‌شود که دارای کنترل‌های فرم (form controls) یا محتوای دیگری مرتبط با انجام عملیات جستجو یا فیلتر کردن هستند. المان `<search>` به صورت معنایی مشخص می‌کند که هدف محتوای داخل آن قابلیت جستجو یا فیلتر کردن است. عملکرد جستجو یا فیلتر می‌تواند برای وب‌سایت یا برنامه، صفحه یا سند وب فعلی، یا کل اینترنت یا زیرمجموعه‌ای از آن باشد.

## ویژگی‌ها (Attributes)

این المان فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

المان `<search>` برای نمایش نتایج جستجو در نظر گرفته نشده است. در عوض، نتایج جستجو یا فیلتر شده باید به عنوان بخشی از محتوای اصلی آن صفحه وب ارائه شوند. با این حال، پیشنهادها و لینک‌هایی که بخشی از قابلیت «جستجوی سریع» درون عملکرد جستجو یا فیلتر هستند، به‌طور مناسب درون محتوای المان `<search>` قرار می‌گیرند، زیرا این‌ها ویژگی‌های جستجو محسوب می‌شوند.

## دسترسی (Accessibility)

المان `<search>` یک landmark از نوع [`search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role) تعریف می‌کند. این کار نیاز به اضافه کردن `role=search` به یک المان {{HTMLElement('form')}} را از بین می‌برد.

## مثال‌ها

### فرم جستجوی هدر

این مثال استفاده از `<search>` را به عنوان کانتینری برای جستجو درون هدر یک وب‌سایت نشان می‌دهد تا جستجوی سراسری در سایت انجام شود. `<search>` یک کانتینر معنایی برای المان {{HTMLElement("form")}} است که query جستجوی وارد شده توسط کاربر را به سرور ارسال می‌کند.

#### HTML

```html
<header>
  <h1>Movie website</h1>
  <search>
    <form action="./search/">
      <label for="movie">Find a Movie</label>
      <input type="search" id="movie" name="q" />
      <button type="submit">Search</button>
    </form>
  </search>
</header>
```

#### نتیجه

### جستجوی برنامه وب

این مثال محتوای احتمالی DOM را هنگام پیاده‌سازی داینامیک قابلیت جستجوی JavaScript در یک برنامه وب نشان می‌دهد. وقتی عملکرد جستجو کاملاً با JavaScript پیاده‌سازی می‌شود، اگر فرمی ارسال نشود، نیازی به المان {{HTMLElement("form")}} یا دکمه submit {{HTMLElement("button")}} نیست. برای معناداری، المان `<search>` برای نگهداری قابلیت جستجو و فیلتر قرار داده شده است.

#### HTML

```html
<search>
  <label>
    Find and filter your query
    <input type="search" id="query" />
  </label>
  <label>
    <input type="checkbox" id="exact-only" />
    Exact matches only
  </label>

  <section>
    <h3>Results:</h3>
    <ul id="results">
      <!-- search result content -->
    </ul>
    <output id="no-results">
      <!-- no results content -->
    </output>
  </section>
</search>
```

#### نتیجه

> [!NOTE]
> به یاد داشته باشید که برخی کاربران JavaScript ندارند، و هیچ‌کدام از کاربران شما تا زمانی که JavaScript با موفقیت دانلود، تجزیه و اجرا نشده باشد، از آن استفاده نمی‌کنند. اطمینان حاصل کنید که کاربران شما می‌توانند به محتوای سایت شما با JavaScript غیرفعال دسترسی داشته باشند.

### چندین جستجو

این مثال صفحه‌ای با دو ویژگی جستجو را نشان می‌دهد. اولی جستجوی سراسری سایت است که در هدر قرار دارد. دومی جستجو و فیلتر بر اساس زمینه صفحه است که در مثال ما جستجوی ماشین است.

#### HTML

```html
<body>
  <header>
    <h1>Car rental agency</h1>
    <search title="Website">...</search>
  </header>
  <main>
    <h2>Cars available for rent</h2>
    <search title="Cars">
      <h3>Filter results</h3>
      ...
    </search>
    <article>
      <!-- search result content -->
    </article>
  </main>
</body>
```

#### نتیجه

## خلاصه فنی (Technical summary)

| دسته‌بندی محتوا (Content categories) | Flow content, phrasing content, palpable content |
|---|---|
| محتوای مجاز (Permitted content) | Flow content, اما بدون فرزندان `<main>`, `<nav>`, `<aside>`, `<footer>`, `<header>`, یا `<search>` (در غیر این صورت عنصر `<search>` معتبر نیست). |
| حذف تگ (Tag omission) | هیچ‌کدام، هم تگ شروع و هم تگ پایانی الزامی است. |
| والدین مجاز (Permitted parents) | هر عنصری که محتوای جریانی (flow content) را بپذیرد. |
| نقش ARIA ضمنی (Implicit ARIA role) | `search` |
| رابط DOM (DOM interface) | `HTMLElement` |

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">Content categories</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>, <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content">palpable content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ تگ آغازین و پایانی هر دو اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role">search</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role"><code>form</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role"><code>region</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role"><code>search</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- سایر عناصر مرتبط با جستجو: <code>&lt;header&gt;</code>, <code>&lt;footer&gt;</code>, <code>&lt;aside&gt;</code>, <code>&lt;nav&gt;</code>, <code>&lt;form&gt;</code>
- [ARIA: Search role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)