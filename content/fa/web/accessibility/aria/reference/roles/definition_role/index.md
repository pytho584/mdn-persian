---
title: "ARIA: definition role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/definition_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: definition role"
short-title: definition
slug: Web/Accessibility/ARIA/Reference/Roles/definition_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#definition
sidebar: accessibilitysidebar
---

نقش ARIA `definition` نشان می‌دهد که عنصر، تعریف یک اصطلاح یا مفهوم است.

## توضیحات

نقش ARIA `definition` می‌تواند بر روی عنصری که تعریف یک اصطلاح یا مفهوم است قرار گیرد، مشابه عنصر بومی {{HTMLElement('dfn')}}. برای مرتبط کردن تعریف با `term` (اصطلاح) در حال تعریف، و برای ارائه یک نام قابل دسترسی، به اصطلاح در حال تعریف با `role="term"` با استفاده از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) ارجاع دهید.

```html-nolint
<p>
  <span role="term">Mansplaining</span>,
  <span role="definition">
    a portmanteau of "man" and "explain", is the patronizing act of explaining
    without being asked to do so, to someone already learned on the topic, often
    after someone has already explained it
  </span>.
</p>
```

> [!NOTE]
> به جای یک `<span>` با نقش‌های [`term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role) و `definition`، از عنصر {{HTMLElement('dfn')}} استفاده کنید. **همیشه در صورت وجود از عنصر بومی استفاده کنید.**

```html
<p>
  <dfn>Mansplaining</dfn>, a portmanteau of "man" and "explain", is the
  patronizing act of explaining without being asked to do so, to someone already
  learned on the topic, often after someone has already explained it.
</p>
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role)
- عنصر {{HTMLElement('dfn')}}
- عنصر {{HTMLElement('dd')}}
- عنصر {{HTMLElement('dl')}}
- عنصر {{HTMLElement('dt')}}