```
---
title: "HTMLElement: offsetHeight property"
---

---
title: "HTMLElement: offsetHeight property"
short-title: offsetHeight
slug: Web/API/HTMLElement/offsetHeight
page-type: web-api-instance-property
browser-compat: api.HTMLElement.offsetHeight
---

{{ APIRef("HTML DOM") }}

ویژگی فقط‌خواندنی **`offsetHeight`** در رابط {{domxref("HTMLElement")}} ارتفاع یک عنصر را به‌صورت یک عدد صحیح، شامل padding عمودی و border ها، برمی‌گرداند.

به‌طور معمول، `offsetHeight` اندازه‌گیری ارتفاع CSS عنصر بر حسب پیکسل است، شامل هرگونه border، padding و نوار اسکرول افقی (در صورت رندر شدن). این ویژگی ارتفاع شبه‌عناصر (pseudo-elements) مانند `::before` یا `::after` را شامل نمی‌شود. برای شیء body سند، این اندازه‌گیری شامل ارتفاع کل محتوای خطی (linear content) است، نه ارتفاع CSS عنصر. عناصر شناور (floated) که پایین‌تر از سایر محتوای خطی گسترش می‌یابند نادیده گرفته می‌شوند.

اگر عنصر پنهان باشد (مثلاً با تنظیم `style.display` روی خود عنصر یا یکی از اجداد (ancestors) آن به `"none"`)، آنگاه `0` برگردانده می‌شود.

## مقدار

یک عدد صحیح.

## مثال‌ها

![یک عنصر نمونه با padding، border و margin بزرگ. `offsetHeight` ارتفاع چیدمان عنصر است که شامل padding و border آن می‌شود و margin آن را شامل نمی‌شود.](dimensions-offset.png)

تصویر مثال بالا یک نوار اسکرول و یک `offsetHeight` را نشان می‌دهد که در اندازه پنجره جای می‌گیرد. با این حال، عناصر غیرقابل‌اسکرول ممکن است مقادیر `offsetHeight` بزرگی داشته باشند، بسیار بزرگ‌تر از محتوای قابل مشاهده. این عناصر معمولاً درون عناصر قابل اسکرول قرار می‌گیرند؛ در نتیجه، بسته به تنظیم `scrollTop` ظرف قابل اسکرول، ممکن است به‌طور کامل یا جزئی نامرئی باشند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("Element.clientHeight")}}
- {{domxref("Element.scrollHeight")}}
- {{domxref("HTMLElement.offsetWidth")}}
- {{domxref("HTMLElement.offsetLeft")}}
- {{domxref("HTMLElement.offsetTop")}}
- {{domxref("Element.getBoundingClientRect()")}}
```