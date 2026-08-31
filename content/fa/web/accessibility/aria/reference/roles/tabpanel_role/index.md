---
title: "ARIA: tabpanel role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: tabpanel role"
short-title: tabpanel
slug: Web/Accessibility/ARIA/Reference/Roles/tabpanel_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#tabpanel
  - https://www.w3.org/WAI/ARIA/apg/patterns/tabs/examples/tabs-manual/
sidebar: accessibilitysidebar
---

نقش `tabpanel` در ARIA یک محفظه برای منابع محتوای لایه‌ای است که با یک `tab` مرتبط است.

## توضیحات

نقش `tabpanel` نشان می‌دهد که عنصر ظرفی برای منابع مرتبط با نقش [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) است، که در آن هر `tab` در یک [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role) قرار می‌گیرد.

یک `tabpanel` بخشی از رابط tab است، یک الگوی رایج تجربه کاربری که در آن گروهی از tabهای بصری امکان جابه‌جایی سریع بین چند نمای لایه‌ای را فراهم می‌کنند. هر tab با نقش `tab` تعریف می‌شود و این tabها در عنصری با نقش `tablist` قرار می‌گیرند. `tablist` اغلب به‌صورت بصری در بالای ناحیه محتوا یا کنار آن قرار می‌گیرد و tabpanelهای مرتبط را در بر می‌گیرد. `tabpanel` نقش ظرف برای هر صفحه محتوایی است که با یک tab متناظر در `tablist` رابط tab مرتبط است.

در بسیاری از رابط‌های tab، تنها یک `tabpanel` در هر زمان قابل مشاهده است. با این حال، برخی رابط‌ها ممکن است نیاز به نمایش همزمان چند tabpanel داشته باشند. در این موارد، به `tablist` ویژگی [`aria-multiselectable`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable) داده می‌شود و عناصر `tab` از ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) استفاده می‌کنند تا مشخص کنند آیا `tabpanel` مرتبط با آن‌ها قابل مشاهده است یا خیر. حالت انتخاب‌شده tab در عوض برای مشخص کردن اینکه کدام tabpanel در حال حاضر پنل «فعال» است استفاده می‌شود. برای مثال، این می‌تواند نشان دهد که اگر شخصی هنگام تمرکز روی یک tab در `tablist` چندانتخابی، کلید <kbd>tab</kbd> را فشار دهد، کانون صفحه‌کلید به کدام tabpanel منتقل می‌شود.

در رابط‌های tab با انتخاب تکی، تنها `tabpanel` مرتبط با tab انتخاب‌شده فعلی نمایش داده می‌شود. همه عناصر `tabpanel` دیگر که با tabهای انتخاب‌نشده مرتبط هستند باید از کاربران پنهان شوند. بنابراین وقتی انتخاب tab تغییر می‌کند، tabpanel نمایش‌داده‌شده نیز تغییر می‌کند، در حالی که tabpanel نمایش‌داده‌شده قبلی پنهان می‌شود.

در رابط‌های tab با چندانتخابی، ممکن است چندین عنصر `tabpanel` مطابق با حالت بازشدگی عناصر `tab` مرتبط‌شان نمایش داده شوند.

tabها به عنوان پیوندهای لنگر به پنل‌های جداگانه عمل نمی‌کنند — و هنگام فعال‌سازی، کانون صفحه‌کلید باید روی عنصر `tab` فعلی باقی بماند و به‌طور خودکار به `tabpanel` تازه نمایش‌داده‌شده منتقل نشود. اگرچه یک رابط tab ممکن است بر اساس یک الگوی نشانه‌گذاری زیرین از ابرپیوندهای درون‌صفحه‌ای که به بخش‌های محتوای مرتبط اشاره می‌کنند، به‌صورت تدریجی تقویت شود، اما وقتی جاوااسکریپت برای تبدیل این عناصر به یک رابط tab استفاده می‌شود، رفتار پیش‌فرض ابرپیوندها باید جلوگیری شود. ایدئال این است که با حذف یا اصلاح ویژگی `href` این کار انجام شود، زیرا مزیت اضافی حذف موارد منوی مخصوص ابرپیوند از منوی زمینه مرورگر عنصر را نیز دارد.

