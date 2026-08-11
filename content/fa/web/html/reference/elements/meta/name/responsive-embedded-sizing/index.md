---
title: "<meta name=\"responsive-embedded-sizing\">"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name/responsive-embedded-sizing"
translated_by: "n8n + AI"
---

مقدار `responsive-embedded-sizing` برای ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/meta/name) یک عنصر {{htmlelement("meta")}} به سندی که درون یک {{htmlelement("iframe")}} تعبیه شده اجازه می‌دهد اطلاعات اندازه خود را با سند والد به اشتراک بگذارد. سپس فریم می‌تواند با استفاده از ویژگی CSS {{cssxref("frame-sizing")}} نسبت به اندازه layout سند درون‌اش، اندازه‌دهی شود.

## توضیحات

به دلایل امنیتی و حریم خصوصی، عناصر {{htmlelement("iframe")}} به طور پیش‌فرض هیچ اطلاعاتی درباره اندازه محتوای سندی که درون خود جای داده‌اند به سند والد افشا نمی‌کنند.

برای فعال‌سازی اندازه‌دهی واکنش‌گرا (responsive sizing) در {{htmlelement("iframe")}} بر اساس محتوای آن، می‌توان تگ `<meta name="responsive-embedded-sizing">` را در سند تعبیه‌شده قرار داد تا آن سند را برای به اشتراک‌گذاری اطلاعات اندازه خود با سند والد فعال کند.

سپس می‌توان ویژگی CSS {{cssxref("frame-sizing")}} را روی `<iframe>` تنظیم کرد تا آن را وادار به پذیرش اندازه افقی یا عمودی مشابه اندازه واقعی محتوای سند تعبیه‌شده (که در مشخصات «اندازه ذاتی layout داخلی» نامیده می‌شود، اما در مستندات ما به «اندازه layout» خلاصه شده) کند. این کار باعث می‌شود محتوای `<iframe>` به‌طور یکپارچه در عنصر والد جای بگیرد و از نوارهای پیمایش غیرضروری جلوگیری شود.

برای تغییر اندازه پویای `<iframe>` با تغییر اندازه layout سند تعبیه‌شده، می‌توانید متد {{domxref("Window.requestResize()")}} را از سند تعبیه‌شده فراخوانی کنید تا اندازه به‌روز شده را گزارش دهد.

## مثال‌ها

برای مثال‌های کامل، به صفحات {{cssxref("frame-sizing")}} و {{domxref("Window.requestResize()")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Window.requestResize()")}}
- ویژگی CSS {{cssxref("frame-sizing")}}
- ماژول [CSS box sizing](/en-US/docs/Web/CSS/Guides/Box_sizing)