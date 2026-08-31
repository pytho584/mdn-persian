---
title: "ARIA: structure role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structure_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: structure role"
short-title: structure
slug: Web/Accessibility/ARIA/Reference/Roles/structure_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#structure
sidebar: accessibilitysidebar
---

نقش `structure` برای عناصر ساختاری سند است.

> [!WARNING]
> نقش `structure` یک [abstract role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#6._abstract_roles) است. برای کامل بودن مستندات در اینجا آورده شده است. نباید توسط نویسندگان وب استفاده شود. از HTML و نقش‌های ساختاری زیرکلاس استفاده کنید.

## توضیحات

`Structure` یک [abstract role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#6._abstract_roles) ابرکلاس برای ساختارهای سند است، مانند [`document`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role)،
[`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) و [`sectionhead`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/sectionhead_role)، که با کمک به فناوری‌های کمکی برای تعیین محتوای فعال در برابر محتوای ایستای سند، از دسترس‌پذیری محتوای وب پویا پشتیبانی می‌کنند. برخی از نقش‌های زیرکلاس، مانند
[`section` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/section_role)، به نوبه خود ابرکلاس نقش‌های دیگر هستند.

نقش `structure` ابرکلاس همه نقش‌های ساختار سند است که برای ارائه توصیف ساختاری برای بخشی از محتوا استفاده می‌شوند. بیشتر نقش‌های ساختاری دیگر نباید استفاده شوند، زیرا مرورگرها اکنون از عنصر HTML معنایی با همان معنی پشتیبانی می‌کنند. نقش‌های ساختاری بدون معادل HTML، مانند [`presentation` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) که به این معنی است که محتوا صرفاً نمایشی است، اطلاعاتی درباره ساختار سند به فناوری‌های کمکی مانند صفحه‌خوان‌ها ارائه می‌دهند، زیرا برچسب‌های HTML بومی معادل در دسترس نیستند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ARIA: `roletype` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/roletype_role)
- [ARIA: `generic` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role)
- [ARIA: `presentation` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role)
- [ARIA: `range` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role)
- [ARIA: `section` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/section_role)
- [ARIA: `sectionhead` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/sectionhead_role)

<!-- these shouldn't be used so we shouldn't link to them
- [ARIA: `application` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
- [ARIA: `document` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role)
- [ARIA: `rowgroup` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
- [ARIA: `separator` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
-->