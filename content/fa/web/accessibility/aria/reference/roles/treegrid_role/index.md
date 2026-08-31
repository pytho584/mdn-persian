---
title: "ARIA: treegrid role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: treegrid role"
short-title: treegrid
slug: Web/Accessibility/ARIA/Reference/Roles/treegrid_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#treegrid
  - https://www.w3.org/WAI/ARIA/apg/patterns/treegrid/examples/treegrid-1/
sidebar: accessibilitysidebar
---

نقش `treegrid` عنصری را به‌عنوان شبکه‌ای شناسایی می‌کند که سطرهای آن می‌توانند به همان شیوه‌ای که برای یک `tree` انجام می‌شود، باز و بسته شوند.

## توضیحات

یک `treegrid` یک شبکه داده سلسله‌مراتبی یا جدول است که از اطلاعات جدولی تشکیل شده که قابل ویرایش یا تعاملی است. یک `treegrid` ترکیبی از نقش‌های [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role) و [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) است. مانند یک `grid`، `treegrid` از سطرها، ستون‌ها و سلول‌های شبکه تشکیل شده است. مانند یک `tree`، گره‌های والد در یک `treegrid` قابل باز کردن و بسته شدن هستند.
ویجت `treegrid` شامل یک یا چند عنصر [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) است و به صورت اختیاری عناصر [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) برای گروه‌بندی سطرها دارد. هر سطر به نوبه خود شامل یک یا چند سلول است. هر سلول یا فرزند DOM یک عنصر سطر است یا توسط آن سطر مالکیت می‌شود و یکی از عناصر [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)، [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role) یا [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role) است، به طوری که نقش `gridcell` برای همه سلول‌هایی استفاده می‌شود که حاوی اطلاعات سربرگ ستون یا سطر نیستند.

یک `row` که می‌تواند باز یا بسته شود تا مجموعه‌ای از سطرهای فرزند را نشان دهد یا پنهان کند، یک **سطر والد** است. هر سطر والد دارای ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) است که روی عنصر سطر یا روی سلولی در سطر تنظیم شده است.

ویژگی `aria-expanded` زمانی که سطرهای فرزند نمایش داده می‌شوند روی `true` و زمانی که سطرهای فرزند پنهان هستند روی `false` تنظیم می‌شود. عناصری که نمایش سطرهای فرزند را کنترل نمی‌کنند نباید ویژگی `aria-expanded` را داشته باشند، زیرا وجود این ویژگی به فناوری‌های کمکی نشان می‌دهد که عنصر دارای این ویژگی یک والد است.

هنگامی که رابط کاربری شبکه شما به سطرهایی نیاز دارد که از `aria-expanded` پشتیبانی کنند یا اگر شبکه شما نیاز به پشتیبانی از [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset)، [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) یا [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level) دارد، از `treegrid` استفاده کنید نه `grid`.

هر `row` یا `gridcell` در یک سطر باید با صفحه‌کلید قابل فوکوس باشد و فوکوس صفحه‌کلید برای همه این نوادگان tree grid باید مدیریت شود. استثنای این قاعده سلول‌های سربرگ ستون هستند که اگر عملکردی مانند مرتب‌سازی یا فیلتر ارائه ندهند، نیازی به فوکوس‌پذیری ندارند. هر سطر و سلول باید یا حاوی یک عنصر قابل فوکوس باشد یا خودش قابل فوکوس باشد، صرف‌نظر از اینکه محتوای سلول به صورت جداگانه قابل ویرایش یا تعاملی است یا خیر.

### شبکه‌های درختی تک‌انتخابی و چندانتخابی

اگر `treegrid` به کاربر اجازه دهد فقط یک مورد را برای یک اقدام انتخاب کند، به عنوان **تک‌انتخابی** شناخته می‌شود. در شبکه‌های درختی تک‌انتخابی، موردی که فوکوس دارد نیز حالت انتخاب شده را با [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) دارد.

اگر treegrid از انتخاب بیش از یک سطر یا سلول پشتیبانی کند، یک **چندانتخابی** است. در شبکه‌های درختی چندانتخابی، حالت انتخاب مستقل از فوکوس است. طراحی بصری و فناوری‌های کمکی باید بین موارد انتخاب شده و موردی که فوکوس دارد تمایز قائل شوند.

