---
title: "tabindex HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex"
translated_by: "n8n + AI"
---

`tabindex` یک [ویژگی سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) در HTML است که به توسعه‌دهندگان اجازه می‌دهد المان‌های HTML را قابل تمرکز (focusable) کنند، امکان تمرکز متوالی (معمولاً با کلید <kbd>Tab</kbd>، از این رو نام آن) را فعال یا غیرفعال کنند و ترتیب نسبی آن‌ها را در پیمایش متوالی با فوکوس تعیین کنند.

این ویژگی یک عدد صحیح به عنوان مقدار می‌پذیرد و نتایج متفاوتی بسته به مقدار عدد دارد:

> **نکته:** اگر یک المان HTML رندر شود و دارای ویژگی `tabindex` با هر مقدار عدد صحیح معتبر باشد، می‌توان با جاوااسکریپت (با فراخوانی متد [`focus()`](/en-US/docs/Web/API/HTMLElement/focus)) یا با کلیک ماوس آن را متمرکز کرد. مقدار `tabindex` مشخص می‌کند که آیا المان «قابل پیمایش با Tab» (tabbable) است یا نه (یعنی با پیمایش متوالی صفحه‌کلید، معمولاً با کلید <kbd>Tab</kbd> قابل دسترسی است).

- یک **مقدار منفی** (عدد دقیق不重要، معمولاً `tabindex="-1"`) به این معنی است که المان از طریق پیمایش متوالی صفحه‌کلید قابل دسترسی نیست.

  > **نکته:** `tabindex="-1"` می‌تواند برای المان‌هایی مفید باشد که مستقیماً با کلید <kbd>Tab</kbd> قابل پیمایش نیستند، اما باید بتوان فوکوس صفحه‌کلید را روی آن‌ها تنظیم کرد. مثال‌ها شامل یک پنجره مودال خارج از صفحه است که وقتی ظاهر می‌شود باید فوکوس شود، یا یک پیام خطای ارسال فرم که بلافاصله پس از ارسال ناموفق باید فوکوس شود.

- `tabindex="0"` به این معنی است که المان باید در پیمایش متوالی صفحه‌کلید، پس از همه مقادیر مثبت `tabindex`، قابل فوکوس باشد. ترتیب پیمایش فوکوس این المان‌ها با ترتیب آن‌ها در سند تعیین می‌شود.
- یک **مقدار مثبت** به این معنی است که المان باید در پیمایش متوالی صفحه‌کلید قابل فوکوس باشد، با ترتیبی که با مقدار عدد تعیین می‌شود. یعنی `tabindex="4"` قبل از `tabindex="5"` و `tabindex="0"` فوکوس می‌شود، اما بعد از `tabindex="3"`. اگر چند المان مقدار مثبت یکسانی داشته باشند، ترتیب نسبی آن‌ها با توجه به موقعیتشان در سند تعیین می‌شود. حداکثر مقدار مجاز برای `tabindex` 32767 است.
- اگر ویژگی `tabindex` بدون مقدار مشخصی استفاده شود، اینکه المان قابل فوکوس است یا نه توسط مرورگر تعیین می‌شود.

  > **هشدار:** توصیه می‌شود فقط از مقادیر `0` و `1-` برای `tabindex` استفاده کنید. از استفاده از مقادیر `tabindex` بزرگتر از `0` و ویژگی‌های CSS که می‌توانند ترتیب المان‌های قابل فوکوس HTML را تغییر دهند (مانند [ترتیب‌دهی آیتم‌های فلکس](/en-US/docs/Web/CSS/CSS_flexible_box_layout/Ordering_flex_items)) خودداری کنید. این کار برای افرادی که برای پیمایش از صفحه‌کلید یا فناوری‌های کمکی استفاده می‌کنند، پیمایش و تعامل با محتوای صفحه را دشوار می‌کند. در عوض، سند را با المان‌ها در یک توالی منطقی بنویسید.

برخی از عناصر HTML قابل‌focus، به‌طور پیش‌فرض توسط user agent (عامل کاربر) یک مقدار `tabindex` برابر با `0` دریافت می‌کنند. این عناصر عبارتند از: {{HTMLElement("a")}} یا {{HTMLElement("area")}} با attribute `href`، {{HTMLElement("button")}}، {{HTMLElement("frame")}} (منسوخ شده)، {{HTMLElement("iframe")}}، {{HTMLElement("input")}}، {{HTMLElement("object")}}، {{HTMLElement("select")}}، {{HTMLElement("textarea")}}، عنصر SVG {{SVGElement("a")}} و همچنین {{HTMLElement("summary")}} که خلاصه‌ای برای {{HTMLElement("details")}} ارائه می‌دهد. توسعه‌دهندگان نباید attribute `tabindex` را به این عناصر اضافه کنند مگر اینکه رفتار پیش‌فرض را تغییر دهند (مثلاً با مقدار منفی می‌توان عنصر را از ترتیب ناوبری focus خارج کرد).

> [!WARNING]
> attribute `tabindex` نباید در عنصر {{HTMLElement("dialog")}} استفاده شود.

## نکات دسترسی‌پذیری (Accessibility)

از استفاده از attribute `tabindex` به‌همراه محتوای غیرتعاملی ([non-interactive content](/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content)) برای قابل‌focus کردن با صفحه‌کلید عناصری که قرار است تعاملی باشند، خودداری کنید. مثلاً استفاده از {{HTMLElement("div")}} برای توصیف یک دکمه به‌جای {{HTMLElement("button")}}.

کامپوننت‌های تعاملی که با عناصر غیرتعاملی ساخته می‌شوند، در [accessibility tree](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis) قرار نمی‌گیرند. این کار باعث می‌شود فناوری‌های کمکی نتوانند به این کامپوننت‌ها دسترسی پیدا کرده و آن‌ها را کنترل کنند. بهتر است محتوا به‌صورت معنایی با عناصر تعاملی (مانند {{HTMLElement("a")}}، {{HTMLElement("button")}}، {{HTMLElement("details")}}، {{HTMLElement("input")}}، {{HTMLElement("select")}}، {{HTMLElement("textarea")}} و غیره) توصیف شود. این عناصر به‌طور پیش‌فرض نقش‌ها (roles) و حالت‌هایی (states) دارند که وضعیت را به accessibility اعلام می‌کنند؛ در غیر این صورت باید این کار را با [ARIA](/en-US/docs/Web/Accessibility/ARIA) مدیریت کنید.

- [استفاده از attribute tabindex | Vispero](https://vispero.com/resources/using-the-tabindex-attribute/)

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- تمام [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- {{domxref("HTMLElement.tabIndex")}} که این attribute را بازتاب می‌دهد
- مشکلات دسترسی‌پذیری `tabindex`: [از Tabindex بزرگ‌تر از 0 استفاده نکنید](https://adrianroselli.com/2014/11/dont-use-tabindex-greater-than-0.html) نوشتهٔ Adrian Roselli
- {{glossary("Reading order")}}