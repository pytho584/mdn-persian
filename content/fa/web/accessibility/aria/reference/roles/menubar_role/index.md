---
title: "ARIA: menubar role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: menubar role"
short-title: menubar
slug: Web/Accessibility/ARIA/Reference/Roles/menubar_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#menubar
  - https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-navigation/
sidebar: accessibilitysidebar
---

یک `menubar` نمایشی از `menu` است که معمولاً قابل مشاهده باقی می‌ماند و معمولاً به صورت افقی ارائه می‌شود.

## توضیحات

منو (menu) یک ویجت است که فهرستی از گزینه‌ها را به کاربر ارائه می‌دهد، مانند مجموعه‌ای از اقدامات یا عملکردها. نوع منوی menubar معمولاً به صورت یک نوار افقی از دستورات که به طور مداوم قابل مشاهده است ارائه می‌شود. منوبرها مانند نوارهای منوی سیستم‌عامل بومی رفتار می‌کنند، مانند نوارهای منویی که شامل منوهای کشویی هستند و معمولاً در بالای بسیاری از پنجره‌های برنامه‌های دسکتاپ یافت می‌شوند.

نقش `menubar` برای ایجاد یک نوار منو مشابه آنچه در بالای پنجره در بسیاری از برنامه‌های دسکتاپ یافت می‌شود استفاده می‌شود؛ نواری بصری و معمولاً افقی از آیتم‌های منو که به کاربر دسترسی سریع به مجموعه‌ای ثابت از دستورات را می‌دهد.

یک `menubar` شامل سه نوع آیتم منو است، از جمله [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role) و [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role). این آیتم‌های منو ممکن است به صورت اختیاری در یک یا چند ظرف [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) تودرتو قرار گیرند. گروه‌ها یا آیتم‌ها ممکن است به صورت اختیاری با عناصر [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) از هم جدا شوند. در حالی که هر آیتم منو باید بتواند فوکوس دریافت کند، حتی اگر غیرفعال باشد، عناصر `group` و `separator` فوکوس‌پذیر نیستند.

یک مثال از menubar بومی، نواری است که ممکن است در بالای صفحه وجود داشته باشد اگر در حال خواندن این مطلب در یک مرورگر دسکتاپ هستید. یک مثال از menubar مبتنی بر وب، نوار منوی افقی است که عبارت "File Edit View Insert Format" و غیره را نشان می‌دهد و معمولاً در زیر نام سند در یک سند گوگل قابل مشاهده است.

تعاملات menubar باید مشابه تعاملات معمول نوار منو در یک رابط کاربری گرافیکی دسکتاپ باشد. در Google Docs، هر یک از آن آیتم‌های منو یک `menuitem` با زیرمنوی بازشو دارند، بنابراین هر کدام دارای ویژگی `aria-haspopup` با مقدار `true` هستند. عنصر `menubar` این ویژگی را ندارد.

menubar و همه آیتم‌های منو فوکوس‌پذیر هستند و دارای ویژگی [tabindex](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) هستند. هنگامی که menubar از طریق کلید Tab فوکوس دریافت می‌کند، فوکوس صفحه‌کلید بر روی اولین آیتم منو قرار می‌گیرد. هر آیتم در منو دارای `tabindex` با مقدار `-1` است، به جز اولین آیتم که `tabindex` آن `0` است.

اگر یک menubar در نتیجه یک اقدام زمینه‌ای، مانند یک کلید میانبر، فوکوس دریافت کند، کلیدهای <kbd>Escape</kbd> یا <kbd>Enter</kbd> ممکن است فوکوس را به زمینه فراخوان بازگردانند. با این حال، مطمئن شوید که کلیدهای میانبری ایجاد نمی‌کنید که با میانبرهای عامل کاربر، سیستم‌عامل یا فناوری کمکی تداخل داشته باشند - هر UA، OS یا AT.

هر آیتم منو، صرف‌نظر از عمق تودرتو بودن، قادر به دریافت فوکوس است، حتی اگر غیرفعال باشد.

اگر یک `menubar` برچسب قابل مشاهده دارد، [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) را با مقداری که به عنصر برچسب‌گذار اشاره می‌کند قرار دهید. در غیر این صورت، با گنجاندن یک [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) توصیفی، نام قابل دسترس برای menubar فراهم کنید.

