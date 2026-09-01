---
title: "HTMLElement: inputMode property"
short-title: inputMode
slug: Web/API/HTMLElement/inputMode
page-type: web-api-instance-property
browser-compat: api.HTMLElement.inputMode
---

{{ APIRef("HTML DOM") }}

ویژگی **`inputMode`** در {{domxref("HTMLElement")}} مقدار ویژگی [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode) عنصر را بازتاب می‌دهد.

این ویژگی راهنمایی درباره نوع داده‌ای است که کاربر هنگام ویرایش عنصر یا محتوای آن ممکن است وارد کند. این امر به مرورگر اجازه می‌دهد صفحه‌کلید مجازی مناسبی را نمایش دهد.

این ویژگی عمدتاً روی عناصر {{HTMLElement("input")}} استفاده می‌شود، اما روی هر عنصری که در حالت [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) باشد نیز قابل استفاده است.

## مقدار

این ویژگی می‌تواند یکی از مقادیر زیر را داشته باشد:

- `decimal`
  - : صفحه‌کلید ورودی عددی کسری که شامل ارقام و جداکننده اعشار برای زبان/منطقه کاربر است (معمولاً <kbd>.</kbd> یا <kbd>,</kbd>).
- `email`
  - : صفحه‌کلید مجازی بهینه‌سازی‌شده برای وارد کردن آدرس ایمیل.
    معمولاً شامل کاراکتر <kbd>@</kbd> و همچنین بهینه‌سازی‌های دیگر است.
- `none`
  - : بدون صفحه‌کلید مجازی. زمانی استفاده می‌شود که صفحه کنترل ورودی صفحه‌کلید خود را پیاده‌سازی کند.
- `numeric`
  - : صفحه‌کلید ورودی عددی که فقط به ارقام ۰–۹ نیاز دارد.
    دستگاه‌ها ممکن است کلید منفی را نشان دهند یا ندهند.
- `search`
  - : صفحه‌کلید مجازی بهینه‌سازی‌شده برای ورودی جستجو.
    برای مثال، [کلید بازگشت/ارسال](https://html.spec.whatwg.org/multipage/interaction.html#input-modalities:-the-enterkeyhint-attribute) ممکن است با برچسب «جستجو» نمایش داده شود.
- `tel`
  - : صفحه‌کلید تلفن که شامل ارقام ۰–۹، ستاره (<kbd>\*</kbd>) و مربع (<kbd>#</kbd>) است.
- `text`
  - : صفحه‌کلید ورودی استاندارد برای زبان/منطقه فعلی کاربر.
- `url`
  - : صفحه‌کلید بهینه‌سازی‌شده برای وارد کردن آدرس‌های URL.
    برای مثال، کلید <kbd>/</kbd> ممکن است برجسته‌تر باشد.

برای جزئیات مربوط به استفاده از این ویژگی، به صفحه ویژگی HTML [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode) مراجعه کنید که این ویژگی منعکس‌کننده آن است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode)