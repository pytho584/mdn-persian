---
title: "ARIA: searchbox role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: searchbox role"
short-title: searchbox
slug: Web/Accessibility/ARIA/Reference/Roles/searchbox_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#searchbox
sidebar: accessibilitysidebar
---

نقش `searchbox` نشان‌دهنده عنصری است که نوعی `textbox` برای تعیین معیارهای جستجو است.

## توضیحات

می‌توان از `searchbox` به جای [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role) استفاده کرد، زمانی که جعبه متن درون عنصری با نقش [`search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role) قرار دارد. معادل معنایی `searchbox` در HTML، {{HTMLElement('input')}} از نوع `search` یعنی [`<input type="search">`](/en-US/docs/Web/HTML/Reference/Elements/input/search) است که در صورت امکان باید به جای آن استفاده شود.

`searchbox` باید دارای یک نام دسترس‌پذیر باشد. اگر نقش `searchbox` روی یک عنصر HTML {{HTMLElement('input')}} اعمال شود، باید از یک {{HTMLElement('label')}} مرتبط استفاده کرد. در غیر این صورت، اگر برچسب قابل مشاهده وجود دارد از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) استفاده کنید، یا اگر برچسب قابل مشاهده وجود ندارد از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید.

صفحه‌خوان عبارت «search box»، «search edit» یا «search field» را به همراه نام دسترس‌پذیر اعلام می‌کند. اگر «search» در برچسب گنجانده شده باشد، این امر می‌تواند تکراری باشد.

## مثال‌ها

```html
<div tabindex="0" aria-label="search" role="searchbox" contenteditable></div>
```

در حالی که مثال بالا معتبر است، نوشتن کد زیر برای کاربر صفحه‌خوان ساده‌تر، خلاصه‌تر و با تکرار کمتر است:

```html
<input type="search" />
```

در ادامه یک فرم جستجو با یک searchbox و دکمه، ناحیه زنده ARIA و ظرفی برای نتایج جستجو آورده شده است.

```html
<form role="search">
  <input
    type="search"
    role="searchbox"
    aria-description="search results will appear below"
    id="search"
    value="" />
  <label for="search">Search this site</label>
  <button>Submit search</button>
</form>
<div aria-live="polite" role="region" aria-atomic="true">
  <div class="sr-only"></div>
</div>
<div id="search-results"></div>
```

افزودن `role="searchbox"` زمانی که فرم از نوع `search` است و برچسب نشان می‌دهد عنصر یک جستجو است، ممکن است باعث شود فناوری کمکی چیزی مانند «search search this site search box» را اعلام کند که تکراری است. بنابراین گنجاندن `role="searchbox"` ضروری نیست:

```html
<input
  type="search"
  aria-description="search results will appear below"
  id="search"
  value="" />
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`<input type="search">`](/en-US/docs/Web/HTML/Reference/Elements/input/search)
- [ARIA: `search` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)
- [ARIA: `textbox` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)