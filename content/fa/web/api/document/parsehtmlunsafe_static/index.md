---
title: "Document: parseHTMLUnsafe() static method"
short-title: parseHTMLUnsafe()
slug: Web/API/Document/parseHTMLUnsafe_static
page-type: web-api-static-method
browser-compat: api.Document.parseHTMLUnsafe_static
---

{{APIRef("DOM")}}

> [!WARNING]
> این متد ورودی خود را به‌عنوان HTML تجزیه و نتیجه را در DOM می‌نویسد.
> چنین APIهایی به نام [sink های تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و اگر ورودی در اصل از طرف یک مهاجم باشد، به‌طور بالقوه بردار حمله‌ای برای [اسکریپت‌های بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند.
>
> برای کاهش این ریسک، همیشه اشیاء `TrustedHTML` را به‌جای رشته‌ها عبور دهید و [مکانیزم انواع قابل اعتماد را اعمال کنید](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types).
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

> [!NOTE]
> در مرورگرهایی که از آن پشتیبانی می‌کنند، تقریباً همیشه بهتر است به‌جای این متد از {{domxref("Document/parseHTML_static", "Document.parseHTML()")}} استفاده کنید؛ زیرا این متد همیشه موجودیت‌های HTML ناامن در برابر XSS را حذف می‌کند.

متد ایستای **`parseHTMLUnsafe()`** در شیء {{domxref("Document")}} برای تجزیه ورودی HTML و به‌صورت اختیاری فیلتر کردن عناصر و ویژگی‌های ناخواسته HTML به‌کار می‌رود تا یک نمونه جدید از {{domxref("Document")}} ایجاد کند.

## Syntax

```js-nolint
Document.parseHTMLUnsafe(input)
Document.parseHTMLUnsafe(input, options)
```

### پارامترها

- `input`
  - : یک نمونه {{domxref("TrustedHTML")}} یا رشته‌ای که HTML موردنظر برای تجزیه را تعریف می‌کند.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها با پارامترهای اختیاری زیر:
    - `sanitizer` {{optional_inline}}
      - : یک شیء {{domxref("Sanitizer")}} یا {{domxref("SanitizerConfig")}} که تعیین می‌کند کدام عناصر ورودی مجاز یا حذف شوند.
        همچنین می‌تواند رشته‌ای با مقدار `"default"` باشد که یک `Sanitizer` را با [پیکربندی پیش‌فرض sanitizer (ایمن در برابر XSS)](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration) اعمال می‌کند.
        اگر مشخص نشود، هیچ sanitizer استفاده نمی‌شود.

        توجه داشته باشید اگر چندین بار از همان پیکربندی استفاده می‌کنید، انتظار می‌رود استفاده از یک `Sanitizer` و تغییر آن هنگام نیاز، کارآمدتر باشد.

### مقدار بازگشتی

یک {{domxref("Document")}}.

### استثناها

- `TypeError`
  - : در شرایط زیر پرتاب می‌شود:
    - وقتی [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP اعمال شده باشد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و سیاست پیش‌فرضی تعریف نشده باشد و `html` به‌صورت رشته‌ای عبور داده شود.
    - وقتی به `options.sanitizer` مقدار زیر داده شود:
      - یک {{domxref("SanitizerConfig")}} که [معتبر](/en-US/docs/Web/API/SanitizerConfig#valid_configuration) نیست.
        مثلاً پیکربندی که شامل هر دو تنظیم «مجاز» و «حذف‌شده» باشد.
      - رشته‌ای که مقدار آن `"default"` نباشد.
      - مقداری که نه {{domxref("Sanitizer")}} باشد، نه {{domxref("SanitizerConfig")}} و نه رشته.

## توضیحات

متد ایستای **`parseHTMLUnsafe()`** برای ایجاد یک نمونه جدید از {{domxref("Document")}} و به‌صورت اختیاری فیلتر کردن عناصر و ویژگی‌های ناخواسته استفاده می‌شود.
`Document` حاصل دارای [نوع محتوا](/en-US/docs/Web/API/Document/contentType) «text/html»، [مجموعه کاراکتر](/en-US/docs/Web/API/Document/characterSet) UTF-8 و آدرس «about:blank» خواهد بود.

ورودی HTML ممکن است شامل [ریشه‌های سایه اعلانی](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) باشد.
اگر رشته HTML بیش از یک [ریشه سایه اعلانی](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) را در یک میزبان سایه خاص تعریف کند، تنها اولین {{domxref("ShadowRoot")}} ایجاد می‌شود — اعلان‌های بعدی به‌عنوان عناصر {{htmlelement("template")}} درون آن ریشه سایه تجزیه می‌شوند.

`parseHTMLUnsafe()` به‌طور پیش‌فرض هیچ پاک‌سازی (sanitization) انجام نمی‌دهد.
اگر هیچ sanitizer به‌عنوان پارامتر عبور داده نشود، تمام موجودیت‌های HTML ورودی تزریق می‌شوند.

### ملاحظات امنیتی

پسوند «Unsafe» در نام متد نشان می‌دهد که این متد حذف تمام موجودیت‌های HTML ناامن در برابر XSS را اعمال نمی‌کند (برخلاف {{domxref("Document/parseHTML_static", "Document.parseHTML()")}}).
اگرچه در صورت استفاده با یک sanitizer مناسب می‌تواند این کار را انجام دهد، اما الزاماً از یک sanitizer مؤثر یا اصلاً از هیچ sanitizer استفاده نمی‌کند!
بنابراین این متد یک بردار احتمالی برای حملات [اسکریپت‌های بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است؛ جایی که رشته‌های بالقوه ناامن ارائه‌شده توسط کاربر بدون پاک‌سازی قبلی به DOM تزریق می‌شوند.

باید این ریسک را با همیشه عبور دادن اشیاء {{domxref("TrustedHTML")}} به‌جای رشته‌ها و [اعمال مکانیزم انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید.
این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور می‌کند که این فرصت را دارد تا ورودی را [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) کند و نشانه‌گذاری بالقوه خطرناک (مانند عناصر {{htmlelement("script")}} و ویژگی‌های کنترل‌کننده رویداد) را قبل از تزریق حذف کند.

استفاده از `TrustedHTML` این امکان را می‌دهد که اثربخشی کد پاک‌سازی را تنها در چند مکان بررسی و ممیزی کرد، نه اینکه در تمام sink های تزریق شما پراکنده باشد.
وقتی از `TrustedHTML` استفاده می‌کنید، نیازی به عبور دادن sanitizer به متد نیست.

اگر به هر دلیلی نمی‌توانید از `TrustedHTML` (یا حتی بهتر از آن، `setHTML()`) استفاده کنید، سپس امن‌ترین گزینه استفاده از `setHTMLUnsafe()` با [پیکربندی پیش‌فرض sanitizer ایمن در برابر XSS](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration) است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.parseHTML_static", "Document.parseHTML()")}}
- {{domxref("Element.setHTML()")}} و {{domxref("Element.setHTMLUnsafe()")}}
- {{domxref("ShadowRoot.setHTML()")}} و {{domxref("ShadowRoot.setHTMLUnsafe()")}}
- {{domxref("DOMParser.parseFromString()")}} برای تجزیه HTML یا XML به یک درخت DOM
- [HTML Sanitizer API](/en-US/docs/Web/API/HTML_Sanitizer_API)