هنگامی که کانون صفحه‌کلید روی یک `tablist` یا یک `tab` درون `tablist` است، کلید <kbd>Tab</kbd> باید طوری برنامه‌ریزی شود که از tab متمرکز‌شده — که ممکن است tab انتخاب‌شده باشد یا نباشد — به `tabpanel` که نمایانگر tab انتخاب‌شده فعلی است منتقل شود.

هر `tab` در یک `tablist` می‌تواند به عنوان برچسبی برای `tabpanel` متناظر خود عمل کند. مقدار `id` هر `tab` را به عنوان مقدار ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای هر `tabpanel` قرار دهید.

همچنین می‌توانید به‌صورت اختیاری هر `tabpanel` را با `tab` مرتبط آن با گنجاندن [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) `tabpanel` به عنوان مقدار ویژگی [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) متعلق به `tab` مرتبط کنید.

هنگامی که یک رابط tab مقداردهی اولیه می‌شود، یک `tabpanel` نمایش داده می‌شود و `tab` مرتبط با آن به‌گونه‌ای استایل می‌گیرد که نشان دهد فعال است، که این وضعیت برنامه‌ای آن را منعکس می‌کند. همه عناصر `tabpanel` غیرفعال باید از دید همه کاربران پنهان شوند. این کار معمولاً با استفاده از `display: none` در CSS انجام می‌شود.

برای اطلاعات بیشتر مختص استفاده از این نقش، مقاله [نقش `tab` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) را ببینید.

ویژگی [`tabindex="-1"`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) را اضافه کنید تا به یک `tabpanel` اجازه دریافت کانون داده شود بدون اینکه `tabpanel` در ترتیب کانون صفحه‌کلید صفحه قرار گیرد.

مطمئن شوید که برای `tabpanel` زمانی که کانون دریافت می‌کند، استایل تعریف می‌کنید، ترجیحاً با استفاده از شبه‌کلاس CSS {{CSSXref(':focus')}}، تا کاربران صفحه‌کلید بدانند که تغییر کانون رخ داده است و از محتوایی که در حال حاضر کانون دارد آگاه باشند.

چرخ فلک‌ها را می‌توان با این الگوی tab ایجاد کرد: کنترل‌کننده انتخاب اسلاید می‌تواند به‌صورت `tabs` در یک `tablist` نشانه‌گذاری شود و اسلاید با عنصر `tabpanel` نمایش داده شود.

### نقش‌ها و ویژگی‌های مرتبط

- [نقش `tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)
  - : قابلیت مشاهده `tabpanel` مرتبط را کنترل می‌کند.
- [نقش `tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)
  - : گروه عناصر `tab`.
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : یک نام دسترس‌پذیر فراهم می‌کند. به عنصر `tab` اشاره می‌کند که پنل را کنترل می‌کند.
- [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)
  - : باید روی عناصر `tab` لازم استفاده شود اگر از `tablist` چندانتخابی استفاده می‌شود.

### تعاملات صفحه‌کلید

تعاملات صفحه‌کلید [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role#keyboard_interactions) را در تعریف نقش [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role) ببینید.

## مثال

مثال [`tabpanel`، `tab`، و `tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role#example) را در تعریف نقش [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) ببینید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `tab` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)
- [نقش `tablist` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)
- [مثال: برگه‌ها با فعال‌سازی خودکار](https://www.w3.org/WAI/ARIA/apg/example-index/tabs/tabs-automatic.html) - W3C
- [مثال: برگه‌ها با فعال‌سازی دستی](https://www.w3.org/WAI/ARIA/apg/example-index/tabs/tabs-manual.html) -W3C