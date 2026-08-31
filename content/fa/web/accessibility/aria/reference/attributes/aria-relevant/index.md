---
title: "ARIA: aria-relevant attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant"
translated_by: "n8n + AI"

---
title: "ARIA: ویژگی aria-relevant"
short-title: aria-relevant
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-relevant
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-relevant
sidebar: accessibilitysidebar

در نواحی زندهٔ ARIA استفاده می‌شود، ویژگی سراسری `aria-relevant` مشخص می‌کند که عامل کاربر (user agent) چه اعلان‌هایی را هنگامی که [درخت دسترسی‌پذیری](/en-US/docs/Glossary/Accessibility_tree) درون یک ناحیهٔ زنده تغییر می‌کند، فعال کند.

## توضیحات

[نواحی زندهٔ ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) بخش‌هایی از یک صفحهٔ وب هستند که وقتی توجه کاربر ممکن است در جای دیگری باشد، به‌روز می‌شوند. هنگامی که یک به‌روزرسانی خارج از فوکوس صفحه‌کلید کاربر است، فناوری‌های کمکی مانند صفحه‌خوان‌ها از یک ناحیهٔ زنده برای گزارش به‌روزرسانی به کاربر استفاده می‌کنند.

نمونه‌هایی از نواحی زنده عبارتند از تیترهای خبری متحرک، تیکرهای سهام، پنجره‌های گفتگو و تابلوهای امتیاز. این موارد بدون تعامل کاربر به‌روز می‌شوند. برخی به‌روزرسانی‌ها برای کاربر مهم هستند که بداند. آنها «مرتبط» هستند. برخی دیگر نیستند. `aria-relevant` برای توصیف نوع تغییراتی که در یک ناحیهٔ [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) رخ داده و کدام‌ها مرتبط و باید اعلام شوند، استفاده می‌شود.

مقدار یک لیست جدا شده با فاصله از انواع تغییرات است، شامل `additions`، `removals` و `text`، با یک مخفف `all` به معنی هر سه مورد.

وقتی `aria-relevant` تعریف نشده باشد، مقدار از نزدیک‌ترین جد (ancestor) با مقدار تعریف‌شده به ارث برده می‌شود. مقادیر به‌ارث‌برده جمع‌پذیر نیستند؛ مقدار ارائه‌شده روی یک عنصر فرزند به‌طور کامل هر مقدار به‌ارث‌برده از یک عنصر جد را لغو می‌کند. وقتی یک ناحیهٔ زنده ویژگی `aria-relevant` را تنظیم نکرده باشد و هیچ جدی با این ویژگی تنظیم‌شده نداشته باشد، به طور پیش‌فرض `additions text` است، یعنی گره‌های عنصر به درخت دسترسی‌پذیری درون ناحیهٔ زنده اضافه می‌شوند، و همچنین محتوای متنی یا یک جایگزین متنی به هر فرزندی در درخت دسترسی‌پذیری ناحیهٔ زنده اضافه می‌شود. این به این دلیل است که به طور کلی تغییرات متنی و اضافه‌شدن گره‌ها مرتبط هستند، اما حذف گره‌ها مرتبط نیست.

اگرچه مقدار پشتیبانی‌شده‌ای نیست، اگر مقدار `none` منطقی‌ترین باشد، آن ناحیه نباید یک ناحیهٔ زنده باشد.

مقادیر `removals` و `all` باید با احتیاط استفاده شوند. برای مثال، وقتی یک گل در جام جهانی اتفاق می‌افتد، امتیاز جدید (اضافه‌شدن) مهم است، مقدار قدیمی (حذف) مهم نیست. فناوری‌های کمکی فقط زمانی باید از حذف محتوا مطلع شوند که حذف آن نشان‌دهندهٔ یک تغییر مهم باشد، مانند زمانی که یک بازیکن از بازی خارج می‌شود.

## مقادیر

- `additions`
  - : گره‌های عنصر به درخت دسترسی‌پذیری درون ناحیهٔ زنده اضافه می‌شوند.
- `all`
  - : مخفف `additions removals text`.
- `removals`
  - : محتوای متنی، یک جایگزین متنی، یا یک گره عنصر درون ناحیهٔ زنده از درخت دسترسی‌پذیری حذف می‌شود.
- `text`
  - : محتوای متنی یا یک جایگزین متنی به هر فرزندی در درخت دسترسی‌پذیری ناحیهٔ زنده اضافه می‌شود.

## رابط‌های مرتبط

- {{domxref("Element.ariaRelevant")}}
  - : ویژگی [`ariaRelevant`](/en-US/docs/Web/API/Element/ariaRelevant) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-relevant` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaRelevant")}}
  - : ویژگی [`ariaRelevant`](/en-US/docs/Web/API/ElementInternals/ariaRelevant) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-relevant` را منعکس می‌کند.

## نقش‌های مرتبط

در **تمامی** نقش‌ها استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic)
- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)
- [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy)
- [نواحی زندهٔ ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)