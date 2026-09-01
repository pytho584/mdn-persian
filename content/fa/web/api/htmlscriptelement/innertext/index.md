---
title: "HTMLScriptElement: innerText property"
short-title: innerText
slug: Web/API/HTMLScriptElement/innerText
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.innerText
---

{{APIRef("HTML DOM")}}

> [!WARNING]
> این ویژگی محتوای متنی یک عنصر اسکریپت را نشان می‌دهد که ممکن است بسته به نوع اسکریپت قابل اجرا باشد.
> APIهایی از این دست به عنوان [injection sinks](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) (تزریق‌کننده‌ها) شناخته می‌شوند و به طور بالقوه بردار حمله برای [cross-site scripting (XSS)](/en-US/docs/Web/Security/Attacks/XSS) (اسکریپت‌نویسی بین‌سایتی) هستند.
>
> می‌توانید این خطر را با همیشه اختصاص دادن اشیاء {{domxref("TrustedScript")}} به جای رشته‌ها و [اجباری کردن trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

خاصیت **`innerText`** در رابط {{domxref("HTMLScriptElement")}} محتوای متنی عنصر {{HTMLElement("script")}} را نشان می‌دهد. این خاصیت همانند خاصیت‌های {{domxref("HTMLScriptElement.textContent","textContent")}} و {{domxref("HTMLScriptElement.text","text")}} عمل می‌کند.

## مقدار

خواندن این خاصیت یک رشته شامل متن اسکریپت برمی‌گرداند. تنظیم این خاصیت یا یک شیء {{domxref("TrustedScript")}} یا یک رشته را می‌پذیرد.

### استثناها

- `TypeError`
  - : اگر خاصیت به یک رشته تنظیم شود در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) اجباری شده باشند و هیچ خط‌مشی پیش‌فرضی تعریف نشده باشد، پرتاب می‌شود.

## توضیحات

خاصیت **`innerText`** در رابط {{domxref("HTMLScriptElement")}} محتوای متنی داخل عنصر {{HTMLElement("script")}} را نشان می‌دهد.

برای یک اسکریپت قابل اجرا (یعنی اسکریپتی که {{domxref('HTMLScriptElement/type','type')}} آن نشان می‌دهد که یک ماژول یا اسکریپت کلاسیک است)، این متن یک کد قابل اجرای درون‌خطی است. برای انواع دیگر ممکن است یک نقشه واردات (import map)، قوانین حدس و گمان (speculation rules)، یا نوع دیگری از بلوک داده را نشان دهد.

توجه داشته باشید که اگر خاصیت {{domxref('HTMLScriptElement/src','src')}} تنظیم شده باشد، محتوای خاصیت `innerText` نادیده گرفته می‌شود.

خاصیت `innerText` همچنین در {{domxref("HTMLElement.innerText","HTMLElement")}} تعریف شده است و از این رو می‌تواند با سایر عناصر استفاده شود. هنگام استفاده با سایر عناصر، این خاصیت انتظار یا اجبار اختصاص {{domxref("TrustedScript")}} را ندارد.

### ملاحظات امنیتی

برای ملاحظات امنیتی به [ملاحظات امنیتی](/en-US/docs/Web/API/HTMLScriptElement/textContent#security_considerations) در {{domxref("HTMLScriptElement.textContent")}} مراجعه کنید (ملاحظات برای خاصیت‌های `text`، `textContent` و `innerText` یکسان هستند).

## مثال‌ها

برای مثال‌ها به [مثال‌ها](/en-US/docs/Web/API/HTMLScriptElement/textContent#examples) در {{domxref("HTMLScriptElement.textContent")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.innerText")}}