یک عنصر `menuitem` در `menubar` می‌تواند شامل یک زیرمنوی فرزند از آیتم‌های منو باشد. زیرمنوها می‌توانند چندین سطح عمق داشته باشند. به طور کلی، `menubar` بیرونی افقی است و همه زیرمنوها عمودی هستند. اگر اینطور نیست، اگر menubar شما عمودی است، [`aria-orientation="vertical"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) را روی عنصر `menubar` قرار دهید. در غیر این صورت، این ویژگی لازم نیست، زیرا مقدار پیش‌فرض افقی است.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
  - : مجموعه‌ای از آیتم‌های منو را شناسایی می‌کند.
- نقش [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)
  - : یک گزینه در مجموعه‌ای از انتخاب‌های موجود در یک `menubar`. ممکن است زیرمنو داشته باشد.
- نقش [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
  - : یک آیتم منوی قابل علامت‌گذاری در مجموعه‌ای از عناصر با نقش یکسان که فقط یکی از آن‌ها در یک زمان می‌تواند علامت‌گذاری شود.
- نقش [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
  - : یک آیتم منو با حالت قابل علامت‌گذاری که مقادیر ممکن آن `true`، `false` یا `mixed` است.
- [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation)
  - : اگر menubar عمودی است، `aria-orientation="vertical"` را روی عنصر `menubar` قرار دهید. جهت‌گیری پیش‌فرض `horizontal` است.

### تعاملات صفحه‌کلید

هنگامی که فوکوس در یک `menubar` است، همیشه روی یک آیتم منو در داخل نوار منو قرار دارد. هنگامی که فوکوس روی یک `menuitem` سطح بالا در یک نوار منو است، تعاملات صفحه‌کلید زیر باید پشتیبانی شوند:

- <kbd>پیکان رو به پایین</kbd>
  - : اگر `menuitem` دارای فوکوس، زیرمنو داشته باشد، زیرمنو را باز می‌کند و فوکوس را روی اولین آیتم در زیرمنو قرار می‌دهد.
- <kbd>پیکان رو به بالا</kbd>
  - : (اختیاری) اگر `menuitem` دارای فوکوس، زیرمنو داشته باشد، زیرمنو را باز می‌کند و فوکوس را روی _آخرین_ آیتم در زیرمنو قرار می‌دهد.
- <kbd>پیکان رو به راست</kbd>
  - : فوکوس را به آیتم بعدی منتقل می‌کند، به صورت اختیاری از آخرین به اولین می‌پیچد.
- <kbd>پیکان رو به چپ</kbd>
  - : فوکوس را به آیتم قبلی منتقل می‌کند، به صورت اختیاری از اولین به آخرین می‌پیچد.
- <kbd>Home</kbd>
  - : اگر پیچیدن کلید پیکان پشتیبانی نمی‌شود، فوکوس را به اولین آیتم در `menubar` منتقل می‌کند.
- <kbd>End</kbd>
  - : اگر پیچیدن کلید پیکان پشتیبانی نمی‌شود، فوکوس را به آخرین آیتم در `menubar` منتقل می‌کند.
- <kbd>Tab</kbd>
  - : فوکوس را به عنصر بعدی در توالی تب منتقل می‌کند. اگر این باعث خروج از menubar شود، همه زیرمنوهای موجود در menubar بسته می‌شوند.
- <kbd>shift + Tab</kbd>
  - : فوکوس را به عنصر قبلی در توالی تب منتقل می‌کند. اگر این باعث خروج از menubar شود، همه زیرمنوهای موجود در menubar بسته می‌شوند.

برای اطلاعات بیشتر در مورد تعاملات صفحه‌کلید هنگامی که فوکوس روی یک آیتم منو در یک menubar است (که همیشه چنین است)، به [`menuitem` keyboard interactions](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role#keyboard_interactions)، [`menuitemradio` keyboard interactions](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role#keyboard_interactions) و [`menuitemcheckbox` keyboard interactions](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role#keyboard_interactions) مراجعه کنید.

توجه: تعاملات بالا فرض می‌کنند `menubar` افقی است. اگر `menubar` عمودی است، `aria-orientation="vertical"` را اضافه کنید و کلیدهای صفحه‌کلید زیر را به ترتیب تغییر دهید:

- <kbd>پیکان رو به پایین</kbd>
  - : مانند <kbd>پیکان رو به راست</kbd> که در بالا توضیح داده شد عمل می‌کند.
- <kbd>پیکان رو به بالا</kbd>
  - : مانند <kbd>پیکان رو به چپ</kbd> که در بالا توضیح داده شد عمل می‌کند.
- <kbd>پیکان رو به راست</kbd>
  - : مانند <kbd>پیکان رو به پایین</kbd> که در بالا توضیح داده شد عمل می‌کند.
- <kbd>پیکان رو به چپ</kbd>
  - : مانند <kbd>پیکان رو به بالا</kbd> که در بالا توضیح داده شد عمل می‌کند.

## مثال‌ها

- [تمرین‌های W3C WAI-ARIA: مثال `menubar` ناوبری](https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-navigation/)
- [تمرین‌های W3C WAI-ARIA: مثال `menubar` ویرایشگر](https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-editor/)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `toolbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role)