---
title: "ARIA: spinbutton role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: spinbutton role"
short-title: spinbutton
slug: Web/Accessibility/ARIA/Reference/Roles/spinbutton_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#spinbutton
sidebar: accessibilitysidebar
---

نقش `spinbutton` نوعی محدوده را تعریف میکند که از کاربر انتظار دارد مقداری را از میان انتخاب‌های گسسته انتخاب کند.

## توضیحات

نقش `spinbutton` نشان می‌دهد که عنصر یک ویجت ورودی است که مقدار آن را به مجموعه‌ای یا محدوده‌ای از مقادیر گسسته محدود می‌کند. این نقش همچنین دارای قابلیت افزایش و کاهش است. به عنوان مثال، در یک ویجت که به کاربران اجازه می‌دهد مقدار شرط‌بندی را در بازی Texas Holdem انتخاب کنند، نقش `spinbutton` می‌تواند به کاربران اجازه دهد عددی بین حداقل و حداکثر شرط را با افزایش‌های مجاز طبق قوانین فعلی بازی انتخاب کنند.

spinbutton محدوده مقادیر ممکن را نشان می‌دهد. مقدار ورودی spinbutton نمایانگر مقدار فعلی است.

spinbuttonها اغلب دارای سه جزء هستند: یک فیلد متنی که مقدار فعلی را نمایش می‌دهد، یک دکمه افزایش و یک دکمه کاهش. فیلد متنی معمولاً تنها جزء قابل تمرکز است، زیرا عملکردهای افزایش و کاهش از طریق کلیدهای جهت‌نما در دسترس هستند. به طور معمول، فیلد متنی همچنین به کاربران اجازه می‌دهد تا مقدار را مستقیماً ویرایش کنند.