برای شبکه‌های درختی چندانتخابی، [`aria-multiselectable="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable) را روی عنصری با نقش `treegrid` قرار دهید. همه سطرها یا سلول‌های انتخاب شده دارای [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) با مقدار `true` هستند. همه سطرها و سلول‌هایی که قابل انتخاب هستند اما در حال حاضر انتخاب نشده‌اند، `aria-selected` را با مقدار `false` دارند. ویژگی `aria-selected` را روی سطرها و سلول‌هایی که به صورت جداگانه قابل انتخاب نیستند قرار ندهید، زیرا وجود این ویژگی به فناوری‌های کمکی نشان می‌دهد که سطر یا سلول قابل انتخاب است.

### سطرهای یتیم

در مواردی که یک `row` یا `rowgroup` فرزند در DOM در داخل `treegrid` تودرتو نیست، ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) باید روی عنصر `treegrid` تنظیم شود و به تمام شناسه‌های فرزندان غیرنوادگی اشاره کند. اگر سطرها یا سلول‌ها از طریق `aria-owns` در یک treegrid گنجانده شوند، پس از نوادگان DOM عنصر `treegrid` به فناوری‌های کمکی ارائه می‌شوند، مگر اینکه نوادگان واقعی DOM شبکه نیز در ویژگی `aria-owns` گنجانده شوند.

### شبکه‌های درختی با محتوای بارگذاری پویا

اگر برخی سطرها یا ستون‌ها در DOM نیستند و هنگام اسکرول به صورت پویا بارگذاری می‌شوند، [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount)، [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount)، [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) و [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) مطرح می‌شوند. ویژگی‌های `aria-colcount` و `aria-rowcount` روی `treegrid` تنظیم می‌شوند. مقادیر به ترتیب تعداد کل ستون‌ها و سطرهای شبکه کاملاً بارگذاری شده هستند. شاخص‌های هر سطر و ستون روی سلول‌های جداگانه تنظیم می‌شوند، نه روی عنصر `treegrid`.

### نام قابل دسترس، توضیح و فوکوس treegrid

عنصری با نقش `treegrid` باید یک نام قابل دسترس داشته باشد. اگر برچسب مناسبی در محتوا قابل مشاهده است، نام را از طریق [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) ارائه دهید. به عبارت دیگر، اگر عنصری در رابط کاربری وجود دارد که به عنوان برچسب برای treegrid عمل می‌کند، `aria-labelledby` را به عنوان ویژگی روی عنصر با نقش `treegrid` قرار دهید و مقدار ویژگی را به `id` عنصر یا عناصر برچسب‌گذار تنظیم کنید. اگر هیچ برچسب قابل مشاهده‌ای وجود ندارد، به جای آن از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید. نه هر دو.

اگر محتوا شامل یک عنوان یا توضیح برای `treegrid` است، [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) را روی عنصر `treegrid` قرار دهید و مقدار ویژگی، `id` عنصر حاوی توضیح باشد.

اگر خود ظرف `treegrid` فوکوس دریافت کند، مقدار ویژگی [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) آن باید به [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) سطر، `columnheader`، `rowheader` یا `gridcell` انتخاب شده اشاره کند، مگر اینکه از tabindex چرخشی برای مدیریت فوکوس بین آن نقش‌ها استفاده شود، که در این صورت نباید از `aria-activedescendant` استفاده کرد.

اگر `treegrid` غیرفعال است، آن حالت غیرفعال را از نظر بصری آشکار، به صورت برنامه‌نویسی اجباری کنید و ویژگی [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) را روی خود `treegrid` قرار دهید تا فناوری‌های کمکی از وضعیت غیرفعال آن مطلع شوند.

### مرتب‌سازی treegrid

اگر treegrid عملکردهای مرتب‌سازی ارائه می‌دهد، ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) روی عناصر سلول سربرگ مربوطه قرار می‌گیرد، نه روی خود شبکه.

### منوهای treegrid

اگر `treegrid` دارای یک [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role) متصل است که با کلیک راست باز می‌شود، [`aria-haspopup="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) را روی عنصر `treegrid` قرار دهید. این به فناوری‌های کمکی اطلاع می‌دهد که `treegrid` یک پاپ‌آپ مرتبط دارد. قابلیت باز کردن و قرار دادن فوکوس در منو برای کاربران صفحه‌کلید و دستگاه‌های اشاره‌گر باید با جاوااسکریپت اضافه شود.

### treegridهای فقط‌خواندنی

به طور پیش‌فرض، treegridها قابل ویرایش فرض می‌شوند. اگر یک tree grid قابل ویرایش نیست، از ویژگی [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly) استفاده کنید تا به فناوری‌های کمکی اطلاع دهید که `treegrid` فقط‌خواندنی است. مقدار این ویژگی، وقتی روی عنصر با نقش `treegrid` تنظیم شود، به تمام عناصر `columnheader`، `rowheader` و `gridcell` سرایت می‌کند. می‌توان آن مقدار سراسری را برای عناصر `gridcell` جداگانه با قرار دادن `aria-readonly` روی نوادگان عنصر tree grid جداگانه لغو کرد.

مانند همه ویژگی‌های ARIA، افزودن `aria-readonly` فقط به فناوری‌های کمکی اطلاع می‌دهد که محتوا قابل ویرایش است یا نیست، اما هیچ کاری برای فعال یا غیرفعال کردن تعامل انجام نمی‌دهد. این کار باید با ویژگی سراسری HTML [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) یا با جاوااسکریپت انجام شود.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- نقش [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
  - : یک سطر از سلول‌ها در یک ساختار جدولی، به صورت اختیاری در یک `rowgroup`. شامل یک یا چند سطر از سلول‌های شبکه، سربرگ‌های ستون یا سربرگ‌های سطر است.
- نقش [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
  - : گروهی از [سطرها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) در یک ساختار جدولی.
- نقش [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
  - : برای تقلید از عملکرد عنصر HTML {{HTMLElement('td')}} در نظر گرفته شده است، در نقش‌های `grid` و `treegrid` یافت می‌شود و باید فرزند مستقیم یک `row` باشد.
- نقش [columnheader](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
  - : سلولی در یک سطر که حاوی اطلاعات سربرگ برای یک ستون است، مشابه عنصر بومی {{HTMLElement('th')}} با محدوده ستون.
- نقش [rowheader](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
  - : سلولی حاوی اطلاعات سربرگ برای یک `row` در یک ساختار جدولی.
- [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)
  - : برای موارد قابل باز شدن، مقدار `true` یا `false` است. همچنین نشان می‌دهد که مورد قابل باز شدن است، بنابراین اگر مورد قابل باز شدن نباشد نباید وجود داشته باشد.
- [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns)
  - : یک رابطه زمینه‌ای بین یک والد و عناصر فرزند آن را زمانی که سلسله‌مراتب DOM نمی‌تواند برای نمایش رابطه استفاده شود، شناسایی می‌کند.
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : از این ویژگی برای برچسب‌گذاری `treegrid` استفاده کنید. ویژگی `aria-labelledby` معمولاً شناسه عنصری است که برای عنوان‌گذاری treegrid استفاده می‌شود.
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : یک رشته مقدار قابل خواندن توسط انسان که `treegrid` را شناسایی می‌کند. اگر برچسب قابل مشاهده‌ای وجود دارد، باید از `aria-labelledby` استفاده شود.

### تعاملات صفحه‌کلید

برای ایجاد یک treegrid قابل دسترس، باید امکان حرکت فوکوس بین سطرها و سلول‌های شبکه با صفحه‌کلید پیاده‌سازی شود. حرکت فوکوس به داخل شبکه ممکن است منجر به فوکوس روی اولین سلول یا اولین سطر شود. اینکه فوکوس به سلول مجاور بعدی یا سطر برود به الزامات محتوای آن بستگی دارد، و برخی treegridها به سطرها فوکوس نمی‌دهند.

تعاملات صفحه‌کلید زیر باید زمانی پشتیبانی شوند که یک عنصر در شبکه فوکوس دریافت کرده است، به عنوان مثال پس از اینکه کاربر فوکوس را با Tab به شبکه منتقل کرده است.

- <kbd>Enter</kbd>
  - : اگر فوکوس فقط روی سلول فعال باشد و فوکوس روی اولین سلول با ویژگی `aria-expanded` باشد، سطرهای فرزند را باز یا بسته می‌کند. در غیر این صورت، عمل پیش‌فرض را برای سلول انجام می‌دهد.
- <kbd>Tab</kbd>
  - : اگر سطر حاوی فوکوس دارای عناصر قابل فوکوس مانند {{HTMLElement('input')}}، {{HTMLElement('button')}} یا {{HTMLElement('a')}} باشد، فوکوس را به ورودی بعدی در سطر منتقل می‌کند. اگر فوکوس روی آخرین عنصر قابل فوکوس در سطر باشد، فوکوس را از ویجت treegrid به عنصر قابل فوکوس بعدی منتقل می‌کند.
- <kbd>Right Arrow</kbd>
  - : اگر فوکوس روی یک سطر جمع‌شده باشد، سطر را باز می‌کند. اگر فوکوس روی یک سطر باز یا روی سطری باشد که سطر فرزند ندارد،