---
title: "ARIA: widget role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/widget_role"
translated_by: "n8n + AI"
short-title: widget
slug: Web/Accessibility/ARIA/Reference/Roles/widget_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#widget
sidebar: accessibilitysidebar
---

نقش **`widget`**، یک [نقش انتزاعی](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#6._abstract_roles)، یک جزء تعاملی از یک رابط کاربری گرافیکی (GUI) است.

> [!WARNING]
> نقش `widget` یک نقش انتزاعی است که برای هستی‌شناسی استفاده می‌شود. این نقش برای کامل بودن مستندات در اینجا آورده شده است. نباید توسط نویسندگان وب استفاده شود.

## توضیحات

نقش انتزاعی `widget` یک نقش ابرکلاس برای برخی عناصر GUI تعاملی و نقش‌های گروه‌بندی است. `role="widget"` نباید با نقش‌های ویجتی مانند `option`، `menuitem` و `searchbox` اشتباه گرفته شود.

نقش `widget` یک ابرکلاس برای چندین نقش GUI تعاملی انتزاعی از جمله [`command`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/command_role)، [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)، [`input`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/input_role)، [`range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role) و [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) (در صورت قابل تمرکز بودن) است که نباید توسط نویسندگان وب استفاده شوند.

نقش انتزاعی `widget` همچنین یک ابرکلاس برای برخی نقش‌های گروه‌بندی است که می‌توانند توسط نویسندگان وب استفاده شوند، از جمله [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)، [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) (زمانی که قابل تمرکز نیست) و [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)، که می‌توانند و باید در صورت لزوم استفاده شوند. هنگامی که کاربر به یکی از این نقش‌های غیرانتزاعی ویجت پیمایش می‌کند، رویدادهای صفحه کلید می‌توانند به حالت مرور برنامه تغییر کرده و رویدادهای صفحه کلید را به مرورگر منتقل کنند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ARIA: نقش `roletype`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/roletype_role)

- [ARIA: نقش `command`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/command_role)
- [ARIA: نقش `composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)
- [ARIA: نقش `gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [ARIA: نقش `input`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/input_role)
- [ARIA: نقش `range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role)
- [ARIA: نقش `row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [ARIA: نقش `separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
- [ARIA: نقش `tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)