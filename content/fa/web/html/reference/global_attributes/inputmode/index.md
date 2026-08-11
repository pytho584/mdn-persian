---
title: "inputmode HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode"
translated_by: "n8n + AI"
---

`inputmode` یک [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) از نوع enumerated است که به مرورگر提示 می‌دهد کاربر چه نوع داده‌ای را در عنصر (یا محتوایش) وارد می‌کند. این ویژگی به مرورگر کمک می‌کند صفحه‌کلید مجازی مناسبی نمایش دهد.

این attribute بیشتر روی عناصر {{HTMLElement("input")}} استفاده می‌شود، اما روی هر عنصری که در حالت `contenteditable` باشد هم قابل استفاده است.

نکته مهم: `inputmode` هیچ الزامی برای اعتبارسنجی ورودی ایجاد نمی‌کند. برای اعمال نوع داده‌ای خاص، باید از نوع `input` مناسب استفاده کنید (مثلاً `<input type="email">`). برای راهنمایی دقیق‌تر درباره انتخاب نوع {{HTMLElement("input")}} به بخش [Value](#value) مراجعه کنید.

## مقدار (Value)

این attribute می‌تواند هر یک از مقادیر زیر را بگیرد:

- `none`
  - : بدون صفحه‌کلید مجازی. زمانی استفاده می‌شود که خود صفحه کنترل ورودی صفحه‌کلید را پیاده‌سازی کرده است.
- `text` (مقدار پیش‌فرض)
  - : صفحه‌کلید استاندارد ورودی متن برای زبان کاربر.
- `decimal`
  - : صفحه‌کلید ورودی اعداد اعشاری شامل ارقام و جداکننده اعشار متناسب با locale کاربر (معمولاً <kbd>.</kbd> یا <kbd>,</kbd>). ممکن است کلید منفی (<kbd>-</kbd>) نمایش داده شود یا نشود.
- `numeric`
  - : صفحه‌کلید ورودی اعداد، فقط ارقام ۰ تا ۹. ممکن است کلید منفی داشته باشد یا نداشته باشد.
- `tel`
  - : صفحه‌کلید تلفنی شامل ارقام ۰ تا ۹، ستاره (<kbd>\*</kbd>) و مربع (<kbd>#</kbd>). برای ورودی‌هایی که _حتماً_ شماره تلفن هستند، بهتر است از `{{HTMLElement("input/tel", '&lt;input type="tel"&gt;')}}` استفاده شود.
- `search`
  - : صفحه‌کلید مجازی بهینه‌شده برای جستجو. مثلاً کلید return/submit ممکن است برچسب "Search" داشته باشد. برای ورودی‌های جستجو بهتر است از `{{HTMLElement("input/search", '&lt;input type="search"&gt;')}}` استفاده شود.
- `email`
  - : صفحه‌کلید مجازی بهینه‌شده برای ایمیل. معمولاً شامل <kbd>@</kbd> و سایر بهینه‌سازی‌ها. برای ورودی ایمیل بهتر است از `{{HTMLElement("input/email", '&lt;input type="email"&gt;')}}` استفاده شود.
- `url`
  - : صفحه‌کلید بهینه‌شده برای URL. مثلاً کلید <kbd>/</kbd> پررنگ‌تر است. ممکن است دسترسی به تاریخچه و ... داشته باشد. برای ورودی URL بهتر است از `{{HTMLElement("input/url", '&lt;input type="url"&gt;')}}` استفاده شود.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگرها (Browser compatibility)

{{Compat}}

## همچنین ببینید

- همه [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- global attribute [`enterkeyhint`](/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint)