---
title: "ARIA: aria-multiline attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiline"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-multiline attribute"
short-title: aria-multiline
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-multiline
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-multiline
sidebar: accessibilitysidebar
---

ویژگی `aria-multiline` مشخص می‌کند که یک `textbox` ورودی چندخطی را می‌پذیرد یا فقط یک خط را.

## توضیحات

رفتار پیش‌فرض کلیدهای <kbd>Enter</kbd> یا <kbd>Return</kbd> بین فیلدهای متنی تک‌خطی و چندخطی متفاوت است. هنگامی که تمرکز کاربر در یک `{{htmlelement("input/text", '&lt;input type="text"&gt;')}}` تک‌خطی باشد، معمولاً فشردن کلید <kbd>Enter</kbd> یا <kbd>Return</kbd> فرم را ارسال می‌کند.

هنگامی که تمرکز کاربر در یک {{HTMLElement('textarea')}} چندخطی باشد، فشردن کلید یک شکست خط درج می‌کند. این ویژگی فقط برای عناصری با نقش [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role) مرتبط است؛ ویژگی `aria-multiline` به فناوری‌های کمکی نشان می‌دهد که آیا آن جعبه متن ورودی چندخطی می‌پذیرد یا فقط تک‌خطی، و انتظارات را درباره نوع داده‌ای که باید وارد شود و عملکرد آن کلیدها تعیین می‌کند.

> [!NOTE]
> در صورت امکان، از {{HTMLElement('input')}} یا {{HTMLElement('textarea')}} HTML استفاده کنید، زیرا این عناصر دارای معناشناسی و رفتارهای داخلی هستند، به ویژگی‌ها یا اسکریپت‌نویسی ARIA نیاز ندارند و پشتیبانی از صفحه‌کلید را به‌صورت داخلی دارند.

اگر `aria-multiline="true"` تنظیم شود، به این معنی است که ویجت textbox شکست خط را در ورودی می‌پذیرد، مشابه {{HTMLElement('textarea')}} در HTML. عناصر دارای نقش `textbox` که این ویژگی را ندارند یا مقدار آن `false` است، جعبه‌های متنی ساده هستند.

هنگام طراحی جعبه‌های متن، از تمرکز و کلیدهای فشرده آگاه باشید. ARIA فقط درخت دسترس‌پذیری و در نتیجه نحوه ارائه textbox به کاربران شما توسط فناوری کمکی را تغییر می‌دهد. ARIA هیچ چیزی را درباره عملکرد یا رفتار پیش‌فرض یک عنصر تغییر نمی‌دهد. هنگامی که از عناصر معنایی HTML برای هدف و عملکرد پیش‌فرض آن‌ها استفاده نمی‌کنید، باید از جاوااسکریپت برای مدیریت رفتار و عملکرد، از جمله پاسخ به رویدادهای کلید، استفاده کنید.

## مقادیر

- `true`
  - : جعبه متن ورودی چندخطی را می‌پذیرد.
- `false`
  - : جعبه متن فقط یک خط ورودی را می‌پذیرد.

## رابط‌های مرتبط

- {{domxref("Element.ariaMultiLine")}}
  - : ویژگی [`ariaMultiLine`](/en-US/docs/Web/API/Element/ariaMultiLine) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-multiline` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaMultiLine")}}
  - : ویژگی [`ariaMultiLine`](/en-US/docs/Web/API/ElementInternals/ariaMultiLine) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-multiline` را منعکس می‌کند.

## نقش‌های مرتبط

نقش‌های استفاده‌شده:

- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)

به نقش‌های زیر به ارث می‌رود:

- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- نقش ARIA [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
- نقش ARIA [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)