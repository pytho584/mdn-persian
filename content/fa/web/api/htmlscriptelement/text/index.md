---
title: "HTMLScriptElement: text property"
short-title: text
slug: Web/API/HTMLScriptElement/text
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.text
---

{{APIRef("HTML DOM")}}

> [!WARNING]
> این ویژگی محتوای متنی یک عنصر اسکریپت را نشان می‌دهد که بسته به نوع اسکریپت ممکن است قابل اجرا باشد.
> چنین APIهایی به عنوان [سرچشمه‌های تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و به طور بالقوه بردار حمله‌ای برای [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند.
>
> می‌توانید این ریسک را با اختصاص دادن همواره اشیاء {{domxref("TrustedScript")}} به جای رشته‌ها و [اجباری کردن انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

ویژگی **`text`** در رابط {{domxref("HTMLScriptElement")}} محتوای متنی درون‌خطی عنصر {{HTMLElement("script")}} را نشان می‌دهد.
این ویژگی دقیقاً مانند ویژگی‌های {{domxref("HTMLScriptElement.textContent","textContent")}} و {{domxref("HTMLScriptElement.innerText","innerText")}} رفتار می‌کند.

## مقدار

دریافت این ویژگی یک رشته شامل متن اسکریپت را برمی‌گرداند.

تنظیم این ویژگی یا یک شیء {{domxref("TrustedScript")}} یا یک رشته را می‌پذیرد.

### استثناها

- `TypeError`
  - : زمانی پرتاب می‌شود که ویژگی با یک رشته تنظیم شود در حالی که [انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP اجباری شده‌اند](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و هیچ خط‌مشی پیش‌فرضی تعریف نشده باشد.

## توضیحات

ویژگی **`text`** در رابط {{domxref("HTMLScriptElement")}} محتوای متنی داخل عنصر {{HTMLElement("script")}} را نشان می‌دهد.

برای یک اسکریپت قابل اجرا (یعنی اسکریپتی که {{domxref('HTMLScriptElement/type','type')}} آن نشان می‌دهد که یک اسکریپت ماژول یا کلاسیک است)، این متن، کد قابل اجرای درون‌خطی است.
برای انواع دیگر، ممکن است یک نقشه واردات، قوانین حدس‌زنی، یا نوع دیگری از بلوک داده را نشان دهد.

توجه داشته باشید که اگر ویژگی {{domxref('HTMLScriptElement/src','src')}} تنظیم شده باشد، محتوای ویژگی `text` نادیده گرفته می‌شود.

### ملاحظات امنیتی

به [ملاحظات امنیتی](/en-US/docs/Web/API/HTMLScriptElement/textContent#security_considerations) در {{domxref("HTMLScriptElement.textContent")}} مراجعه کنید (ملاحظات برای ویژگی‌های `text`، `textContent` و `innerText` یکسان هستند).

## مثال‌ها

به [مثال‌ها](/en-US/docs/Web/API/HTMLScriptElement/textContent#examples) در {{domxref("HTMLScriptElement.textContent")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLScriptElement.textContent")}}
- {{domxref("HTMLScriptElement.innerText")}}