علاوه بر شامل کردن ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) برای فعال کردن تمرکز spinbutton، پشتیبانی از صفحه‌کلید و دستگاه‌های اشاره‌گر نیز باید پیاده‌سازی شود. کلیدهای جهت‌نما مانند کلیدهای جهت‌نما باید برای کاربران صفحه‌کلید پشتیبانی شوند. تغییر مقدار هنگام کلیک بر روی دکمه‌های افزایش و کاهش باید برای دستگاه‌های اشاره‌گر پشتیبانی شود. به [تعاملات صفحه‌کلید](#keyboard_interactions) در زیر مراجعه کنید.

> [!NOTE]
> توصیه می‌شود از عنصر [`<input type="number">`](/en-US/docs/Web/HTML/Reference/Elements/input/number) یا سایر انواع ورودی برای تاریخ و زمان که به‌طور ضمنی دارای معنای `role="spinbutton"` هستند، به جای نقش `spinbutton` استفاده کنید. عامل‌های کاربر ویجت‌های سبک‌داری برای این عناصر ورودی فراهم می‌کنند که عملکرد پیش‌فرض افزایش، کاهش و محدودسازی بومی محدوده را ارائه می‌دهند. هنگام استفاده از عناصر غیر معنایی، تمام ویژگی‌های عنصر معنایی بومی باید با ویژگی‌های ARIA، جاوااسکریپت و CSS بازآفرینی شوند.

### گزینه‌های ویجت محدوده ARIA

ARIA به توسعه‌دهندگان شش نقش مختلف [ویجت محدوده](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#2._widget_roles) ارائه می‌دهد، از جمله `progressbar`، `meter`، `slider` و `spinbutton`.

نقش [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role) مشابه عنصر {{HTMLElement('progress')}} در HTML، یک محدوده فقط‌خواندنی است. این نقش نشان‌دهنده بخشی از تکمیل یک وظیفه است که در یک جهت پیشرفت می‌کند، مانند نوار پیشرفت بارگذاری یک فایل که هنگام بارگذاری کامل در نهایت به ۱۰۰٪ می‌رسد.

نقش [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role) مشابه عنصر {{HTMLElement('meter')}} در HTML، یک نشانگر فقط‌خواندنی است. این نقش مقدار چیزی را در یک محدوده شناخته‌شده نشان می‌دهد، مانند نشانگر باتری رایانه یا نشانگر سوخت خودرو.

نقش `slider` مشابه ورودی HTML از نوع `range`، [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range)، یک محدوده ورودی خواندنی-نوشتنی است. اسلایدرها به کاربران اجازه می‌دهند مقداری را بین حداقل و حداکثر از پیش تعریف‌شده انتخاب کنند. کاربر با حرکت دادن دکمه اسلایدر در امتداد یک اسلایدر افقی یا عمودی، مقداری را انتخاب می‌کند.

نقش `spinbutton` نیز خواندنی-نوشتنی است: محدوده مقادیر گسسته‌ای که فراهم می‌کند از طریق تعامل کاربر انتخاب می‌شود. مانند کنترل‌های `slider`، ویجت‌های `spinbutton` باید بتوانند تمرکز دریافت کنند و از تعامل با صفحه‌کلید، اشاره‌گر و لمسی پشتیبانی کنند.

> [!WARNING]
> برای تغییر مقدار spinbutton، فناوری‌های کمکی مبتنی بر لمس باید به حرکات کاربر برای افزایش و کاهش مقدار با شبیه‌سازی رویدادهای کلید پاسخ دهند.
> قبل از استفاده از نقش `spinbutton` (و همه ویجت‌های محدوده)، ویجت‌های spinbutton را با فناوری‌های کمکی در دستگاه‌هایی که لمس مکانیزم ورودی اصلی است، به‌طور کامل آزمایش کنید.

### ویژگی‌های مشترک

ویژگی [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) حداقل مقدار را تعیین می‌کند. اگر حذف شود یا عدد نباشد، به‌طور پیش‌فرض `0` (صفر) است.

ویژگی [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) حداکثر مقدار را تعریف می‌کند. اگر وجود نداشته باشد یا عدد نباشد، به‌طور پیش‌فرض `100` است.

مقدار ویژگی [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) باید بین حداقل و حداکثر مقادیر، هر دو به‌طور شامل، باشد. این ویژگی برای `meter` الزامی و برای `progressbar` اختیاری است.

برای `spinbutton`، مگر اینکه از عناصر HTML معنایی مانند [`<input type="number">`](/en-US/docs/Web/HTML/Reference/Elements/input/number) استفاده کنید، اگر مقدار به‌روزرسانی شود، مقدار `aria-valuenow` نیز باید به‌صورت برنامه‌نویسی به‌روزرسانی شود.

ویژگی اختیاری [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext) زمانی گنجانده می‌شود که مقدار عددی `aria-valuenow` مقدار مورد نظر spinbutton را منعکس نکند. مقادیر اختیاری حداقل، حداکثر و فعلی باید عددی باشند. وقتی مقادیری که این اعداد نشان می‌دهند عددی نیستند، ویژگی `aria-valuetext` باید با یک رشته که مقدار عددی را تعریف می‌کند گنجانده شود. به عنوان مثال، اگر از spinbutton برای اندازه‌های تیشرت استفاده کنید، ویژگی `aria-valuetext` باید با افزایش `aria-valuenow` از `XX-Small` به `XX-Large` تغییر کند.

مقدار `aria-valuetext` باید همزمان با به‌روزرسانی مقدار یا `aria-valuenow` به‌روزرسانی شود. ویژگی‌های ARIA بر روی عناصر HTML معنایی پشتیبانی می‌شوند. اگرچه هیچ ویژگی HTML معادلی برای `<input>` وجود ندارد، می‌توانید `aria-valuetext` را بر روی هر نوع {{htmlelement('input')}} قرار دهید. وقتی `aria-valuetext` یک ویژگی مهم برای spinbutton است، به جای آن از {{HTMLElement('select')}} با عناصر {{HTMLElement('option')}} استفاده کنید.

یک نام قابل دسترس **الزامی** است. اگر نقش `spinbutton` بر روی یک عنصر HTML {{HTMLElement('input')}} اعمال شود، نام قابل دسترس می‌تواند از {{HTMLElement('label')}} مرتبط بیاید. در غیر این صورت، اگر برچسب قابل مشاهده وجود دارد از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) و اگر برچسب قابل مشاهده وجود ندارد از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید.

هنگامی که از عنصر HTML {{HTMLElement('input')}} برای ایجاد spinbutton خود استفاده نمی‌کنید، ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) را برای قابل تمرکز کردن spinbutton اضافه کنید. نقش `spinbutton` تعاملی با کاربر است و بنابراین باید بتواند تمرکز دریافت کند. تمرکز باید بر روی ورودی spinbutton قرار گیرد، نه بر روی دکمه‌های مرتبطی که مقدار spinbutton را افزایش و کاهش می‌دهند.

### فرزندان محدود به دکمه‌ها یا متن

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند محتوای خاصی را شامل شوند. فرزندان یا عناصر متعلق به `spinbutton` به یک جعبه متن و دو دکمه محدود می‌شوند. همچنین می‌توان نقش `spinbutton` را بر روی یک ورودی `text` اعمال کرد و از دکمه‌های هم‌سطح برای پشتیبانی از عملکردهای افزایش و کاهش استفاده کرد.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow)
  - : روی یک مقدار اعشاری بین `aria-valuemin` و `aria-valuemax` تنظیم می‌شود که مقدار فعلی spinbutton را نشان می‌دهد. اگر وجود نداشته باشد، عنصر spinbutton مقدار فعلی ندارد.
- [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext)
  - : فناوری‌های کمکی اغلب مقدار `aria-valuenow` را به صورت عدد ارائه می‌دهند. اگر `aria-valuenow` نتواند دقیق باشد، از `aria-valuetext` برای ارائه مقدار قابل درک‌تر به spinbutton استفاده کنید.
- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin)
  - : روی یک مقدار اعشاری نمایانگر حداقل مقدار و کمتر از `aria-valuemax` تنظیم می‌شود. اگر وجود نداشته باشد، مقدار پیش‌فرضی وجود ندارد.
- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax)
  - : روی یک مقدار اعشاری نمایانگر حداکثر مقدار و بیشتر از `aria-valuemin` تنظیم می‌شود. اگر وجود نداشته باشد، مقدار پیش‌فرضی وجود ندارد.
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : مقدار رشته‌ای را تعریف می‌کند یا عنصر (یا عناصری) را که عنصر spinbutton را برچسب‌گذاری می‌کنند و نام قابل دسترس فراهم می‌کنند، شناسایی می‌کند. نام قابل دسترس الزامی است.
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : مقدار رشته‌ای را تعریف می‌کند که عنصر spinbutton را برچسب‌گذاری می‌کند. این مقدار نام قابل دسترسی را به عنصر ارائه می‌دهد زمانی که هیچ برچسب قابل مشاهده برای ارائه نام قابل دسترس مورد نیاز از طریق {{HTMLElement('label')}} یا `aria-labelledby` در دسترس نیست.

### تعاملات صفحه‌کلید

| کلید(ها) | عملیات |
| --- | --- |
| فلش‌های راست و بالا | مقدار انتخاب‌شده را یک مرحله افزایش دهید |
| فلش‌های چپ و پایین | مقدار انتخاب‌شده را یک مرحله کاهش دهید |
| Page Up | (اختیاری) مقدار را به میزان معینی بزرگ‌تر یا مساوی یک مرحله افزایش دهید |
| Page Down | (اختیاری) مقدار را به میزان معینی بزرگ‌تر یا مساوی یک مرحله کاهش دهید |
| Home | spinbutton را به حداقل مقدار تنظیم کنید |
| End | spinbutton را به حداکثر مقدار تنظیم کنید |

برای کلیدهای اختیاری <kbd>Page Up</kbd> و <kbd>Page Down</kbd>، تغییر در مقدار spinbutton ترجیحاً باید مقداری بزرگ‌تر از تغییرات گام انجام‌شده توسط فلش‌های بالا و پایین باشد.

## مثال‌ها

در مثال زیر، یک نقش `spinbutton` تعریف شده است تا به کاربران اجازه دهد روزی از ماه را انتخاب کنند.

```html
<p id="day">Enter the day of the month</p>
<button type="button" tabindex="-1" aria-label="previous day">˱</button>
<div
  role="spinbutton"
  tabindex="0"
  aria-valuenow="1"
  aria-valuetext="first"
  aria-valuemin="1"
  aria-valuemax="31"
  aria-labelledby="day">
  1
</div>
<button type="button" tabindex="-1" aria-label="next day">˲</button>
```

در این مثال، ما یک `tabindex` منفی اضافه کردیم تا دکمه‌ها را از ترتیب تب پیش‌فرض حذف کنیم. همچنین `tabindex` را به یک {{HTMLElement('div')}} که معمولاً غیرتعاملی است اضافه کردیم تا خود `spinbutton` را به ترتیب تب وارد کنیم. این مثال برای مدیریت اقدامات صفحه‌کلید زمانی که spinbutton فوکوس دارد و زمانی که کاربر ماوس روی دکمه‌ها کلیک می‌کند، به جاوااسکریپت نیاز دارد.

### با HTML معنایی

این مثال همچنین می‌توانست با HTML معنایی نوشته شود و نیاز به هرگونه CSS یا جاوااسکریپت و همچنین نیاز به گنجاندن و ارائه عملکرد برای دکمه‌های افزایش و کاهش اضافی را برطرف کند. قطعه کد زیر مثال قبلی را بدون نقش `spinbutton` و با استفاده از HTML معنایی نشان می‌دهد.

```html
<label for="day">Enter the day of the month</label>
<input
  type="number"
  value="1"
  aria-valuetext="first"
  min="1"
  max="31"
  id="day" />
```

{{EmbedLiveSample("With_semantic_HTML", 50, 50)}}

در این حالت، تنها جاوااسکریپت مورد نیاز، به‌روزرسانی `aria-valuetext` هنگام تغییر مقدار ورودی است که در این مورد واقعاً یک ویژگی اختیاری است.

## بهترین روش‌ها

`<input type="number">` در HTML به‌طور ضمنی نقش `spinbutton` را دارد. `<input type="date">` در HTML دارای ۳ دکمه چرخان تودرتو است، یکی برای هر کدام از ماه، روز و سال. هنگام استفاده از عناصر فرم HTML معنایی برای اهداف مورد نظرشان، از ویژگی‌های `aria-valuemax` یا `aria-valuemin` استفاده نکنید؛ به جای آن از `min` و `max` استفاده کنید. در غیر این صورت، هر ویژگی سراسری `aria-*` و هر ویژگی `aria-*` دیگری برای نقش `spinbutton` قابل اعمال است.

### ترجیح HTML معنایی

توصیه می‌شود از عنصر بومی {{HTMLElement("input")}} از نوع `number`، [`<input type="number">`](/en-US/docs/Web/HTML/Reference/Elements/input/number)، به جای نقش `spinbutton` استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`<input type="number">`](/en-US/docs/Web/HTML/Reference/Elements/input/number)
- [`<input type="date">`](/en-US/docs/Web/HTML/Reference/Elements/input/