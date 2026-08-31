---
title: "ARIA: scrollbar role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: scrollbar role"
short-title: scrollbar
slug: Web/Accessibility/ARIA/Reference/Roles/scrollbar_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#scrollbar
sidebar: accessibilitysidebar
---

یک `scrollbar` یک شیء گرافیکی است که پیمایش محتوا را در یک ناحیه نمایش کنترل می‌کند.

## توضیحات

یک `scrollbar` یک محدوده است که کنترل می‌کند چه بخشی از محتوای یک نما (viewport) در حال حاضر در قاب نما قابل مشاهده است؛ چه نما به اندازه کامل مرورگر باشد، یک iframe، یا [بافت قالب‌بندی بلوکی](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) هر عنصر.

### نوار پیمایش چیست

بسیاری از برنامه‌ها زمانی که ناحیه محتوا بزرگ‌تر از پنجره برنامه است، نوارهای پیمایش بومی ارائه می‌دهند. نوارهای پیمایش معمولاً در سمت راست یا پایین ناحیه نمایش ظاهر می‌شوند. نوارهای پیمایش بومی به صورت نواحی مسیر مستطیلی باریکی به طول نمایی که کنترل می‌کنند ظاهر می‌شوند و دارای قطعه‌ای از رابط کاربری به نام دستگیره (thumb) یا اسکرولر (scroller) هستند که می‌توان آن را در امتداد یک مسیر کشید تا محتوای مرتبط درون نما حرکت کند. برخی نوارهای پیمایش در هر انتهای مسیر پیکان‌هایی دارند که با فعال شدن، امکان پیمایش نما را به یک فاصله کوتاه مشخص فراهم می‌کنند.

این سند را به عنوان مثال در نظر بگیرید: اگر نما همان پنجره کامل مرورگر باشد و محتوا بلندتر از نما باشد، در بیشتر مرورگرها نوار پیمایش در لبه راست پنجره، طول کلی صفحه را نشان می‌دهد و دستگیره پیمایش، بخشی از محتوای صفحه را نشان می‌دهد که در حال حاضر در نما قرار دارد.

نوارهای پیمایش همچنین ممکن است روی نماهایی ظاهر شوند که زیربخش‌هایی از پنجره کامل مرورگر هستند. با ادامه استفاده از این محتوا به عنوان مثال، اگر این محتوا در یک {{HTMLElement('iframe')}} یا {{HTMLElement('object')}} جاسازی شده باشد، نوار پیمایش عمودی بومی به ارتفاع قاب خواهد بود. یک نوار پیمایش معمولاً به اندازه طول نما است، اما لازم نیست چنین باشد.

اگر در حال حاضر نوار پیمایش را نمی‌بینید، ممکن است به این دلیل باشد که مرورگر شما فقط هنگام پیمایش نوار پیمایش را نشان می‌دهد یا فقط زمانی که محتوای یک عنصر بزرگ‌تر از آن است که در بافت قالب‌بندی بلوکی‌اش جا شود. بسته به مرورگر و سیستم‌عامل، ممکن است نوارهای پیمایش حتی زمانی که محتوا در نما جا می‌شود و پیمایش لازم یا حتی ممکن نیست، قابل مشاهده شوند.

### ARIA `scrollbar`

