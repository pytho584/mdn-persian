---
title: "ARIA: aria-autocomplete attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-autocomplete attribute"
short-title: aria-autocomplete
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete
page-type: aria-attribute
spec-urls:
  - https://w3c.github.io/aria/#aria-autocomplete,
  - https://www.w3.org/WAI/ARIA/apg/patterns/combobox/examples/combobox-autocomplete-both/
sidebar: accessibilitysidebar
---

ویژگی `aria-autocomplete` نشان می‌دهد که آیا وارد کردن متن می‌تواند نمایش یک یا چند پیش‌بینی از مقدار موردنظر کاربر را برای یک [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role) یا [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role) فعال کند و مشخص می‌کند که در صورت ارائه پیش‌بینی‌ها، آن‌ها چگونه نمایش داده شوند.

## توضیحات

تکمیل خودکار یک ویژگی رابط کاربری است که در آن پیشنهادهای درون‌خطی هنگام تایپ کاربر در یک ورودی ارائه می‌شوند. متن پیشنهادی برای تکمیل مقدار فیلد به‌صورت پویا در فیلد، بعد از مکان‌نمای ورودی ظاهر می‌شود و اگر کاربر عملی مانند رفتن به بخش بعدی (Tab) انجام دهد که باعث خروج فوکوس از فیلد شود، مقدار پیشنهادی به مقدار نهایی تبدیل می‌شود.

ویژگی `aria-autocomplete` نوع مدل تعامل تکمیل خودکار را توصیف می‌کند که یک textbox، searchbox یا combobox هنگام کمک پویا به کاربران برای تکمیل متن ورودی استفاده خواهد کرد. این ویژگی بین دو مدل تمایز قائل می‌شود: مدل **درون‌خطی** (`aria-autocomplete="inline"`) که یک مقدار پیش‌بینی‌شده واحد ارائه می‌دهد و مدل **فهرست** (`aria-autocomplete="list"`) که مجموعه‌ای از مقادیر ممکن را در یک عنصر جداگانه که در کنار یا زیر ورودی متن ظاهر می‌شود، ارائه می‌دهد؛ مشابه {{HTMLElement('datalist')}}. مقدار سوم، `aria-autocomplete="both"` برای زمانی است که رابط کاربری یک فهرست را نمایش می‌دهد و همچنین یک مقدار پیش‌بینی‌شده را شامل می‌شود. مقدار پیش‌فرض `none` است، به این معنی که textbox، searchbox یا combobox هیچ مقدار تکمیل خودکاری ارائه نمی‌دهد.

ویژگی `aria-autocomplete` فقط نوع رفتار پیش‌بینی‌کننده برای یک عنصر ورودی را برای فناوری‌های کمکی توصیف می‌کند؛ این ویژگی کارکرد واقعی را فراهم نمی‌کند. تکمیل خودکار واقعی باید با استفاده از ویژگی‌های HTML یا جاوااسکریپت ارائه شود.

اگر مقدار تکمیل خودکار پیشنهادی، مقادیری ارائه دهد که به ورودی کاربر وابسته نیستند، در نظر بگیرید که تکمیل خودکار را برای همه حذف کنید. به عنوان مثال، یک ورودی جستجو که عبارات جستجوی اخیر فیلترنشده را نمایش می‌دهد ممکن است برای تیم بازاریابی در یک سایت تجارت الکترونیک مفید باشد، اما احتمالاً برای کاربر صفحه‌خوان مفید نیست. زمانی که بهتر است مقدار `aria-autocomplete` مشخص نشود یا روی پیش‌فرض `none` تنظیم شود، احتمالاً کاربران غیر از فناوری کمکی شما نیز به این تجربه نیاز ندارند.

هنگام پیاده‌سازی قابلیت تکمیل خودکار، اطمینان حاصل کنید که بخش پیشنهادی مقدار به‌عنوان متن انتخاب‌شده نمایش داده می‌شود تا تشخیص بین ورودی کاربر و پیشنهاد ممکن شود. مطمئن شوید که وقتی مقدار پیشنهادی مقدار موردنظر نیست، کاربران بتوانند به راحتی پیشنهاد را حذف کنند یا با ادامه تایپ آن را جایگزین کنند.

هنگام پیاده‌سازی یک فهرست از مقادیر، در حالی که فهرست پیشنهادها نمایش داده می‌شود، فوکوس DOM باید روی ورودی متن باقی بماند.

- [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) را با مقدار id فهرست مقادیر پیشنهادی قرار دهید.
- [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) را مطابق با نقش عنصری که مجموعه مقادیر پیشنهادی را شامل می‌شود، قرار دهید.
- در صورت نیاز، فوکوس را مدیریت کنید، از جمله استفاده از [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) اگر ظرف مجموعه پشتیبانی می‌کند.
- از حالت [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) روی عنصر با نقش [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role) برای اطلاع‌رسانی نمایش فهرست استفاده کنید.

اگر مقدار فهرست تکمیل خودکار به‌طور خودکار هنگام از دست دادن فوکوس فیلد پذیرفته شود، فهرست باید در نقشی قرار گیرد که از `aria-activedescendant` پشتیبانی می‌کند و مقدار `aria-activedescendant` روی فیلد ورودی به‌صورت پویا تنظیم شود تا به عنصر حاوی پیشنهاد انتخاب‌شده اشاره کند.

## مقادیر

- `none` (پیش‌فرض)
  - : وقتی کاربر در حال ارائه ورودی است، هیچ پیشنهاد خودکاری نمایش داده نمی‌شود.
- `inline`
  - : `aria-autocomplete="inline"` متنی که یک راه برای تکمیل ورودی ارائه‌شده را پیشنهاد می‌کند ممکن است به‌صورت پویا بعد از مکان‌نما درج شود.
- `list`
  - : `aria-autocomplete="list"` وقتی کاربر در حال ارائه ورودی است، عنصری حاوی مجموعه‌ای از مقادیر که می‌توانند ورودی ارائه‌شده را تکمیل کنند ممکن است نمایش داده شود.
- `both`
  - : `aria-autocomplete="both"` ورودی‌ای که هر دو مدل را هم‌زمان ارائه می‌دهد. وقتی کاربر در حال ارائه ورودی است، عنصری حاوی مجموعه‌ای از مقادیر که می‌توانند ورودی ارائه‌شده را تکمیل کنند ممکن است نمایش داده شود. اگر نمایش داده شود، یک مقدار از مجموعه به‌طور خودکار انتخاب می‌شود و متن لازم برای تکمیل مقدار انتخاب‌شده به‌طور خودکار بعد از مکان‌نما در ورودی ظاهر می‌شود.

## نقش‌های مرتبط

مورد استفاده در نقش‌ها:

- نقش [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- نقش [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
- از نقش [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role) به ارث می‌برد.

## مشخصات

{{Specifications}}

## همچنین ببینید

- نقش [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- نقش [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
- نقش [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- عنصر {{HTMLElement('datalist')}} و [ویژگی `<input> list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)
- ویژگی [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls)
- ویژگی [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup)
- ویژگی [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant)
- ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)
- [مثال ترکیبی قابل ویرایش با فهرست و تکمیل خودکار درون‌خطی](https://www.w3.org/WAI/ARIA/apg/patterns/combobox/examples/combobox-autocomplete-both/)
- [Event.ariaAutoComplete](/en-US/docs/Web/API/Element/ariaAutoComplete)