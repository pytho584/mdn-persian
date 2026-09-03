---
title: "Prompt API"
slug: Web/API/Prompt_API
page-type: web-api-overview
browser-compat: api.LanguageModel
spec-urls: https://webmachinelearning.github.io/prompt-api/
---

{{DefaultAPISidebar("Prompt API")}}{{SecureContext_Header}}

> [!WARNING]
> این ویژگی در حال حاضر از سوی دو سازندهٔ مرورگر با مخالفت روبه‌رو است. برای جزئیات، بخش [مواضع استانداردها](#standards_positions) را در پایین ببینید.

**Prompt API** به صفحه‌های وب امکان می‌دهد بدون نیاز به مدیریت جزئیات پیاده‌سازیِ خاصِ مدل هوش مصنوعی مورد استفاده، مستقیماً از طریق یک رابط جاوااسکریپتی به مدل زبانی‌ای که عامل کاربر (user agent) فراهم کرده است پرامپت بفرستند.

## مفاهیم و کاربرد

ارسال پرامپت به هوش مصنوعی برای دریافت اطلاعات در وب بسیار رایج است؛ مواردی مانند جست‌وجوی سریع اطلاعات، تولید کد و محتوا، چت‌بات‌های خدمات مشتریان، شناسایی و توصیف تصویر و رونویسی صوتی نمونه‌هایی از آن هستند.

Prompt API سازوکاری ناهمزمان (مبتنی بر {{jsxref("Promise")}}) در اختیار وب‌سایت‌ها می‌گذارد تا بتوانند به مدل هوش مصنوعی داخلیِ خودِ مرورگر پرامپت بفرستند. در اختیار داشتن مدلی روی خودِ دستگاه (on-device) مفید و کارآمد است؛ زیرا داده‌های حساس می‌توانند روی دستگاه کاربر باقی بمانند، مدل به‌صورت آفلاین در دسترس است و توسعه‌دهندگان از هزینه و تأخیر فراخوانی‌های API به سرویس‌های خارجی بی‌نیاز می‌شوند.

این API جزئیات وابسته به مدل، مانند توکن‌سازی (tokenization) و الگوسازی (templating) را در سطح خود پنهان می‌کند؛ بنابراین توسعه‌دهندگان لازم نیست این تفاوت‌ها را در پیاده‌سازی‌های مختلف مدیریت کنند.

تمام تعامل با مدل زبانی از طریق یک نشست (session) از نوع {{domxref("LanguageModel")}} انجام می‌شود. می‌توانید از این نشست برای تعیین زمینه (context) مدل استفاده کنید؛ برای مثال اسناد، اطلاعات پیش‌زمینه یا تاریخچهٔ گفت‌وگو را به مدل بدهید و سپس از آن بخواهید به پرسش‌های مشخص پاسخ دهد.

پیش از ایجاد نشست، می‌توانید متد ایستای {{domxref("LanguageModel.availability_static", "LanguageModel.availability()")}} را فراخوانی کنید تا مشخص شود آیا مدل زبانی از پیکربندی معیّنی روی دستگاه فعلی پشتیبانی می‌کند یا نه. این کار به صفحه‌ها اجازه می‌دهد اگر داده‌های پیکربندی موردنظر در دسترس نباشند یا بارگیری نشده باشند، به‌شکلی سازگار عمل کنند. برای مثال، می‌توانید اعلانی برای بارگیری نمایش دهید یا به یک سرویس هوش مصنوعی ابری بازگردید؛ به‌جای اینکه نشستی بسازید که در نهایت با شکست مواجه شود.

برای ایجاد نشست، متد ایستای {{domxref("LanguageModel.create_static", "create()")}} را فراخوانی کنید. پس از ایجاد نشست، می‌توانید {{domxref("LanguageModel.append()", "append()")}} را برای بارگذاریِ از پیشِ محتوا در نشست بدون تولید پاسخ، و {{domxref("LanguageModel.prompt()","prompt()")}} یا {{domxref("LanguageModel.promptStreaming()", "promptStreaming()")}} را برای ارسال ورودی متنی یا چندوجهی (multimodal) و دریافت پاسخ فراخوانی کنید.

می‌توانید عملیات در حال انتظار مانند `create()`، `prompt()` و `append()` را با استفاده از یک {{domxref("AbortController")}} لغو کنید.

پس از ساخته‌شدن یک نمونه (instance) از `LanguageModel`، می‌توانید با فراخوانی متد {{domxref("LanguageModel.destroy()")}} منابع اختصاص‌داده‌شده به آن را آزاد کنید و از ادامهٔ هرگونه فعالیت جلوگیری کنید. توصیه می‌شود این کار را پس از پایان کار با این شیء انجام دهید، زیرا ممکن است منابع زیادی مصرف کند.

برای شروع، راهنمای [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using) را ببینید که مفاهیم پایه را گام‌به‌گام توضیح می‌دهد.

## رابط‌ها

- {{domxref("CreateMonitor")}} {{Experimental_Inline}}
  - : اطلاعاتی درباره پیشرفت بارگیری یک مدل هوش مصنوعی فراهم می‌کند؛ برای مثال، یک بستهٔ زبانی (language pack) یا برخی داده‌های تنظیم دقیق (fine-tuning).
- {{domxref("LanguageModel")}} {{Experimental_Inline}}
  - : نشان‌دهندهٔ نشستی با مدل زبانی ارائه‌شده توسط مرورگر است. متدهای ایستایی برای ایجاد نشست و بررسی در دسترس‌بودن، و متدهای نمونه (instance) برای پرامپت‌دادن به مدل، مدیریت زمینه، همانندسازی نشست‌ها و مانند آن ارائه می‌دهد.

## هدرهای HTTP

- {{httpheader("Permissions-Policy")}}؛ دایرکتیو {{httpheader("Permissions-Policy/language-model", "language-model")}} {{Experimental_Inline}}
  - : دسترسی به قابلیت پرامپت را کنترل می‌کند.
    اگر خط‌مشی به‌طور خاص استفاده از آن را منع کند، متد ایستای {{domxref("LanguageModel.availability_static", "LanguageModel.availability()")}} مقدار `unavailable` را برمی‌گرداند و هرگونه تلاش برای فراخوانی سایر متدهای `LanguageModel` با `NotAllowedError` از نوع {{domxref("DOMException")}} ناموفق خواهد بود.

## ملاحظات امنیتی

این API به [زمینه‌های امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) (HTTPS) محدود است. علاوه بر این، ایجاد اشیاء `LanguageModel` مستلزم این است که کاربر اخیراً با صفحه تعامل کرده باشد ([فعال‌سازی گذرای کاربر](/en-US/docs/Web/Security/Defenses/User_activation) لازم است).

دسترسی به این API همچنین از طریق دایرکتیو {{httpheader("Permissions-Policy/language-model", "language-model")}} در {{httpheader("Permissions-Policy")}} کنترل می‌شود.

## مثال‌ها

برای مثال‌های کامل، راهنماهای ما را ببینید؛ از [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using) شروع کنید.

همچنین دموهای تیم Chrome DevRel را ببینید:

- [Prompt API playground](https://chrome.dev/web-ai-demos/prompt-api-playground/)
- [MediaRecorder audio transcription](https://chrome.dev/web-ai-demos/mediarecorder-audio-prompt/)
- [Canvas API image prompt](https://chrome.dev/web-ai-demos/canvas-image-prompt/)

## مشخصات

{{Specifications}}

### مواضع استانداردها

دو سازندهٔ مرورگر با این مشخصات [مخالفت کرده‌اند](/en-US/docs/Glossary/Web_standards#opposing_standards). مواضع شناخته‌شدهٔ استاندارد به این شرح است:

- Mozilla (Firefox): [نظر منفی](https://github.com/mozilla/standards-positions/issues/1213)
- Apple (WebKit): [نظر منفی](https://github.com/WebKit/standards-positions/issues/495)

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [The Prompt API](https://developer.chrome.com/docs/ai/prompt-api) در developer.chrome.com (2026)