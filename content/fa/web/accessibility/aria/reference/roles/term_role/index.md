---
title: "ARIA: term role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: term role"
short-title: term
slug: Web/Accessibility/ARIA/Reference/Roles/term_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#term
sidebar: accessibilitysidebar
---

نقش `term` می‌تواند برای یک واژه یا عبارت با یک [`definition`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/definition_role) اختیاری متناظر استفاده شود.

## توضیحات

نقش `term` می‌تواند برای یک واژه یا عبارت با یک [`definition`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/definition_role) اختیاری متناظر استفاده شود. از نظر معنایی معادل عنصر HTML {{HTMLElement('dfn')}} و عنصر اصطلاح تعریف ({{HTMLElement('dt')}}) در فهرست تعریف ({{HTMLElement('dl')}} ) است.

نقش `term` برای شناسایی صریح یک واژه یا عبارت استفاده می‌شود که تعریفی برای آن توسط نویسنده ارائه شده است یا انتظار می‌رود توسط کاربر ارائه شود. اگر تعریفی وجود داشته باشد، یا یک فرم یا کنترل فرم برای وارد کردن تعریف وجود داشته باشد، نویسندگان باید [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) را برای اشاره به عنصر مرتبط تنظیم کنند.

از `role="term"` در عناصر تعاملی مانند پیوندها استفاده نکنید، زیرا می‌تواند با توانایی کاربران فناوری کمکی برای تعامل با عنصر تداخل کند. همچنین، خود واژه، نام دسترس‌پذیر است، بنابراین از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) استفاده نکنید.

> [!WARNING]
> نام دسترس‌پذیر باید خود واژه باشد، بنابراین از `aria-label` یا `aria-labelledby` استفاده نکنید.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

هیچ‌کدام.

### تعاملات صفحه‌کلید

هیچ‌کدام.

### ویژگی‌های جاوااسکریپت مورد نیاز

هیچ‌کدام.

## مثال‌ها

```html
<p>
  <span role="term">Mansplaining</span>,
  <span role="definition"
    >a portmanteau of "man" and "explain", is the patronizing act of explaining
    without being asked to do so, to someone already learned on the topic, often
    after someone has already explained it</span
  >.
</p>
```

با معناشناسی بهتر، می‌توان مثال بالا را به صورت زیر نیز نوشت:

```html
<p>
  <dfn role="term">Mansplaining</dfn>,
  <span role="definition"
    >a portmanteau of "man" and "explain", is the patronizing act of explaining
    without being asked to do so, to someone already learned on the topic, often
    after someone has already explained it</span
  >.
</p>
```

یا بدون هیچ‌گونه ARIA (اما احتمالاً نه به شکلی که بخواهید آن را ارائه دهید).

```html
<dl>
  <dt>Mansplaining</dt>
  <dd>
    A portmanteau of "man" and "explain", is the patronizing act of explaining
    without being asked to do so, to someone already learned on the topic, often
    after someone has already explained it.
  </dd>
</dl>
```

## نگرانی‌های دسترس‌پذیری

از `role="term"` در عناصر تعاملی مانند پیوندها استفاده نکنید، زیرا ممکن است با توانایی کاربر فناوری کمکی برای تعامل با عنصر تداخل کند.

## بهترین شیوه‌ها

اجازه دهید خود واژه نام دسترس‌پذیر را تعریف کند. از `aria-label` یا `aria-labelledby` استفاده نکنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش ARIA: `definition`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/definition_role).
- عنصر HTML {{HTMLElement('dfn')}}