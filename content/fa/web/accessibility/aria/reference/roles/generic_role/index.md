---
title: "ARIA: generic role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: generic role"
short-title: generic
slug: Web/Accessibility/ARIA/Reference/Roles/generic_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#generic
sidebar: accessibilitysidebar
---

نقش `generic` یک عنصر محفظهای بدون نام ایجاد میکند که به خودی خود هیچ معنای معنایی ندارد.

> [!NOTE]
> نقش `generic` نقش ضمنی عناصر عمومی است که توسط عامل‌های کاربر استفاده می‌شود. این نقش برای کامل‌سازی مستندات در اینجا آورده شده است. نباید توسط نویسندگان وب استفاده شود.

## توضیحات

در حالی که ARIA عمدتاً برای بیان معناشناسی استفاده می‌شود، برخی عناصر وجود دارند که نباید یک نام معنایی را در معرض فناوری‌های کمکی قرار دهند. نقش `generic` نشان می‌دهد که نقش یک عنصر معادل با عناصر غیرمعنایی {{HTMLElement('div')}} و {{HTMLElement('span')}} است.

نقش `generic` برای استفاده به عنوان نقش ضمنی عناصر عمومی در زبان‌های میزبان توسط عامل‌های کاربر در نظر گرفته شده است، نه برای استفاده توسط توسعه‌دهندگان. به جای آن، برای حذف معناشناسی دسترسی ضمنی، از نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) یا `none`، عناصر {{HTMLElement('div')}} و {{HTMLElement('span')}} که هیچ معنای معنایی ندارند، یا نقش‌های محفظه‌ای معنایی مانند [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) برای گروه‌بندی معنایی فرزندان در یک محفظه نام‌گذاری شده استفاده کنید.

مانند یک عنصر با نقش `presentation`، یک عنصر با `role="generic"` می‌تواند تعداد محدودی از ویژگی‌ها و حالت‌های دسترسی را برای فرزندان خود فراهم کند، مانند ویژگی‌های [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live). با این حال، برخلاف عناصر با نقش `presentation`، عناصر `generic` در APIهای دسترسی نمایش داده می‌شوند تا فناوری‌های کمکی بتوانند ویژگی‌هایی مانند چیدمان و مرزها را جمع‌آوری کنند.

از آنجایی که نقش generic بی‌نام است، ویژگی‌های [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) و [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) ممنوع هستند. از آنجایی که نقش عمومی است، ویژگی‌های [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) و [`aria-brailleroledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription) نیز ممنوع هستند.

> [!NOTE]
> عنصر با `role="generic"` نباید دارای نام دسترسی یا توضیح نقش باشد.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

هیچکدام. اگر یک ویژگی یا حالت سراسری ARIA تنظیم شود، `generic` یا `none` نادیده گرفته می‌شوند و نقش ضمنی عنصر استفاده خواهد شد.

## مثال‌ها

این نقش برای استفاده توسط عامل‌های کاربر است و نه توسط توسعه‌دهندگان. بنابراین، هیچ مثال مناسبی وجود ندارد.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عناصر HTML {{HTMLElement('div')}} و {{HTMLElement('span')}}
- نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role)
- نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)