همیشه بهتر است از نوارهای پیمایش بومی استفاده کنید. می‌توانید از ویژگی CSS {{CSSXref('overflow')}} برای اطمینان از ظاهر شدن نوارهای پیمایش بومی استفاده کنید. یک [مشخصات CSS برای نوار پیمایش](https://drafts.csswg.org/css-scrollbars/) در حال توسعه است. برخی مرورگرها اجازه [استایل‌دهی به نوارهای پیمایش از طریق شبه‌عناصر دارای پیشوند](/en-US/docs/Web/CSS/Reference/Selectors/::-webkit-scrollbar) را می‌دهند.

چون استایل‌دهی به نوار پیمایش بومی از نظر تاریخی محدود بوده است، ممکن است به یک نوار پیمایش پیاده‌سازی‌شده در جاوااسکریپت برخورد کنید که باید از آن پشتیبانی کنید و آن را کاملاً قابل دسترس کنید. برای این کار می‌توانید از نقش `scrollbar` استفاده کنید تا به فناوری‌های کمکی اطلاع دهید که یک کنترل رابط کاربری، یک نوار پیمایش تعاملی است.

عنصری با نقش `scrollbar` یک شیء گرافیکی است که پیمایش محتوا را در یک ناحیه نمایش کنترل می‌کند؛ این نقش ARIA نشان می‌دهد که یک عنصر نوار پیمایش است. عنصر HTML که بیشترین شباهت را دارد، نوع `range` از {{HTMLElement('input')}}، یعنی [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range) است.

عنصر `scrollbar` دو ویژگی الزامی دارد: [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) و [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow). ویژگی `aria-controls` به [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ناحیه قابل پیمایشی که کنترل می‌کند ارجاع می‌دهد. ویژگی `aria-valuenow` مقدار فعلی نوار پیمایش را تعریف می‌کند.

در حالی که `aria-valuenow` همیشه الزامی است، ویژگی‌های [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) و [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) فقط زمانی برای نقش `scrollbar` باید تنظیم شوند که مقدار حداقل `scrollbar` برابر `0` نباشد یا مقدار حداکثر برابر `100` نباشد. مقدار `aria-valuenow` باید همیشه بین مقادیر حداقل و حداکثر (شامل آن‌ها) باشد، یا بین `0` و `100` (شامل آن‌ها) اگر مقادیر حداقل و حداکثر به ترتیب به طور پیش‌فرض `0` و `100` باشند. `aria-valuenow` نشان می‌دهد که نما چقدر به پایین سند نزدیک است. آن را مانند یک نوار پیشرفت در نظر بگیرید، جایی که شروع سند مقدار حداقل و پایان سند مقدار حداکثر است.

یک `scrollbar` مقدار فعلی و محدوده مقادیر ممکن را از طریق اندازه نوار پیمایش و موقعیت دستگیره نسبت به محدوده قابل مشاهده جهتی که کنترل می‌کند (افقی یا عمودی) نشان می‌دهد. به عبارت دیگر، طول `scrollbar` (ارتفاع یا عرض) تمام محتوای درون نما را نشان می‌دهد. مقدار `aria-valuemin` شروع محتوا و نوار پیمایش را نشان می‌دهد، مقدار `aria-valuemax` پایان محتوا و پایان نوار پیمایش را نشان می‌دهد. مقدار `aria-valuenow` محتوایی را که در حال حاضر در نما قابل مشاهده است و موقعیت یا مقدار فعلی دستگیره متحرک را نشان می‌دهد. مقدار `aria-valuenow` معمولاً به عنوان درصدی بین `aria-valuemin` و `aria-valuemax` توسط فناوری‌های کمکی محاسبه و ارائه می‌شود.

> [!NOTE]
> فناوری‌های کمکی معمولاً مقدار `aria-valuenow` را به صورت درصدی از محدوده بین مقدار `aria-valuemin` و `aria-valuemax` ارائه می‌دهند، مگر اینکه [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext) تنظیم شده باشد. توصیه می‌شود مقادیر `aria-valuemin`، `aria-valuemax` و `aria-valuenow` را به گونه‌ای تنظیم کنید که برای این محاسبه مناسب باشد.

مانند یک نوار پیمایش بومی، کاربران با عناصر `scrollbar` به طور مستقیم یا غیرمستقیم با استفاده از ماوس، تاچ‌پد، صفحه‌کلید و ورودی صوتی تعامل می‌کنند. پیاده‌سازی‌های نقش `scrollbar` نیز باید همه این روش‌های تعامل را پشتیبانی کنند.

هنگام استفاده از ماوس، کاربر باید بتواند `scrollbar` را با کلیک بر روی پیکان‌های پیمایش در هر انتهای نوار پیمایش، در صورت وجود، کلیک بر روی بخش خالی مسیر پیمایش، و همچنین کلیک و کشیدن دستگیره پیمایش فعال کند.

پیمایش با صفحه‌کلید نیز باید پشتیبانی شود. وقتی فوکوس در نمای کنترل‌شده توسط یک `scrollbar` قرار دارد، کلیدهای <kbd>Up Arrow</kbd> و <kbd>Down Arrow</kbd> (یا <kbd>Left Arrow</kbd> و <kbd>Right Arrow</kbd> برای نوار پیمایش افقی) باید دستگیره نوار پیمایش را به طور متناسب حرکت دهند. علاوه بر این، کلیدهای <kbd>Page Up</kbd>، <kbd>Page Down</kbd>، <kbd>Space</kbd> و <kbd>Shift + Space</kbd> باید با هر بار فشار دادن، محتوا و دستگیره پیمایش را به اندازه ارتفاع (یا عرض) نما حرکت دهند تا پایین یا بالای محتوا (یا چپ یا راست آن) در نما دیده شود.

جاوااسکریپت باید برای تبدیل کنش `scrollbar` به دستورات پیمایش استفاده شود و با موارد زیر به کاربر بازخورد دهد:

1. به‌روزرسانی بصری عنصر `scrollbar`،
2. پیمایش محتوای نما، و
3. به‌روزرسانی مقدار ویژگی [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow).

جهت پیش‌فرض نقش `scrollbar` عمودی است. در این حالت، گنجاندن [`aria-orientation="vertical"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) اختیاری است. جهت، جهت‌گیری نوار پیمایش و اثر پیمایش بر روی ناحیه نمایش کنترل‌شده توسط نوار پیمایش را نشان می‌دهد. اگر پیمایش از چپ به راست یا راست به چپ باشد و نه از بالا به پایین، `aria-orientation="horizontal"` را روی عنصر دارای نقش `scrollbar` قرار دهید.

> [!NOTE]
> یک نام قابل دسترس **الزامی** است. اگر نقش `scrollbar` روی یک عنصر HTML {{HTMLElement('input')}} (یا عنصر `<meter>` یا `<progress>`) اعمال شود، نام قابل دسترس می‌تواند از {{HTMLElement('label')}} مرتبط بیاید. در غیر این صورت، اگر برچسب قابل مشاهده موجود است از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) استفاده کنید، یا اگر برچسب قابل مشاهده وجود ندارد از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید.

### همه عناصر فرزند نمایشی هستند

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در یک API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند متن داشته باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود درون یک `scrollbar` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `scrollbar` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

به عنوان مثال، عنصر `scrollbar` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="scrollbar"><h3>Title of my scrollbar</h3></div>
```

چون فرزندان `scrollbar` نمایشی هستند، کد زیر معادل است:

```html
<div role="scrollbar"><h3 role="presentation">Title of my scrollbar</h3></div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه‌کدهای قبلی با موارد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="scrollbar">Title of my scrollbar</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) (الزامی)
  - : نمای (viewport) را از طریق `id` شناسایی می‌کند که محتوای آن توسط نوار پیمایش کنترل می‌شود.
- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) (الزامی)
  - : روی یک مقدار اعشاری بین `0`، یا `aria-valuemin` در صورت وجود، و `aria-valuemax` تنظیم شده و مقدار فعلی نوار پیمایش را نشان می‌دهد.
- [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext)
  - : فناوری‌های کمکی اغلب مقدار `aria-valuenow` را به صورت درصد ارائه می‌دهند. اگر این مفید نباشد، از این ویژگی استفاده کنید تا مقدار نوار پیمایش برای کاربران قابل‌فهم‌تر شود.
- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin)
  - : روی یک مقدار اعشاری تنظیم می‌شود که نشان‌دهنده مقدار حداقل است و کمتر از `aria-valuemax` است. اگر وجود نداشته باشد، مقدار پیش‌فرض `0` است.
- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax)
  - : روی یک مقدار اعشاری تنظیم می‌شود که نشان‌دهنده مقدار حداکثر است و بیشتر از `aria-valuemin` است. اگر وجود نداشته باشد، مقدار پیش‌فرض `100` است.
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : وقتی از کنترل فرم بومی استفاده نمی‌کنید و بنابراین نمی‌توانید نوار پیمایش را با یک {{HTMLElement('label')}} مرتبط کنید، اگر متن قابل مشاهده موجود باشد که بتواند نام قابل دسترس مورد نیاز را فراهم کند، آن را روی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) عنصری تنظیم کنید که حاوی متنی است که به عنوان برچسب عمل می‌کند. در غیر این صورت از `aria-label` استفاده کنید.
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : اگر هیچ {{htmlelement('label')}} قابل استفاده نباشد و هیچ متن قابل مشاهده‌ای وجود نداشته باشد که بتوان توسط `aria-labelledby` به آن ارجاع داد، مقدار رشته‌ای را فراهم می‌کند که عنصر `scrollbar` را برچسب‌گذاری می‌کند و نام قابل دسترس مورد نیاز را ارائه می‌دهد.
- [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation)
  - : به طور پیش‌فرض، جهت `vertical` است. ویژگی را می‌توان شامل کرد و روی `horizontal`، `undefined` (پیش‌فرض برای همه نقش‌ها مگر اینکه طور دیگری مشخص شود) یا `vertical` تنظیم کرد.

### تعاملات صفحه‌کلید

- <kbd>Up Arrow</kbd>
  - : محتوای نما به اندازه یک خط به بالا حرکت می‌کند و دستگیره به طور متناسب در امتداد لغزنده نوار پیمایش به بالا حرکت می‌کند، تا زمانی که به بالای محتوا و نوار پیمایش برسد.
- <kbd>Down Arrow</kbd>
  - : محتوای نما به اندازه یک خط به پایین حرکت می‌کند و دستگیره به طور متناسب در امتداد لغزنده نوار پیمایش به پایین حرکت می‌کند، تا زمانی که به پایین محتوا و نوار پیمایش برسد.
- <kbd>Left