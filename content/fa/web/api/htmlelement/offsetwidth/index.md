---
title: "HTMLElement: offsetWidth property"
short-title: offsetWidth
slug: Web/API/HTMLElement/offsetWidth
page-type: web-api-instance-property
browser-compat: api.HTMLElement.offsetWidth
---

{{ APIRef("HTML DOM") }}

خاصیت **`offsetWidth`** فقط-خواندنی از رابط {{domxref("HTMLElement")}} عرض چیدمان یک عنصر را به صورت یک عدد صحیح برمی‌گرداند.

به طور معمول، `offsetWidth` اندازه‌گیری بر حسب پیکسل از عرض CSS عنصر است، شامل هرگونه حاشیه (border)، فاصله داخلی (padding) و نوارهای اسکرول عمودی (در صورت رندر شدن). عرض شبه عناصر مانند `::before` یا `::after` را شامل نمی‌شود.

اگر عنصر پنهان باشد (برای مثال، با تنظیم `style.display` روی عنصر یا یکی از اجداد آن به `"none"`)، مقدار `0` برگردانده می‌شود.

## مقدار

یک عدد صحیح.

## مثال‌ها

![یک عنصر نمونه با padding، border و حاشیه (margin) بزرگ. `offsetWidth` عرض چیدمان عنصر شامل padding و border آن است، و حاشیه (margin) را شامل نمی‌شود.](dimensions-offset.png)

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("Element.clientWidth")}}
- {{domxref("Element.scrollWidth")}}
- {{domxref("HTMLElement.offsetHeight")}}
- {{domxref("HTMLElement.offsetLeft")}}
- {{domxref("HTMLElement.offsetTop")}}
- {{domxref("Element.getBoundingClientRect()")}}