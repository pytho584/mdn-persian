---
title: "ARIA: directory role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/directory_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: directory role"
short-title: directory
slug: Web/Accessibility/ARIA/Reference/Roles/directory_role
page-type: aria-role
status:
  - deprecated
spec-urls: https://w3c.github.io/aria/#directory
sidebar: accessibilitysidebar
---

نقش `directory` برای فهرستی از ارجاعات به اعضای یک گروه، مانند فهرست مطالب ایستا، استفاده می‌شد.

> [!WARNING]
> نقش `directory` در ARIA 1.2 منسوخ شده است.

## توصیف

فهرست مطالب (directory) یک فهرست مطالب ایستا است، چه پیوندی داشته باشد چه نداشته باشد. این شامل فهرست‌های مطالب ساخته‌شده با فهرست‌ها، از جمله فهرست‌های تودرتو می‌شود. با این حال، فهرست‌های مطالب پویا ممکن است به جای آن از نقش درخت (tree) استفاده کنند.

نقش منسوخ‌شده `directory` برای فهرست‌های ارجاعات به اعضای یک گروه، مانند فهرست مطالب ایستا، استفاده می‌شد.
به جای آن از نقش [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role) استفاده کنید. یا حتی بهتر، از عناصر {{HTMLElement('ul')}} یا {{HTMLElement('ol')}} استفاده کنید، زیرا استفاده از `directory` هیچ مزیت اضافی برای کاربران فناوری کمکی فراهم نمی‌کند.

## مشخصات

{{Specifications}}

## جستارهای وابسته

- [نقش `list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)
- عنصر {{HTMLElement('ul')}}
- عنصر {{HTMLElement('ol')}}