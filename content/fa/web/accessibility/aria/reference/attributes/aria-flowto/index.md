---
title: "ARIA: aria-flowto attribute"
short-title: aria-flowto
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-flowto
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-flowto
sidebar: accessibilitysidebar
translated_by: "n8n + AI"
---

ویژگی سراسری `aria-flowto` عنصر (یا عناصر) بعدی را در ترتیب خواندن جایگزین محتوا مشخص می‌کند. این امکان را به فناوری کمکی می‌دهد تا با صلاحدید کاربر، حالت پیش‌فرض عمومی خواندن به ترتیب منبع سند را نادیده بگیرد.

## توضیحات

صفحات وب باید به صورت ترتیبی قابل پیمایش باشند. به همین دلیل، توسعه‌دهندگان از استفاده از ویژگی سراسری [tabindex](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) که می‌تواند ترتیب تب را تغییر دهد و ویژگی CSS {{CSSXRef('order')}} که می‌تواند ترتیب بصری را از ترتیب DOM تغییر دهد، منع می‌شوند. با این حال، در شرایط نادر، یک مسیر خواندن متفاوت از ترتیب منبع مورد نیاز است. برای چنین مواردی، ویژگی `aria-flowto` می‌تواند محتوا را برای کاربران فناوری‌های کمکی در دسترس‌تر کند.

ویژگی سراسری `aria-flowto` به نویسنده اجازه می‌دهد تا به کاربران فناوری کمکی نشان دهد که کدام عنصر یا عناصر ممکن است بعداً مورد تمرکز قرار گیرند، و یک ترتیب خواندن جایگزین برای ترتیب منبع فراهم می‌کند. این به فناوری کمکی اجازه می‌دهد تا یک سند را به ترتیبی غیر از ترتیب پیش‌فرض خواندن منبع سند بخواند.

وقتی `aria-flowto` یک ارجاع [id](/en-US/docs/Web/HTML/Reference/Global_attributes/id) واحد دارد، به فناوری‌های کمکی اجازه می‌دهد تا به درخواست کاربر، به عنصر هدف‌گذاری شده توسط آن `id` بروند به جای اینکه سند را به ترتیب DOM بخوانند. وقتی مقدار `aria-flowto` از یک لیست جدا شده با فاصله از چندین ارجاع `id` استفاده می‌کند، فناوری کمکی می‌تواند لیستی از انتخاب‌های مسیر را در اختیار کاربر قرار دهد، که هر `id` ارجاع داده شده یک انتخاب است. نام‌های انتخاب مسیر با نام دسترس‌پذیر هر عنصر هدف از ویژگی `aria-flowto` تعیین می‌شود.

> [!NOTE]
> تنظیم `aria-flowto` بر ترتیب تب محتوا تأثیر نمی‌گذارد. فقط به کاربران این گزینه را می‌دهد که مسیر محتوایی را دنبال کنند که با ترتیب DOM مطابقت ندارد، هنگام استفاده از فناوری‌ای که از این ویژگی پشتیبانی می‌کند.

## مقادیر

- `id`
  - : `id` عنصر بعدی در ترتیب خواندن جایگزین.
- لیست `id`
  - : لیست جدا شده با فاصله از مقادیری که به مقادیر `id` عناصری که کاربر ممکن است بخواهد بعداً در ترتیب خواندن جایگزین محتوا به آن‌ها برود، ارجاع می‌دهد.

## رابط‌های مرتبط

- {{domxref("Element.ariaFlowToElements")}}
  - : ویژگی `ariaFlowToElements` بخشی از رابط هر عنصر است.
    مقدار آن آرایه‌ای از نمونه‌های زیرکلاس‌های {{domxref("Element")}} است که ارجاعات `id` را در ویژگی `aria-flowto` منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).
- {{domxref("ElementInternals.ariaFlowToElements")}}
  - : ویژگی `ariaFlowToElements` بخشی از رابط هر عنصر سفارشی است.
    مقدار آن آرایه‌ای از نمونه‌های زیرکلاس‌های {{domxref("Element")}} است که ارجاعات `id` را در ویژگی `aria-flowto` منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).

## نقش‌های مرتبط

در **همه** نقش‌ها استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- ویژگی HTML [id](/en-US/docs/Web/HTML/Reference/Global_attributes/id)
- ویژگی HTML [tabindex](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex)
- ویژگی CSS {{CSSXRef('order')}}
- [WCAG: ترتیب منبع](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable#guideline_2.4_—_navigable_provide_ways_to_help_users_navigate_find_content_and_determine_where_they_are)
- [استفاده از aria-flowto](https://www.w3.org/WAI/GL/wiki/Using_aria-flowto) - ویکی W3