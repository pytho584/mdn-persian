---
title: "<script type> HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/script/type"
translated_by: "n8n + AI"
---

# ویژگی HTML `type` در عنصر `<script>`

ویژگی **`type`** در عنصر [`<script>`](en-US/docs/Web/HTML/Reference/Elements/script) نوع اسکریپتی را مشخص می‌کند که عنصر نمایش می‌دهد: اسکریپت کلاسیک، import map، ماژول جاوااسکریپت، قوانین حدس و گمان (speculation rules) یا یک بلوک داده.

## مقدار

مقدار این ویژگی نشان‌دهنده نوع داده‌ای است که اسکریپت نمایش می‌دهد و یکی از موارد زیر خواهد بود:

- **ویژگی تنظیم نشده (پیش‌فرض)، رشته خالی، یا MIME type جاوااسکریپت**
  - : نشان می‌دهد که اسکریپت یک «اسکریپت کلاسیک» است و حاوی کد جاوااسکریپت می‌باشد. توصیه می‌شود اگر اسکریپت به کد جاوااسکریپت اشاره دارد، نویسندگان به جای مشخص کردن MIME type، این ویژگی را حذف کنند. MIME type های جاوااسکریپت در [فهرست انواع رسانه IANA](en-US/docs/Web/HTTP/Guides/MIME_types#textjavascript) آمده‌اند.
- [`importmap`](en-US/docs/Web/HTML/Reference/Elements/script/type/importmap)
  - : این مقدار نشان می‌دهد که بدنه عنصر شامل یک import map است. import map یک شیء JSON است که توسعه‌دهندگان می‌توانند از آن برای کنترل نحوه حل کردن مشخص‌کننده‌های ماژول توسط مرورگر هنگام وارد کردن [ماژول‌های جاوااسکریپت](en-US/docs/Web/JavaScript/Guide/Modules#importing_modules_using_import_maps) استفاده کنند.
- `module`
  - : این مقدار باعث می‌شود کد به عنوان یک ماژول جاوااسکریپت در نظر گرفته شود. پردازش محتوای اسکریپت به تأخیر می‌افتد. ویژگی‌های `charset` و `defer` هیچ تأثیری ندارند. برای اطلاعات بیشتر در مورد استفاده از `module`، به راهنمای [ماژول‌های جاوااسکریپت](en-US/docs/Web/JavaScript/Guide/Modules) مراجعه کنید. برخلاف اسکریپت‌های کلاسیک، اسکریپت‌های ماژول برای واکشی از مبدأ متقاطع (cross-origin) نیاز به استفاده از پروتکل CORS دارند.
- [`speculationrules`](en-US/docs/Web/HTML/Reference/Elements/script/type/speculationrules) {{experimental_inline}}
  - : این مقدار نشان می‌دهد که بدنه عنصر شامل قوانین حدس و گمان (speculation rules) است. قوانین حدس و گمان به شکل یک شیء JSON هستند که تعیین می‌کنند چه منابعی باید توسط مرورگر از قبل واکشی (prefetch) یا از پیش رندر (prerender) شوند. این بخشی از [Speculation Rules API](en-US/docs/Web/API/Speculation_Rules_API) است.
- **هر مقدار دیگری**
  - : محتوای تعبیه‌شده به عنوان یک بلوک داده در نظر گرفته می‌شود و توسط مرورگر پردازش نمی‌شود. توسعه‌دهندگان باید از یک MIME type معتبر که MIME type جاوااسکریپت نیست برای نمایش بلوک‌های داده استفاده کنند. تمام ویژگی‌های دیگر نادیده گرفته می‌شوند، از جمله ویژگی `src`.

> **نکته:** در مرورگرهای قدیمی‌تر، `type` زبان اسکریپت‌نویسی کد تعبیه‌شده یا واردشده (از طریق ویژگی `src`) را مشخص می‌کرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}