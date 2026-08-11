---
title: "<input> HTML input element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input"
translated_by: "n8n + AI"
---

عنصر `<input>` در HTML برای ایجاد کنترل‌های تعاملی در فرم‌های تحت وب استفاده می‌شود تا داده‌ها را از کاربر دریافت کند. بسته به دستگاه و user agent، انواع مختلفی از داده‌های ورودی و ویجت‌های کنترلی در دسترس است. عنصر `<input>` به دلیل تنوع بالای نوع‌های ورودی (type) و attributeها، یکی از قدرتمندترین و پیچیده‌ترین عناصر HTML به شمار می‌رود.

```html interactive-example
<label for="name">Name (4 to 8 characters):</label>

<input
  type="text"
  id="name"
  name="name"
  required
  minlength="4"
  maxlength="8"
  size="10" />
```

```css interactive-example
label {
  display: block;
  font:
    1rem "Fira Sans",
    sans-serif;
}

input,
label {
  margin: 0.4rem 0;
}
```

## نوع‌های `<input>`

نحوهٔ کار `<input>` به‌شدت به مقدار [`type`](#type) آن بستگی دارد. به همین دلیل، هر نوع در صفحهٔ مرجع جداگانه‌ای پوشش داده شده است. اگر این attribute مشخص نشود، نوع پیش‌فرض `text` در نظر گرفته می‌شود.

انواع موجود عبارتند از:

| نوع | توضیحات | مثال‌های پایه |
|------|----------|----------------|
| `button` | یک دکمه فشاری بدون رفتار پیش‌فرض که مقدار attribute `value` را نمایش می‌دهد (به طور پیش‌فرض خالی). | ```html<br><input type="button" name="button" value="Button" /><br>``` |
| `checkbox` | یک چک‌باکس که امکان انتخاب/لغو انتخاب یک مقدار واحد را فراهم می‌کند. | ```html<br><input type="checkbox" name="checkbox"/><br>``` |
| `color` | کنترلی برای انتخاب رنگ؛ در مرورگرهای پشتیبان یک color picker باز می‌کند. | ```html<br><input type="color" name="color"/><br>``` |
| `date` | کنترلی برای وارد کردن تاریخ (سال، ماه، روز بدون زمان). در مرورگرهای پشتیبان یک date picker یا چرخ‌های عددی برای سال، ماه، روز باز می‌کند. | ```html<br><input type="date" name="date"/><br>``` |
| `datetime-local` | کنترلی برای وارد کردن تاریخ و زمان (بدون منطقه زمانی). در مرورگرهای پشتیبان یک date picker یا چرخ‌های عددی برای اجزای تاریخ و زمان باز می‌کند. | ```html<br><input type="datetime-local" name="datetime-local"/><br>``` |
| `email` | فیلدی برای ویرایش یک آدرس ایمیل. شبیه `text` است اما در مرورگرهای پشتیبان و دستگاه‌های دارای صفحه‌کلید پویا، دارای پارامترهای اعتبارسنجی و صفحه‌کلید مناسب است. | ```html<br><input type="email" name="email"/><br>``` |
| `file` | کنترلی که به کاربر اجازه انتخاب یک فایل را می‌دهد. از attribute `accept` برای تعیین انواع فایل‌های قابل انتخاب استفاده کنید. | ```html<br><input type="file" accept="image/*, text/*" name="file"/><br>``` |
| `hidden` | کنترلی که نمایش داده نمی‌شود اما مقدار آن به سرور ارسال می‌شود. در ستون بعدی یک مثال وجود دارد، اما مخفی است! | ```html<br><input id="userId" name="userId" type="hidden" value="abc123" /><br>``` |
| `image` | یک دکمه submit گرافیکی. تصویری را که توسط attribute `src` تعریف شده نمایش می‌دهد. اگر `src` موجود نباشد، attribute `alt` نمایش داده می‌شود. | ```html<br><input type="image" name="image" src="" alt="image input"/><br>``` |
| `month` | کنترلی برای وارد کردن ماه و سال (بدون منطقه زمانی). | ```html<br><input type="month" name="month"/><br>``` |
| `number` | کنترلی برای وارد کردن عدد. یک spinner نمایش می‌دهد و اعتبارسنجی پیش‌فرض اضافه می‌کند. در برخی دستگاه‌های دارای صفحه‌کلید پویا، یک صفحه‌کلید عددی نمایش می‌دهد. | ```html<br><input type="number" name="number"/><br>``` |
| `password` | یک فیلد متنی تک‌خطی که مقدار آن مخفی می‌شود. اگر سایت امن نباشد به کاربر هشدار می‌دهد. | ```html<br><input type="password" name="password"/><br>``` |
| `radio` | یک دکمه رادیویی که امکان انتخاب یک مقدار واحد از بین چند گزینه با attribute `name` یکسان را فراهم می‌کند. | ```html<br><input type="radio" name="radio"/><br>``` |
| `range` | کنترلی برای وارد کردن عددی که مقدار دقیق آن مهم نیست. به صورت یک نوار لغزنده نمایش داده می‌شود و به طور پیش‌فرض در وسط قرار دارد. همراه با `min` و `max` برای محدوده مقادیر قابل قبول استفاده می‌شود. | ```html<br><input type="range" name="range" min="0" max="25"/><br>``` |
| `reset` | دکمه‌ای که محتویات فرم را به مقادیر پیش‌فرض بازمی‌گرداند. توصیه نمی‌شود. | ```html<br><input type="reset" name="reset"/><br>``` |
| `search` | یک فیلد متنی تک‌خطی برای وارد کردن عبارات جستجو. خط‌شکست‌ها به طور خودکار از مقدار حذف می‌شوند. ممکن است در مرورگرهای پشتیبان یک آیکون حذف داشته باشد. در برخی دستگاه‌های دارای صفحه‌کلید پویا، به جای کلید enter یک آیکون جستجو نمایش می‌دهد. | ```html<br><input type="search" name="search"/><br>``` |
| `submit` | دکمه‌ای که فرم را ارسال می‌کند. | ```html<br><input type="submit" name="submit"/><br>``` |
| `tel` | کنترلی برای وارد کردن شماره تلفن. در برخی دستگاه‌های دارای صفحه‌کلید پویا، یک صفحه‌کلید تلفن نمایش می‌دهد. | ```html<br><input type="tel" name="tel"/><br>``` |
| `text` | مقدار پیش‌فرض. یک فیلد متنی تک‌خطی. خط‌شکست‌ها به طور خودکار از مقدار حذف می‌شوند. | ```html<br><input type="text" name="text"/><br>``` |
| `time` | کنترلی برای وارد کردن مقدار زمان (بدون منطقه زمانی). | ```html<br><input type="time" name="time"/><br>``` |
| `url` | فیلدی برای وارد کردن یک URL. شبیه `text` است اما در مرورگرهای پشتیبان و دستگاه‌های دارای صفحه‌کلید پویا، دارای پارامترهای اعتبارسنجی و صفحه‌کلید مناسب است. | ```html<br><input type="url" name="url"/><br>``` |
| `week` | کنترلی برای وارد کردن یک تاریخ که شامل شماره سال-هفته و شماره هفته است (بدون منطقه زمانی). | ```html<br><input type="week" name="week"/><br>``` |
| **مقادیر منسوخ** | | |
| `datetime` {{deprecated_inline}} | کنترلی برای وارد کردن تاریخ و زمان (ساعت، دقیقه، ثانیه و کسری از ثانیه) بر اساس منطقه زمانی UTC. | ```html<br><input type="datetime" name="datetime"/><br>``` |

## Attributeها

element `<input>` به دلیل attributeهایش بسیار قدرتمند است؛ attribute [`type`](#type) که در بالا با مثال‌هایی توضیح داده شد، مهم‌ترین آن‌هاست. از آنجا که هر element `<input>`، صرف‌نظر از type، بر اساس interface وابسته به `HTMLInputElement` ساخته می‌شود، از نظر فنی دقیقاً مجموعه یکسانی از attributeها را به اشتراک می‌گذارند. با این حال، در واقعیت، بیشتر attributeها فقط روی زیرمجموعه خاصی از typeهای input اثر می‌گذارند. علاوه بر این، نحوه تأثیر برخی attributeها روی یک input به type آن input بستگی دارد و تأثیرات متفاوتی روی typeهای مختلف می‌گذارد.

این بخش جدولی را ارائه می‌دهد که همه attributeها را به همراه توضیح کوتاه فهرست می‌کند. بعد از آن جدول، لیستی می‌آید که هر attribute را با جزئیات بیشتری توضیح می‌دهد و مشخص می‌کند با کدام input typeها مرتبط است. attributeهایی که برای بیشتر یا همه input typeها مشترک هستند، در ادامه با جزئیات بیشتر تعریف شده‌اند. attributeهایی که منحصر به input typeهای خاصی هستند — یا attributeهایی که برای همه input typeها مشترک‌اند اما روی یک input type خاص رفتار ویژه‌ای دارند — در صفحه‌های مربوط به آن typeها مستند شده‌اند.

attributeهای element `<input>` شامل [global HTML attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) و موارد زیر هستند:

| Attribute                                     | Type(s)                                                                 | توضیحات                                                                                              |
| --------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| [`accept`](#accept)                           | `file`                                                                  | نوع فایل مورد انتظار در کنترل‌های بارگذاری فایل                                                       |
| [`alpha`](#alpha)                             | `color`                                                                 | شفافیت رنگ                                                                                           |
| [`alt`](#alt)                                 | `image`                                                                 | ویژگی `alt` برای نوع تصویر. برای دسترسی‌پذیری الزامی است                                               |
| [`autocapitalize`](#autocapitalize)           | همه به جز `url`, `email` و `password`                                  | کنترل خودکار بزرگ‌نویسی در متن ورودی                                                                  |
| [`autocomplete`](#autocomplete)               | همه به جز `checkbox`, `radio` و دکمه‌ها                               | راهنمایی برای قابلیت تکمیل خودکار فرم                                                                 |
| [`capture`](#capture)                         | `file`                                                                  | روش ورودی ضبط رسانه در کنترل‌های بارگذاری فایل                                                       |
| [`checked`](#checked)                         | `checkbox`, `radio`                                                     | آیا کنترل یا دستور انتخاب شده است                                                                     |
| [`colorspace`](#colorspace)                   | `color`                                                                 | [فضای رنگی] که برای انتخاب مقدار رنگ استفاده شود                                                      |
| [`dirname`](#dirname)                         | `hidden`, `text`, `search`, `url`, `tel`, `email`                       | نام فیلد فرم برای ارسال جهت‌گیری عنصر در هنگام ارسال فرم                                              |
| [`disabled`](#disabled)                       | همه                                                                     | آیا کنترل فرم غیرفعال است                                                                             |
| [`form`](#form)                               | همه                                                                     | کنترل را به یک عنصر فرم متصل می‌کند                                                                   |
| [`formaction`](#formaction)                   | `image`, `submit`                                                       | آدرس URL برای ارسال فرم                                                                               |
| [`formenctype`](#formenctype)                 | `image`, `submit`                                                       | نوع رمزگذاری مجموعه داده فرم برای ارسال فرم                                                           |
| [`formmethod`](#formmethod)                   | `image`, `submit`                                                       | روش HTTP برای ارسال فرم                                                                               |
| [`formnovalidate`](#formnovalidate)           | `image`, `submit`                                                       | دور زدن اعتبارسنجی کنترل فرم در هنگام ارسال فرم                                                       |
| [`formtarget`](#formtarget)                   | `image`, `submit`                                                       | زمینه‌ی مرورگر برای ارسال فرم                                                                         |
| [`height`](#height)                           | `image`                                                                 | مشابه ویژگی `height` در {{htmlelement('img')}}؛ بعد عمودی                                             |
| [`list`](#list)                               | همه به جز `hidden`, `password`, `checkbox`, `radio` و دکمه‌ها       | مقدار ویژگی `id` از {{htmlelement('datalist')}} برای گزینه‌های تکمیل خودکار                           |
| [`max`](#max)                                 | `date`, `month`, `week`, `time`, `datetime-local`, `number`, `range`    | حداکثر مقدار                                                                                         |
| [`maxlength`](#maxlength)                     | `text`, `search`, `url`, `tel`, `email`, `password`                     | حداکثر طول (تعداد کاراکترها) `value`                                                                  |
| [`min`](#min)                                 | `date`, `month`, `week`, `time`, `datetime-local`, `number`, `range`    | حداقل مقدار                                                                                          |
| [`minlength`](#minlength)                     | `text`, `search`, `url`, `tel`, `email`, `password`                     | حداقل طول (تعداد کاراکترها) `value`                                                                   |
| [`multiple`](#multiple)                       | `email`, `file`                                                         | بولی. آیا اجازه چند مقدار داده می‌شود                                                                 |
| [`name`](#name)                               | همه                                                                     | نام کنترل فرم. همراه با فرم به عنوان بخشی از یک جفت نام/مقدار ارسال می‌شود                           |
| [`pattern`](#pattern)                         | `text`, `search`, `url`, `tel`, `email`, `password`                     | الگویی که `value` باید با آن مطابقت داشته باشد تا معتبر باشد                                           |
| [`placeholder`](#placeholder)                 | `text`, `search`, `url`, `tel`, `email`, `password`, `number`           | متنی که در کنترل فرم زمانی که مقداری تنظیم نشده نمایش داده می‌شود                                      |
| [`popovertarget`](#popovertarget)             | `button`                                                                | یک `<input type="button">` را به عنوان کنترل برای یک عنصر popover تعیین می‌کند                       |
| [`popovertargetaction`](#popovertargetaction) | `button`                                                                | عملی که کنترل popover باید انجام دهد را مشخص می‌کند                                                   |
| [`readonly`](#readonly)                       | همه به جز `hidden`, `range`, `color`, `checkbox`, `radio` و دکمه‌ها   | بولی. مقدار قابل ویرایش نیست                                                                          |
| [`required`](#required)                       | همه به جز `hidden`, `range`, `color` و دکمه‌ها                        | بولی. مقدار الزامی است یا باید انتخاب شود تا فرم قابل ارسال باشد                                      |
| [`size`](#size)                               | `text`, `search`, `url`, `tel`, `email`, `password`                     | اندازه کنترل                                                                                        |
| [`src`](#src)                                 | `image`                                                                 | مشابه ویژگی `src` در {{htmlelement('img')}}؛ آدرس منبع تصویر                                          |
| [`step`](#step)                               | `date`, `month`, `week`, `time`, `datetime-local`, `number`, `range`    | مقادیر افزایشی معتبر                                                                                 |
| [`switch`](#switch)                           | `checkbox`                                                              | آیا ورودی چک‌باکس باید به صورت یک سوئیچ نمایش داده شود                                                |
| [`type`](#type)                               | همه                                                                     | نوع کنترل فرم                                                                                        |
| [`value`](#value)                             | همه به جز `image`                                                       | مقدار کنترل. وقتی در HTML مشخص شود، معادل مقدار اولیه است                                            |
| [`width`](#width)                             | `image`                                                                 | مشابه ویژگی `width` در {{htmlelement('img')}}                                                        |

چند attribute غیراستاندارد اضافی نیز در ادامه، پس از توضیحات attributeهای استاندارد فهرست شده‌اند.

### Individual attributes

- [`accept`](/en-US/docs/Web/HTML/Reference/Attributes/accept)
  - : فقط برای input نوع `file` معتبر است. attribute «accept» مشخص می‌کند که در کنترل آپلود فایل، چه نوع فایل‌هایی قابل انتخاب هستند. به input نوع `file` مراجعه کنید.

- `alpha` (experimental)
  - : فقط برای input نوع `color` معتبر است. این attribute به کاربر اجازه می‌دهد شفافیت (opacity) رنگ انتخابی را تنظیم کند.

- `alt`
  - : فقط برای دکمه `image` معتبر است. attribute «alt» متن جایگزین برای تصویر فراهم می‌کند؛ اگر [`src`](#src) تصویر وجود نداشته باشد یا به هر دلیل بارگذاری نشود، مقدار این attribute نمایش داده می‌شود. به input نوع `image` مراجعه کنید.

- `autocapitalize`
  - : کنترل می‌کند که آیا متن واردشده به صورت خودکار با حرف بزرگ شروع شود و اگر بله، به چه شکل. برای اطلاعات بیشتر به صفحه attribute سراسری [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize) مراجعه کنید.

- [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
  - : **(این یک Boolean attribute نیست!)** attribute [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) یک رشته با مقادیر جدا شده با فاصله دریافت می‌کند که مشخص می‌کند input چه نوع قابلیت autocomplete (در صورت وجود) باید داشته باشد. یک پیاده‌سازی معمول autocomplete مقادیر قبلی واردشده در همان فیلد input را به خاطر می‌آورد، اما اشکال پیچیده‌تری از autocomplete نیز می‌توانند وجود داشته باشند. برای مثال، یک browser می‌تواند با فهرست مخاطبین دستگاه یکپارچه شود تا آدرس‌های `email` را در یک فیلد input ایمیل به صورت خودکار تکمیل کند. برای مقادیر مجاز به [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete#value) مراجعه کنید.

    attribute `autocomplete` روی `hidden`, `text`, `search`, `url`, `tel`, `email`, `date`, `month`, `week`, `time`, `datetime-local`, `number`, `range`, `color` و `password` معتبر است. این attribute روی inputهایی که داده‌های عددی یا متنی برنمی‌گردانند هیچ اثری ندارد. برای همه input typeها به جز `checkbox`, `radio`, `file` و هر نوع دکمه‌ای معتبر است.

    برای اطلاعات بیشتر، از جمله امنیت رمز عبور و اینکه چطور `autocomplete` برای `hidden` کمی با سایر input typeها تفاوت دارد، به [attribute `autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) مراجعه کنید.

- `autofocus`
  - : یک Boolean attribute است که اگر وجود داشته باشد، نشان می‌دهد input باید به محض بارگذاری کامل صفحه (یا وقتی dialog ای که عنصر در آن قرار دارد نمایش داده شود) به صورت خودکار فوکوس بگیرد.

    > **نکته:**
    > یک عنصر با attribute «autofocus» ممکن است قبل از اینکه رویداد `DOMContentLoaded` رخ دهد فوکوس بگیرد.

    حداکثر یک عنصر در سند می‌تواند attribute «autofocus» داشته باشد. اگر روی بیش از یک عنصر قرار گیرد، اولین عنصری که این attribute را دارد فوکوس می‌گیرد.

    attribute «autofocus» را نمی‌توان روی input های نوع `hidden` استفاده کرد، زیرا input های مخفی قابل فوکوس نیستند.

    > **هشدار:**
    > فوکوس خودکار یک کنترل فرم می‌تواند کاربران کم‌بینا که از فناوری صفحه‌خوان (screen reader) استفاده می‌کنند و افراد دارای اختلالات شناختی را گیج کند. وقتی `autofocus` تنظیم می‌شود، صفحه‌خوان کاربر را بدون هشدار قبلی به کنترل فرم «منتقل» می‌کند.

    هنگام اعمال attribute «autofocus» ملاحظات دسترس‌پذیری (accessibility) را به دقت در نظر بگیرید. فوکوس خودکار روی یک کنترل می‌تواند باعث اسکرول صفحه هنگام بارگذاری شود. فوکوس همچنین می‌تواند باعث نمایش صفحه‌کلید پویا در برخی دستگاه‌های لمسی شود. اگرچه صفحه‌خوان برچسب کنترل فرم را که فوکوس می‌گیرد اعلام می‌کند، اما قبل از برچسب چیزی را اعلام نمی‌کند؛ کاربر بینا در یک دستگاه کوچک نیز به همین ترتیب زمینه‌ای را که توسط محتوای قبلی ایجاد شده از دست می‌دهد.

- [`capture`](/en-US/docs/Web/HTML/Reference/Attributes/capture)
  - : این attribute در مشخصات HTML Media Capture معرفی شده و فقط برای input با نوع `file` معتبر است. `capture` مشخص می‌کند که برای گرفتن یک فایل جدید جهت آپلود با کنترل آپلود `file` در سناریوهای پشتیبانی‌شده، از کدام رسانه استفاده شود: میکروفون، ویدیو یا دوربین. به input type مربوط به `file` مراجعه کنید.

- `checked`
  - : برای هر دو نوع `radio` و `checkbox` معتبر است. `checked` یک attribute بولی است. اگر روی نوع `radio` وجود داشته باشد، نشان می‌دهد که این دکمه رادیویی در گروه دکمه‌های رادیویی هم‌نام، در حال حاضر انتخاب‌شده است. اگر روی نوع `checkbox` وجود داشته باشد، نشان می‌دهد که چک‌باکس به‌طور پیش‌فرض (هنگام بارگذاری صفحه) علامت‌خورده است. این attribute نشان نمی‌دهد که آیا چک‌باکس در حال حاضر علامت خورده است یا نه؛ اگر وضعیت چک‌باکس تغییر کند، این content attribute تغییر را منعکس نمی‌کند. (فقط [`HTMLInputElement`'s `checked` IDL attribute](/en-US/docs/Web/API/HTMLInputElement) به‌روزرسانی می‌شود.)

    > [!NOTE]
    > برخلاف سایر کنترل‌های input، مقدار چک‌باکس‌ها و دکمه‌های رادیویی تنها زمانی در داده‌های ارسالی قرار می‌گیرد که در حال حاضر `checked` باشند. اگر چنین باشند، نام و مقدار(های) کنترل‌های علامت‌خورده ارسال می‌شوند.
    >
    > برای مثال، اگر چک‌باکسی با `name` برابر `fruit` مقدار `value` برابر `cherry` داشته باشد و چک‌باکس علامت‌خورده باشد، داده‌های فرم ارسالی شامل `fruit=cherry` خواهند بود. اگر چک‌باکس فعال نباشد، اصلاً در داده‌های فرم فهرست نمی‌شود. مقدار پیش‌فرض `value` برای چک‌باکس‌ها و دکمه‌های رادیویی `on` است.

- `colorspace`
  - : فقط برای input از نوع `color` معتبر است. attribute `colorspace` مشخص می‌کند که input با `type="color"` از کدام [فضای رنگی](/en-US/docs/Glossary/Color_space) استفاده می‌کند. مقادیر شمارشی (enumerated) ممکن عبارتند از:
    - `"limited-srgb"`: رنگ در فضای رنگی sRGB قرار دارد. این شامل مقادیر `rgb()`، `hsl()`، `hwb()` و `hex-color` است. مقدار رنگ برای هر مؤلفه `r`، `g` و `b` به ۸ بیت محدود می‌شود. این مقدار پیش‌فرض است.
    - `"display-p3"`: [فضای رنگی Display P3](/en-US/docs/Glossary/Color_space#display-p3)، مثلاً `color(display-p3 1.84 -0.19 0.72 / 0.6)`

- [`dirname`](/en-US/docs/Web/HTML/Reference/Attributes/dirname)
  - : برای انواع `hidden`، `text`، `search`، `url`، `tel` و `email` معتبر است. attribute `dirname` امکان ارسال جهت‌گیری (directionality) عنصر را فراهم می‌کند. وقتی این attribute وجود داشته باشد، کنترل فرم دو جفت نام/مقدار ارسال می‌کند: اولی [`name`](#name) و [`value`](#value) است و دومی نامی برابر با مقدار attribute `dirname` دارد و مقدار آن `ltr` یا `rtl` است که توسط مرورگر تعیین می‌شود.

    ```html
    <form action="page.html" method="post">
      <label>
        Fruit:
        <input type="text" name="fruit" dirname="fruit-dir" value="cherry" />
      </label>
      <input type="submit" />
    </form>
    <!-- page.html?fruit=cherry&fruit-dir=ltr -->
    ```

    وقتی فرم بالا ارسال می‌شود، input هم جفت `name`/`value` یعنی `fruit=cherry` و هم جفت `dirname`/جهت یعنی `fruit-dir=ltr` را می‌فرستد. برای اطلاعات بیشتر، به attribute [`dirname`](/en-US/docs/Web/HTML/Reference/Attributes/dirname) مراجعه کنید.

- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : یک attribute بولی است که اگر وجود داشته باشد، نشان می‌دهد کاربر نباید بتواند با input تعامل کند. inputهای غیرفعال معمولاً با رنگ تیره‌تر یا نوعی نشانه دیگر که نشان می‌دهد فیلد قابل استفاده نیست، نمایش داده می‌شوند.

    به طور خاص، inputهای غیرفعال رویداد `click` را دریافت نمی‌کنند و همراه با فرم ارسال نمی‌شوند.

> [!NOTE]
> اگرچه در مشخصات الزامی نیست، اما فایرفاکس به‌طور پیش‌فرض [حالت غیرفعال پویا (dynamic disabled state)](https://stackoverflow.com/questions/5985839/bug-with-firefox-disabled-attribute-of-input-not-resetting-when-refreshing) یک `<input>` را در طول بارگذاری‌های صفحه حفظ می‌کند. برای کنترل این ویژگی از attribute [`autocomplete`](#autocomplete) استفاده کنید.

- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : یک رشته (string) که مشخص می‌کند `<input>` به کدام عنصر {{HTMLElement("form")}} وابسته است (یعنی **مالک فرم** آن). اگر این attribute وجود داشته باشد، مقدار آن باید با `id` یک عنصر `<form>` در همان سند یکسان باشد. اگر این attribute مشخص نشود، `<input>` به نزدیک‌ترین فرمی که درون آن قرار دارد (در صورت وجود) وابسته می‌شود.

    attribute `form` به شما امکان می‌دهد یک input را در هر جایی از سند قرار دهید، اما آن را به فرمی در جای دیگر سند متصل کنید.

    > [!NOTE]
    > یک input فقط می‌تواند به یک فرم متصل شود.

- `formaction`
  - : فقط برای انواع input `image` و `submit` معتبر است. برای اطلاعات بیشتر به نوع input {{HTMLElement("input/submit", "submit")}} مراجعه کنید.
- `formenctype`
  - : فقط برای انواع input `image` و `submit` معتبر است. برای اطلاعات بیشتر به نوع input {{HTMLElement("input/submit", "submit")}} مراجعه کنید.
- `formmethod`
  - : فقط برای انواع input `image` و `submit` معتبر است. برای اطلاعات بیشتر به نوع input {{HTMLElement("input/submit", "submit")}} مراجعه کنید.
- `formnovalidate`
  - : فقط برای انواع input `image` و `submit` معتبر است. برای اطلاعات بیشتر به نوع input {{HTMLElement("input/submit", "submit")}} مراجعه کنید.
- `formtarget`
  - : فقط برای انواع input `image` و `submit` معتبر است. برای اطلاعات بیشتر به نوع input {{HTMLElement("input/submit", "submit")}} مراجعه کنید.
- `height`
  - : فقط برای دکمه input از نوع `image` معتبر است. `height` ارتفاع فایل تصویری است که برای نمایش دکمه ارسال گرافیکی استفاده می‌شود. به نوع input {{HTMLElement("input/image", "image")}} مراجعه کنید.
- `id`
  - : یک attribute سراسری (global) که برای همه عناصر از جمله انواع input معتبر است. یک شناسه یکتا (ID) تعریف می‌کند که باید در کل سند منحصربه‌فرد باشد. هدف آن شناسایی عنصر هنگام لینک‌دهی است. مقدار آن به عنوان مقدار attribute `for` در عنصر {{htmlelement('label')}} برای اتصال برچسب به کنترل فرم استفاده می‌شود. به {{htmlelement('label')}} مراجعه کنید.
- `inputmode`
  - : یک مقدار سراسری که برای همه عناصر معتبر است. به مرورگرها راهنمایی می‌کند که هنگام ویرایش این عنصر یا محتوای آن از چه نوع صفحه‌کلید مجازی استفاده کنند. مقادیر شامل `none`، `text`، `tel`، `url`، `email`، `numeric`، `decimal` و `search` است.
- `list`
  - : مقدار attribute `list` باید `id` یک عنصر {{HTMLElement("datalist")}} در همان سند باشد. `<datalist>` فهرستی از مقادیر از پیش‌تعریف‌شده را برای پیشنهاد به کاربر در این input فراهم می‌کند. هر مقداری در لیست که با [`type`](#type) سازگار نباشد، در گزینه‌های پیشنهادی قرار نمی‌گیرد. مقادیر ارائه‌شده پیشنهاد هستند، نه الزام: کاربران می‌توانند از این لیست از پیش‌تعریف‌شده انتخاب کنند یا مقدار متفاوتی وارد کنند.

    این attribute برای انواع `text`، `search`، `url`، `tel`، `email`، `date`، `month`، `week`، `time`، `datetime-local`، `number`، `range` و `color` معتبر است.

    طبق مشخصات، attribute `list` توسط انواع `hidden`، `password`، `checkbox`، `radio`، `file` و هیچ‌کدام از انواع دکمه پشتیبانی نمی‌شود.

    بسته به مرورگر، کاربر ممکن است یک پالت رنگی سفارشی، علامت‌های تیک در امتداد یک محدوده (range)، یا حتی یک input که مانند {{HTMLElement("select")}} باز می‌شود اما امکان مقادیر غیرفهرست‌شده را نیز می‌دهد، ببیند. برای سایر انواع input به [جدول سازگاری مرورگرها](/en-US/docs/Web/HTML/Reference/Elements/datalist#browser_compatibility) مراجعه کنید.

    به عنصر {{htmlelement('datalist')}} مراجعه کنید.

- [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
  - : برای `date`، `month`، `week`، `time`، `datetime-local`، `number` و `range` معتبر است. این ویژگی بزرگ‌ترین مقدار مجاز در محدودهٔ مقادیر مجاز را مشخص می‌کند. اگر [`value`](#value) وارد شده در المان از این مقدار بیشتر باشد، المان در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) (اعتبارسنجی محدودیت) رد می‌شود. اگر مقدار ویژگی `max` یک عدد نباشد، المان حداکثر مقدار نخواهد داشت.

    یک مورد خاص وجود دارد: اگر نوع داده دوره‌ای باشد (مانند تاریخ‌ها یا زمان‌ها)، مقدار `max` می‌تواند از مقدار `min` کمتر باشد، که نشان می‌دهد محدوده می‌تواند دور بزند. به عنوان مثال، این امکان را می‌دهد که یک محدوده زمانی از ساعت ۱۰ شب تا ۴ صبح تعیین کنید.

- [`maxlength`](/en-US/docs/Web/HTML/Reference/Attributes/maxlength)
  - : برای `text`، `search`، `url`، `tel`، `email` و `password` معتبر است. این ویژگی حداکثر طول رشته‌ای را که کاربر می‌تواند در فیلد وارد کند، تعیین می‌کند (بر حسب [`UTF-16 code units`](/en-US/docs/Glossary/UTF-16)). این مقدار باید یک عدد صحیح ۰ یا بیشتر باشد. اگر `maxlength` مشخص نشود یا مقدار نامعتبری داشته باشد، فیلد حداکثر طول نخواهد داشت. این مقدار همچنین باید بزرگ‌تر یا مساوی مقدار `minlength` باشد.

    اگر طول متن وارد شده در فیلد از `maxlength` [`UTF-16 code units`](/en-US/docs/Glossary/UTF-16) بیشتر باشد، ورودی در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) رد می‌شود. به‌طور پیش‌فرض، مرورگرها از وارد کردن کاراکترهای بیشتر از حد مجاز توسط ویژگی `maxlength` جلوگیری می‌کنند. اعتبارسنجی محدودیت فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند. برای اطلاعات بیشتر به [Client-side validation](#client-side_validation) مراجعه کنید.

- [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min)
  - : برای `date`، `month`، `week`، `time`، `datetime-local`، `number` و `range` معتبر است. این ویژگی کم‌ترین مقدار مجاز در محدودهٔ مقادیر مجاز را مشخص می‌کند. اگر [`value`](#value) وارد شده در المان کمتر از این مقدار باشد، المان در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) رد می‌شود. اگر مقدار ویژگی `min` یک عدد نباشد، المان حداقل مقدار نخواهد داشت.

    این مقدار باید کمتر یا مساوی مقدار ویژگی `max` باشد. اگر ویژگی `min` وجود داشته باشد اما مشخص نشده یا نامعتبر باشد، هیچ مقدار `min` اعمال نمی‌شود. اگر ویژگی `min` معتبر باشد و یک مقدار غیرخالی کمتر از حداقل مجاز توسط `min` وارد شود، اعتبارسنجی محدودیت از ارسال فرم جلوگیری می‌کند. برای اطلاعات بیشتر به [Client-side validation](#client-side_validation) مراجعه کنید.

    یک مورد خاص وجود دارد: اگر نوع داده دوره‌ای باشد (مانند تاریخ‌ها یا زمان‌ها)، مقدار `max` می‌تواند از مقدار `min` کمتر باشد، که نشان می‌دهد محدوده می‌تواند دور بزند. به عنوان مثال، این امکان را می‌دهد که یک محدوده زمانی از ساعت ۱۰ شب تا ۴ صبح تعیین کنید.

- [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength)
  - : برای `text`، `search`، `url`، `tel`، `email` و `password` معتبر است. این ویژگی حداقل طول رشته‌ای را که کاربر می‌تواند در فیلد وارد کند، تعیین می‌کند (بر حسب [`UTF-16 code units`](/en-US/docs/Glossary/UTF-16)). این مقدار باید یک عدد صحیح غیرمنفی و کوچک‌تر یا مساوی مقدار `maxlength` باشد. اگر `minlength` مشخص نشود یا مقدار نامعتبری داشته باشد، ورودی حداقل طول نخواهد داشت.

    اگر طول متن وارد شده در فیلد کمتر از `minlength` [`UTF-16 code units`](/en-US/docs/Glossary/UTF-16) باشد، ورودی در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) رد می‌شود و از ارسال فرم جلوگیری می‌کند. اعتبارسنجی محدودیت فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند. برای اطلاعات بیشتر به [Client-side validation](#client-side_validation) مراجعه کنید.

- [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple)
  - : ویژگی Boolean `multiple` در صورت تنظیم شدن به این معناست که کاربر می‌تواند در ویجت ایمیل، آدرس‌های ایمیل را با کاما جداگانه وارد کند، یا در input از نوع `file` بیش از یک فایل انتخاب کند. برای اطلاعات بیشتر به نوع‌های input `email` و `file` مراجعه کنید.

- `name`
  - : رشته‌ای که نامی برای کنترل input مشخص می‌کند. این نام هنگام ارسال داده‌های فرم به همراه مقدار کنترل ارسال می‌شود.

    `name` را یک ویژگی ضروری در نظر بگیرید (هرچند الزامی نیست). اگر یک input `name` نداشته باشد یا `name` آن خالی باشد، مقدار input با فرم ارسال نمی‌شود. (کنترل‌های غیرفعال، رادیو باتن‌های انتخاب‌نشده، چک‌باکس‌های انتخاب‌نشده و دکمه‌های ریست نیز ارسال نمی‌شوند.)

    دو مورد خاص وجود دارد:
    1. `_charset_` : اگر به عنوان `name` یک عنصر `<input>` از نوع {{HTMLElement("input/hidden", "hidden")}} استفاده شود، مقدار `value` آن input به‌طور خودکار توسط {{Glossary("user agent")}} به encoding کاراکتری که برای ارسال فرم استفاده می‌شود تنظیم می‌گردد.
    2. `isindex`: به دلایل تاریخی، نام [`isindex`](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#attr-fe-name) مجاز نیست.

    ویژگی [`name`](#name) رفتار منحصربه‌فردی برای رادیو باتن‌ها ایجاد می‌کند.

    در یک گروه از رادیو باتن‌های هم‌نام، فقط یک رادیو باتن می‌تواند در هر زمان انتخاب شود. انتخاب هر رادیو باتن در آن گروه به‌طور خودکار رادیو باتن انتخاب‌شدهٔ قبلی را لغو می‌کند. مقدار آن رادیو باتن انتخاب‌شده همراه با `name` در صورت ارسال فرم ارسال می‌شود.

    هنگام tab کردن در یک سری از رادیو باتن‌های هم‌نام، اگر یکی انتخاب شده باشد، همان یکی فوکوس می‌گیرد. اگر در ترتیب منبع (source order) گروه‌بندی نشده باشند، tab کردن به گروه از اولین رادیو باتن گروه شروع می‌شود و از رادیو باتن‌های انتخاب‌نشده عبور می‌کند. به عبارت دیگر، اگر یکی انتخاب شده باشد، tab کردن از رادیو باتن‌های انتخاب‌نشده در گروه عبور می‌کند. اگر هیچ‌کدام انتخاب نشده باشند، گروه رادیو باتن زمانی که اولین دکمه در گروه با همان `name` رسیده شود فوکوس می‌گیرد.

    پس از اینکه یکی از رادیو باتن‌های گروه فوکوس گرفت، استفاده از کلیدهای جهت‌نما در تمام رادیو باتن‌های همان `name` حرکت می‌کند، حتی اگر رادیو باتن‌ها در ترتیب منبع گروه‌بندی نشده باشند.

    وقتی یک عنصر input دارای `name` باشد، آن `name` به عنوان یک property از عنصر form مربوطه در ویژگی {{domxref("HTMLFormElement.elements")}} قرار می‌گیرد. اگر inputای با `name` برابر `guest` و input دیگری با `name` برابر `hat-size` داشته باشید، کد زیر قابل استفاده است:

    ```js
    let form = document.querySelector("form");

    let guestName = form.elements.guest;
    let hatSize = form.elements["hat-size"];
    ```

    پس از اجرای این کد، `guestName` معادل {{domxref("HTMLInputElement")}} برای فیلد `guest` و `hatSize` شیء مربوط به فیلد `hat-size` خواهد بود.

    > [!WARNING]
    > از دادن `name` به عناصر فرم که با propertyهای built-in فرم هم‌نام است خودداری کنید، زیرا در این صورت property یا method از پیش تعریف‌شده را با این ارجاع به input مربوطه override می‌کنید.

- [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern)
  - : این ویژگی برای فیلدهای `text`، `search`، `url`، `tel`، `email` و `password` معتبر است. `pattern` یک عبارت منظم (regular expression) تعریف می‌کند که مقدار [`value`](#value) ورودی باید با آن مطابقت داشته باشد تا در اعتبارسنجی محدودیت (constraint validation) قبول شود. این عبارت باید یک regular expression معتبر جاوااسکریپت باشد (مطابق با نوع `RegExp` و مستندات [راهنمای regular expressions](/en-US/docs/Web/JavaScript/Guide/Regular_expressions)). در متن الگو از اسلش استفاده نکنید. هنگام کامپایل regular expression:
    1. الگو به‌طور ضمنی با `^(?:` و `)$` پیچیده می‌شود، یعنی مطابقت باید با کل مقدار ورودی انجام شود: `^(?:<pattern>)$`.
    2. پرچم `'v'` تنظیم می‌شود تا الگو به‌عنوان دنباله‌ای از نقاط کد یونیکد (Unicode code points) در نظر گرفته شود، نه به‌صورت {{Glossary("ASCII")}}.

    اگر ویژگی `pattern` وجود داشته باشد اما مقدار نداشته باشد یا نامعتبر باشد، هیچ regular expression اعمال نمی‌شود و این ویژگی کاملاً نادیده گرفته می‌شود. اگر الگو معتبر باشد و مقدار غیرخالی با آن مطابقت نداشته باشد، اعتبارسنجی محدودیت از ارسال فرم جلوگیری می‌کند. اگر ویژگی [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple) نیز وجود داشته باشد، regular expression کامپایل‌شده با هر مقدار جدا شده با کاما مطابقت داده می‌شود.

    > [!NOTE]
    > اگر از ویژگی `pattern` استفاده می‌کنید، حتماً با توضیحات متنی در نزدیکی فیلد، کاربر را از فرمت مورد انتظار آگاه کنید. همچنین می‌توانید از ویژگی [`title`](#title) برای توضیح شرایط تطابق استفاده کنید؛ بیشتر مرورگرها این عنوان را به‌صورت tooltip نشان می‌دهند. توضیح قابل مشاهده برای دسترسی‌پذیری (accessibility) ضروری است. tooltip یک بهبود اضافی است.

    برای اطلاعات بیشتر به بخش [اعتبارسنجی سمت کلاینت](#client-side_validation) مراجعه کنید.

- [`placeholder`](/en-US/docs/Web/HTML/Reference/Attributes/placeholder)
  - : این ویژگی برای فیلدهای `text`، `search`، `url`، `tel`، `email`, `password` و `number` معتبر است. `placeholder` یک راهنمای کوتاه به کاربر می‌دهد که چه نوع اطلاعاتی در فیلد انتظار می‌رود. این متن باید یک کلمه یا عبارت کوتاه باشد که نوع دادهٔ مورد انتظار را نشان دهد، نه یک توضیح یا راهنمای کامل. متن _نباید_ شامل carriage return یا line feed باشد. برای مثال، اگر فیلد برای دریافت نام کوچک کاربر است و برچسب آن "نام کوچک" باشد، یک placeholder مناسب می‌تواند "مثلاً، علی" باشد.

    > [!NOTE]
    > ویژگی `placeholder` از نظر معنایی به خوبی روش‌های دیگر توضیح فرم نیست و ممکن است مشکلات فنی غیرمنتظره‌ای در محتوای شما ایجاد کند. برای اطلاعات بیشتر به بخش [برچسب‌ها](#labels) مراجعه کنید.

- `popovertarget`
  - : یک عنصر `<input type="button">` را به دکمه کنترل popover تبدیل می‌کند؛ مقدار آن ID عنصر popoverای است که قرار است کنترل شود. برای جزئیات بیشتر به صفحه اصلی Popover API مراجعه کنید. برقراری ارتباط بین یک popover و دکمه فراخوان آن با استفاده از ویژگی `popovertarget` دو اثر مفید اضافی دارد:
    - مرورگر یک رابطه ضمنی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) و [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) بین popover و فراخوان ایجاد می‌کند و هنگام نمایش، popover را در موقعیت منطقی ترتیب ناوبری با کیبورد قرار می‌دهد. این کار باعث می‌شود popover برای کاربران کیبورد و فناوری کمکی (AT) در دسترس‌تر باشد (همچنین ببینید: [Popover accessibility features](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features)).
    - مرورگر یک مرجع anchor ضمنی بین این دو ایجاد می‌کند و موقعیت‌دهی popoverها را نسبت به کنترل‌هایشان با استفاده از [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) بسیار راحت می‌کند. برای جزئیات بیشتر به [Popover anchor positioning](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) مراجعه کنید.

- `popovertargetaction`
  - : عملیاتی را که باید روی عنصر popover کنترل‌شده توسط یک `<input type="button">` انجام شود مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `"hide"`
      - : دکمه یک popover نمایش‌داده‌شده را مخفی می‌کند. اگر بخواهید یک popover از قبل مخفی را مخفی کنید، هیچ اقدامی انجام نمی‌شود.
    - `"show"`
      - : دکمه یک popover مخفی را نشان می‌دهد. اگر بخواهید یک popover در حال نمایش را نشان دهید، هیچ اقدامی انجام نمی‌شود.
    - `"toggle"`
      - : دکمه وضعیت یک popover را بین نمایش و مخفی‌بودن عوض می‌کند. اگر popover مخفی باشد، نشان داده می‌شود؛ اگر در حال نمایش باشد، مخفی می‌شود. اگر `popovertargetaction` حذف شود، `"toggle"` عمل پیش‌فرضی است که توسط دکمه کنترل انجام می‌شود.

- [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly)
  - : ویژگی Boolean که اگر وجود داشته باشد، نشان می‌دهد کاربر نباید بتواند مقدار ورودی را ویرایش کند. ویژگی `readonly` توسط انواع ورودی `text`, `search`, `url`, `tel`, `email`, `date`, `month`, `week`, `time`, `datetime-local`, `number` و `password` پشتیبانی می‌شود.

    برای اطلاعات بیشتر به [HTML attribute: `readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly) مراجعه کنید.

- [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required)
  - : `required` یک ویژگی Boolean است که اگر وجود داشته باشد، نشان می‌دهد کاربر باید قبل از ارسال فرم مربوطه، مقداری را برای ورودی مشخص کند. ویژگی `required` توسط ورودی‌های `text`, `search`, `url`, `tel`, `email`, `date`, `month`, `week`, `time`, `datetime-local`, `number`, `password`, `checkbox`, `radio` و `file` پشتیبانی می‌شود.

    برای اطلاعات بیشتر به [Client-side validation](#client-side_validation) و [HTML attribute: `required`](/en-US/docs/Web/HTML/Reference/Attributes/required) مراجعه کنید.

- [`size`](/en-US/docs/Web/HTML/Reference/Attributes/size)
  - : برای `email`, `password`, `tel`, `url` و `text` معتبر است؛ ویژگی `size` مشخص می‌کند چه مقدار از ورودی نمایش داده شود. اساساً همان نتیجه تنظیم ویژگی CSS `width` را با چند ویژگی خاص ایجاد می‌کند. واحد واقعی مقدار به نوع ورودی بستگی دارد. برای `password` و `text`، تعداد کاراکترها (یا واحدهای `em`) با مقدار پیش‌فرض `20` است، و برای بقیه، پیکسل (یا واحدهای `px`). CSS `width` بر ویژگی `size` اولویت دارد.

- `src`
  - : فقط برای دکمه ورودی `image` معتبر است؛ `src` رشته‌ای است که URL فایل تصویری را برای نمایش به عنوان دکمه ارسال گرافیکی مشخص می‌کند. به تایپ ورودی `image` مراجعه کنید.

- [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step)
  - : ویژگی `step` برای ورودی‌های `date`, `month`, `week`, `time`, `datetime-local`, `number` و `range` معتبر است. این attribute یک عدد است که دقت (granularity) مقدار ورودی را مشخص می‌کند. فقط مقادیری معتبر هستند که مضرب صحیحی از `step` نسبت به پایه گام (step base) باشند. پایه گام اگر `min` مشخص شده باشد همان `min` است، در غیر این صورت `value`، و اگر هیچکدام مشخص نشده باشد `0` (به جز برای `week` که پایه گام پیش‌فرض آن ۲۵۹٬۲۰۰٬۰۰۰- است که شروع هفته ۱۹۷۰-W01 را نشان می‌دهد).

    اگر به صراحت مشخص نشود:
    - `step` برای `number` و `range` پیش‌فرض ۱ است.
    - هر نوع ورودی تاریخ/زمان مقدار پیش‌فرض `step` مناسب خود را دارد؛ به صفحات جداگانه هر ورودی مراجعه کنید: [`date`](/en-US/docs/Web/HTML/Reference/Elements/input/date#step), [`datetime-local`](/en-US/docs/Web/HTML/Reference/Elements/input/datetime-local#step), [`month`](/en-US/docs/Web/HTML/Reference/Elements/input/month#step), [`time`](/en-US/docs/Web/HTML/Reference/Elements/input/time#step) و [`week`](/en-US/docs/Web/HTML/Reference/Elements/input/week#step).

    مقدار باید یک عدد مثبت (integer یا float) یا مقدار ویژه `any` باشد که به معنای عدم وجود گام‌بندی است و هر مقداری مجاز است (با رعایت سایر محدودیت‌ها مانند [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) و [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)).

    برای مثال، اگر `<input type="number" min="10" step="2">` داشته باشید، هر عدد صحیح زوج بزرگتر یا مساوی ۱۰ معتبر است. اگر حذف شود، `<input type="number">` هر عدد صحیحی معتبر است اما اعداد اعشاری (مانند ۴.۲) معتبر نیستند، زیرا `step` پیش‌فرض ۱ است. برای معتبر بودن ۴.۲، باید `step` را `any`، ۰.۱، ۰.۲ یا مقدار `min` را به عددی که به `.۲` ختم می‌شود تنظیم کرد، مانند `<input type="number" min="-5.2">`.

    > **توجه:**
    > اگر داده وارد شده توسط کاربر با تنظیمات گام‌بندی مطابقت نداشته باشد، مقدار در اعتبارسنجی محدودیت (constraint validation) نامعتبر در نظر گرفته می‌شود و با شبه‌کلاس `:invalid` مطابقت دارد.

    برای اطلاعات بیشتر به بخش [اعتبارسنجی سمت کلاینت](#client-side_validation) مراجعه کنید.

- [`switch`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox#switch)
  - : ویژگی `switch` فقط برای ورودی `checkbox` معتبر است. این attribute یک Boolean است که نشان می‌دهد آیا checkbox باید به صورت یک سوئیچ نمایش داده شود.

    > **توجه:**
    > این attribute هنوز آزمایشی است و پشتیبانی محدودی در مرورگرها دارد. در مرورگرهای ناسازگار نادیده گرفته می‌شود.

- `tabindex`
  - : یک global attribute که برای همه عناصر (از جمله همه انواع input) معتبر است. یک عدد صحیح که مشخص می‌کند آیا عنصر می‌تواند focus بگیرد (focusable است) و آیا باید در ناوبری صفحه‌کلید ترتیبی شرکت کند. از آنجایی که همه انواع input به جز نوع `hidden` focusable هستند، این attribute نباید روی کنترل‌های فرم استفاده شود، زیرا انجام این کار نیاز به مدیریت ترتیب focus برای همه عناصر درون document دارد و در صورت نادرست انجام شدن، به کاربردپذیری (usability) و دسترسی‌پذیری (accessibility) آسیب می‌زند.

- `title`
  - : یک global attribute که برای همه عناصر (از جمله همه انواع input) معتبر است. متنی را شامل می‌شود که اطلاعات راهنمایی (advisory information) مرتبط با عنصر را ارائه می‌دهد. این اطلاعات معمولاً (اما نه لزوماً) به صورت tooltip به کاربر نشان داده می‌شود. `title` نباید به عنوان توضیح اصلی هدف کنترل فرم استفاده شود. در عوض، از عنصر `<label>` با attribute `for` که به `id` کنترل فرم اشاره می‌کند استفاده کنید. به بخش [Labels](#labels) در زیر مراجعه کنید.

- `type`
  - : یک رشته که نوع کنترل را برای نمایش مشخص می‌کند. مثلاً برای ایجاد یک checkbox از مقدار `checkbox` استفاده می‌شود. اگر حذف شود (یا مقدار ناشناخته‌ای مشخص شود)، نوع input `text` استفاده می‌شود و یک فیلد ورودی متن ساده ایجاد می‌کند.

    مقادیر مجاز در بخش [Input types](#input_types) در بالا فهرست شده‌اند.

- `value`
  - : مقدار کنترل ورودی (input control). زمانی که در HTML مشخص شود، این مقدار اولیه است و از آن پس می‌توان با استفاده از JavaScript از طریق property `value` متعلق به آبجکت {{domxref("HTMLInputElement")}} مربوطه، آن را تغییر داد یا خواند. attribute `value` همیشه اختیاری است، اما برای `checkbox`، `radio` و `hidden` باید حتماً در نظر گرفته شود.

- `width`
  - : فقط برای دکمه ورودی از نوع `image` معتبر است. `width` عرض فایل تصویری است که برای نمایش دکمه submit گرافیکی به کار می‌رود. به نوع ورودی `<input type="image">` مراجعه کنید.

### ویژگی‌های غیراستاندارد

ویژگی‌های غیراستاندارد زیر نیز در برخی مرورگرها در دسترس هستند. به‌عنوان یک قانون کلی، تا حد امکان از استفاده از آن‌ها خودداری کنید.

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">Attribute</th>
      <th scope="col">توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="#incremental"><code>incremental</code></a></td>
      <td>
        مشخص می‌کند که آیا رویدادهای {{domxref("HTMLInputElement/search_event", "search")}} مکرر ارسال شوند تا بتوان نتایج جستجوی زنده را در حالی که کاربر هنوز در حال ویرایش مقدار فیلد است به‌روزرسانی کرد.
        <strong>فقط WebKit و Blink (Safari، Chrome، Opera و غیره).</strong>
      </td>
    </tr>
    <tr>
      <td><code>mozactionhint</code> {{deprecated_inline}}</td>
      <td>
        <p>رشته‌ای که نوع عملی را که هنگام فشردن کلید <kbd>Enter</kbd> یا <kbd>Return</kbd> در حین ویرایش فیلد انجام می‌شود مشخص می‌کند؛ این مقدار برای تعیین برچسب مناسب برای آن کلید روی صفحه‌کلید مجازی استفاده می‌شود. <strong>از آنجایی که این attribute منسوخ (deprecated) شده است، به جای آن از <a href="/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint"><code>enterkeyhint</code></a> استفاده کنید.</strong></p>
      </td>
    </tr>
    <tr>
      <td><a href="#orient"><code>orient</code></a></td>
      <td>
        جهت اسلایدر range را تنظیم می‌کند. <strong>فقط Firefox</strong>.
      </td>
    </tr>
    <tr>
      <td><a href="#results"><code>results</code></a></td>
      <td>
        حداکثر تعداد آیتم‌هایی که باید در لیست کشویی جستجوهای قبلی نمایش داده شود. <strong>فقط Safari.</strong>
      </td>
    </tr>
    <tr>
      <td>
        <a href="#webkitdirectory"><code>webkitdirectory</code></a>
      </td>
      <td>
        یک Boolean که نشان می‌دهد آیا فقط به کاربر اجازه انتخاب یک دایرکتوری (یا دایرکتوری‌ها، در صورت وجود <a href="#multiple"><code>multiple</code></a>) داده شود.
      </td>
    </tr>
  </tbody>
</table>

- `incremental` {{non-standard_inline}}
  - : attribute بولی `incremental` یک افزونه (extension) WebKit و Blink است (بنابراین توسط Safari، Opera، Chrome و غیره پشتیبانی می‌شود). اگر وجود داشته باشد، به {{Glossary("user agent")}} می‌گوید که ورودی را به‌عنوان یک جستجوی زنده (live search) پردازش کند. در حین ویرایش مقدار فیلد توسط کاربر، user agent رویدادهای {{domxref("HTMLInputElement/search_event", "search")}} را به آبجکت {{domxref("HTMLInputElement")}} که نمایانگر جعبه جستجو است ارسال می‌کند. این امکان را به کد شما می‌دهد که نتایج جستجو را در زمان واقعی (real time) در حین ویرایش جستجو به‌روزرسانی کند.

    اگر `incremental` مشخص نشده باشد، رویداد {{domxref("HTMLInputElement/search_event", "search")}} تنها زمانی ارسال می‌شود که کاربر به‌صراحت یک جستجو را آغاز کند (مانند فشردن کلید <kbd>Enter</kbd> یا <kbd>Return</kbd> در حین ویرایش فیلد).

    رویداد `search` محدود به نرخ (rate-limited) است به‌طوری که بیشتر از یک بازه زمانی تعریف‌شده توسط پیاده‌سازی ارسال نشود.

- `orient` (غیراستاندارد)
  - : مانند ویژگی CSS غیراستاندارد `-moz-orient` که بر عناصر `<progress>` و `<meter>` تأثیر می‌گذارد، ویژگی `orient` جهت اسلایدر محدوده را تعیین می‌کند. مقادیر شامل `horizontal` (افقی) و `vertical` (عمودی) هستند. برای روش مدرن ساخت کنترل‌های فرم عمودی، به [ایجاد کنترل‌های فرم عمودی](/en-US/docs/Web/CSS/Guides/Writing_modes/Vertical_controls) مراجعه کنید.

- `results` (غیراستاندارد)
  - : ویژگی `results` که فقط توسط Safari پشتیبانی می‌شود، یک مقدار عددی است که به شما امکان می‌دهد حداکثر تعداد آیتم‌های نمایش‌داده‌شده در منوی کشویی داخلی عنصر `<input>` را برای جستجوهای قبلی بازنویسی کنید.

    مقدار باید یک عدد اعشاری غیرمنفی باشد. اگر ارائه نشود یا مقدار نامعتبر باشد، حداکثر تعداد پیش‌فرض مرورگر استفاده می‌شود.

- `webkitdirectory` (غیراستاندارد)
  - : ویژگی بولی `webkitdirectory`، در صورت وجود، نشان می‌دهد که در رابط انتخاب فایل، فقط پوشه‌ها باید برای انتخاب در دسترس کاربر باشند. برای جزئیات و مثال‌های بیشتر به `HTMLInputElement.webkitdirectory` مراجعه کنید.

    اگرچه در ابتدا فقط برای مرورگرهای مبتنی بر WebKit پیاده‌سازی شده بود، `webkitdirectory` در Microsoft Edge و همچنین Firefox 50 و جدیدتر نیز قابل استفاده است. با این حال، حتی با وجود پشتیبانی نسبتاً گسترده، هنوز استاندارد نیست و نباید استفاده شود مگر اینکه چاره‌ای جز آن نداشته باشید.

## متدها

متدهای زیر توسط رابط `HTMLInputElement` ارائه می‌شوند که عناصر `<input>` را در DOM نشان می‌دهد. همچنین متدهایی که توسط رابط‌های والد یعنی `HTMLElement`، `Element`، `Node` و `EventTarget` مشخص شده‌اند نیز در دسترس هستند.

- `checkValidity()`
  - : اگر مقدار عنصر بررسی‌های اعتبارسنجی را پاس کند، `true` برمی‌گرداند؛ در غیر این صورت `false` برمی‌گرداند و رویداد `invalid` را روی عنصر صادر می‌کند.
- `reportValidity()`
  - : اگر مقدار عنصر بررسی‌های اعتبارسنجی را پاس کند، `true` برمی‌گرداند؛ در غیر این صورت `false` برمی‌گرداند، رویداد `invalid` را روی عنصر صادر می‌کند و (اگر رویداد لغو نشده باشد) مشکل را به کاربر گزارش می‌دهد.
- `select()`
  - : کل محتوای عنصر `<input>` را انتخاب می‌کند، اگر محتوای عنصر قابل انتخاب باشد. برای عناصری که محتوای متنی قابل انتخابی ندارند (مانند انتخابگر رنگ بصری یا ورودی تاریخ تقویمی)، این متد هیچ کاری انجام نمی‌دهد.
- `setCustomValidity()`
  - : اگر مقدار عنصر ورودی معتبر نباشد، یک پیام سفارشی برای نمایش تنظیم می‌کند.
- `setRangeText()`
  - : محتوای محدوده مشخص‌شده‌ای از کاراکترها را در عنصر ورودی به یک رشته داده‌شده تنظیم می‌کند. پارامتر `selectMode` برای کنترل نحوه تأثیر بر محتوای موجود در دسترس است.
- `setSelectionRange()`
  - : محدوده مشخص‌شده‌ای از کاراکترها را در یک عنصر ورودی متنی انتخاب می‌کند. برای ورودی‌هایی که به‌عنوان فیلدهای متنی ارائه نمی‌شوند، هیچ کاری انجام نمی‌دهد.
- `showPicker()`
  - : انتخابگر مرورگر را برای عنصر ورودی نمایش می‌دهد؛ همان چیزی که معمولاً با انتخاب عنصر نمایش داده می‌شود، اما با فشردن دکمه یا تعامل کاربر دیگر فعال می‌شود.
- `stepDown()`
  - : مقدار یک ورودی عددی را به‌طور پیش‌فرض یک واحد کاهش می‌دهد، یا به تعداد واحدهای مشخص‌شده کاهش می‌دهد.
- `stepUp()`
  - : مقدار یک ورودی عددی را یک واحد یا به تعداد واحدهای مشخص‌شده افزایش می‌دهد.

## CSS

inputها بهعنوان replaced elements ویژگیهایی دارند که روی عناصر غیرفرم اعمال نمیشوند. سلکتورهای CSS میتوانند کنترلهای فرم را بر اساس ویژگیهای UI آنها هدف قرار دهند؛ به این سلکتورها شبهکلاسهای UI میگویند. همچنین میتوان عنصر input را با استفاده از attribute selectors بر اساس نوع آن انتخاب کرد. چند property هم هستند که در این زمینه کاربرد ویژهای دارند.

### UI pseudo-classes

| شبه-کلاس | توضیحات |
|-----------|----------|
| {{Cssxref(":enabled")}} | هر عنصر فعالی که بتوان آن را فعال کرد (انتخاب، کلیک، تایپ و غیره) یا focus دریافت کند، و همچنین حالتی disabled دارد که در آن نمی‌توان فعال یا focus دریافت کرد. |
| {{Cssxref(":disabled")}} | هر عنصر غیرفعالی که حالت enabled دارد، یعنی اگر غیرفعال نبود می‌توانست فعال شود (انتخاب، کلیک، تایپ و غیره) یا focus دریافت کند. |
| {{Cssxref(":read-only")}} | عنصری که کاربر نمی‌تواند آن را ویرایش کند. |
| {{Cssxref(":read-write")}} | عنصری که کاربر می‌تواند آن را ویرایش کند. |
| {{Cssxref(":placeholder-shown")}} | عنصری که در حال حاضر متن placeholder را نمایش می‌دهد، شامل عناصر `<input>` و {{HTMLElement("textarea")}} با ویژگی <a href="#placeholder"><code>placeholder</code></a> که هنوز مقداری ندارند. |
| {{Cssxref(":default")}} | فرم‌المان‌هایی که در یک گروه از عناصر مرتبط، پیش‌فرض هستند. با نوع‌های ورودی {{HTMLElement("input/checkbox", "checkbox")}} و {{HTMLElement("input/radio", "radio")}} که در هنگام بارگذاری یا رندر صفحه checked بوده‌اند، مطابقت دارد. |
| {{Cssxref(":checked")}} | با نوع‌های ورودی {{HTMLElement("input/checkbox", "checkbox")}} و {{HTMLElement("input/radio", "radio")}} که در حال حاضر checked هستند (و {{HTMLElement("option")}} در یک {{HTMLElement("select")}} که در حال حاضر انتخاب شده است) مطابقت دارد. |
| {{Cssxref(":indeterminate")}} | عناصر {{HTMLElement("input/checkbox", "checkbox")}} که خاصیت indeterminate آن‌ها توسط JavaScript به true تنظیم شده است، عناصر {{HTMLElement("input/radio", "radio")}} زمانی که تمام دکمه‌های رادیویی با مقدار name یکسان در فرم unchecked هستند، و عناصر {{HTMLElement("progress")}} در حالت indeterminate. |
| {{Cssxref(":valid")}} | کنترل‌های فرمی که می‌توان اعتبارسنجی محدودیت روی آن‌ها اعمال کرد و در حال حاضر معتبر هستند. |
| {{Cssxref(":invalid")}} | کنترل‌های فرمی که اعتبارسنجی محدودیت روی آن‌ها اعمال شده و در حال حاضر معتبر نیستند. با یک کنترل فرم که مقدار آن با محدودیت‌های تعیین‌شده توسط ویژگی‌هایش مانند <a href="#required"><code>required</code></a>، <a href="#pattern"><code>pattern</code></a>، <a href="#step"><code>step</code></a> و <a href="#max"><code>max</code></a> مطابقت ندارد، مطابقت دارد. |
| {{Cssxref(":in-range")}} | ورودی غیرخالی که مقدار فعلی آن در محدوده تعیین‌شده توسط ویژگی‌های <a href="#min"><code>min</code></a> و <a href="#max"><code>max</code></a> و <a href="#step"><code>step</code></a> باشد. |
| {{Cssxref(":out-of-range")}} | ورودی غیرخالی که مقدار فعلی آن در محدوده تعیین‌شده توسط ویژگی‌های <a href="#min"><code>min</code></a> و <a href="#max"><code>max</code></a> نیست یا از محدودیت <a href="#step"><code>step</code></a> پیروی نمی‌کند. |
| {{Cssxref(":required")}} | عنصر `<input>`، {{HTMLElement("select")}} یا {{HTMLElement("textarea")}} که ویژگی <a href="#required"><code>required</code></a> روی آن تنظیم شده باشد. فقط با عناصری که می‌توانند required باشند مطابقت دارد. قرار دادن این ویژگی روی عنصری که نمی‌تواند required باشد باعث مطابقت نمی‌شود. |
| {{Cssxref(":optional")}} | عنصر `<input>`، {{HTMLElement("select")}} یا {{HTMLElement("textarea")}} که ویژگی <a href="#required"><code>required</code></a> روی آن تنظیم نشده باشد. با عناصری که نمی‌توانند required باشند مطابقت ندارد. |
| {{Cssxref(":blank")}} | عناصر `<input>` و {{HTMLElement("textarea")}} که در حال حاضر مقداری ندارند. |
| {{Cssxref(":user-invalid")}} | مشابه <code>:invalid</code> است، اما در رویداد blur فعال می‌شود. با ورودی نامعتبر مطابقت دارد، اما فقط پس از تعامل کاربر، مانند focus روی کنترل، ترک کنترل، یا تلاش برای ارسال فرم حاوی کنترل نامعتبر. |
| {{Cssxref(":open")}} | عناصر `<input>` که یک انتخاب‌گر برای انتخاب مقدار به کاربر نمایش می‌دهند (مثلاً <a href="/en-US/docs/Web/HTML/Reference/Elements/input/color"><code>&lt;input type="color"&gt;</code></a>) — اما فقط زمانی که عنصر در حالت باز (open) است، یعنی زمانی که انتخاب‌گر نمایش داده می‌شود. |

#### مثال pseudo-classes

می‌توانیم برچسب یک checkbox را بر اساس checked یا unchecked بودن آن استایل دهیم. در این مثال، ویژگی‌های `color` و `font-weight` عنصر `<label>` را که بلافاصله بعد از یک input checked قرار دارد، استایل می‌دهیم. اگر `input` checked نباشد، هیچ استایلی اعمال نمی‌شود.

```html hidden
<input id="checkboxInput" type="checkbox" />
<label for="checkboxInput">Toggle the checkbox on and off</label>
```

```css
input:checked + label {
  color: red;
  font-weight: bold;
}
```

### انتخاب‌گرهای attribute

می‌توان انواع مختلف کنترل‌های فرم را بر اساس [`type`](#type) آن‌ها با استفاده از [attribute selectors](/en-US/docs/Learn_web_development/Core/Styling_basics/Attribute_selectors) هدف قرار داد. انتخاب‌گرهای attribute در CSS عناصر را بر اساس وجود یک attribute یا مقدار مشخصی از آن attribute تطبیق می‌دهند.

```css
/* یک input از نوع password را انتخاب می‌کند */
input[type="password"] {
}

/* یک کنترل فرم که مقادیر معتبر آن محدود به یک بازه است را انتخاب می‌کند */
input[min][max] {
}

/* یک کنترل فرم با attribute pattern را انتخاب می‌کند */
input[pattern] {
}
```

### ::placeholder

به‌طور پیش‌فرض، ظاهر متن placeholder به صورت نیمه‌شفاف یا خاکستری روشن است. شبه‌عنصر `::placeholder` مربوط به [`placeholder` text](#placeholder) input است. این شبه‌عنصر را می‌توان با زیرمجموعه‌ای محدود از ویژگی‌های CSS استایل داد.

```css
::placeholder {
  color: blue;
}
```

فقط زیرمجموعه‌ای از ویژگی‌های CSS که برای شبه‌عنصر `::first-line` قابل استفاده هستند، می‌توانند در قاعده‌ای که از `::placeholder` در انتخاب‌گر خود استفاده می‌کند، به کار روند.

### caret-color

یک ویژگی مخصوص عناصر ورودی متن، ویژگی CSS `caret-color` است که به شما امکان می‌دهد رنگ caret (نشانگر) ورودی متن را تنظیم کنید:

#### HTML

```html
<label for="textInput">Note the red caret:</label>
<input id="textInput" class="custom" size="32" />
```

#### CSS

```css
input.custom {
  caret-color: red;
  font:
    16px "Helvetica",
    "Arial",
    sans-serif;
}
```

#### نتیجه

### field-sizing

ویژگی `field-sizing` به شما امکان می‌دهد رفتار اندازه‌گیری کنترل‌های فرم را کنترل کنید (به‌طور پیش‌فرض آن‌ها یک اندازه ترجیحی دارند). این ویژگی به شما امکان می‌دهد رفتار پیش‌فرض را لغو کرده و کنترل‌های فرم را طوری تنظیم کنید که اندازه آن‌ها با محتوایشان تطبیق یابد.

این ویژگی معمولاً برای ایجاد فیلدهای فرمی استفاده می‌شود که محتوای خود را در بر می‌گیرند و با تایپ متن بیشتر بزرگ می‌شوند. این ویژگی با انواع input که ورودی مستقیم متن را می‌پذیرند (مانند [`text`](/en-US/docs/Web/HTML/Reference/Elements/input/text) و [`url`](/en-US/docs/Web/HTML/Reference/Elements/input/url))، نوع input [`file`](/en-US/docs/Web/HTML/Reference/Elements/input/file) و عناصر `<textarea>` کار می‌کند.

### object-position و object-fit

در برخی موارد (معمولاً مربوط به inputهای غیرمتنی و رابط‌های تخصصی)، عنصر `<input>` یک [replaced element] است. در این حالت، موقعیت و اندازه عنصر درون قاب خود را می‌توان با استفاده از ویژگی‌های CSS `object-position` و `object-fit` تنظیم کرد.

### استایل‌دهی

برای اطلاعات بیشتر در مورد افزودن رنگ به عناصر در HTML، به موارد زیر مراجعه کنید:

- [Applying color to HTML elements using CSS](/en-US/docs/Web/CSS/Guides/Colors/Applying_color)

همچنین ببینید:

- [Styling HTML forms](/en-US/docs/Learn_web_development/Extensions/Forms/Styling_web_forms)
- [Advanced styling for HTML forms](/en-US/docs/Learn_web_development/Extensions/Forms/Advanced_form_styling)

## قابلیت‌های اضافی

### Labels

برای مرتبط کردن متن کمکی با یک `<input>`، به عنصر `<label>` نیاز داریم. عنصر `<label>` اطلاعات توضیحی درباره یک فیلد فرم فراهم می‌کند که _همیشه_ مناسب است (به‌جز نگرانی‌های مربوط به چیدمان). استفاده از `<label>` برای توضیح اینکه چه چیزی باید در `<input>` یا `<textarea>` وارد شود، هرگز ایده بدی نیست.

#### labelهای مرتبط

جفت‌سازی معنایی عناصر `<input>` و `<label>` برای فناوری‌های کمکی مانند صفحه‌خوان‌ها مفید است. با جفت‌کردن آن‌ها از طریق attribute [`for`](/en-US/docs/Web/HTML/Reference/Elements/label#for) متعلق به `<label>`، label را به input پیوند می‌دهید تا صفحه‌خوان‌ها بتوانند inputها را دقیق‌تر برای کاربران توصیف کنند.

داشتن متن ساده در کنار عنصر `<input>` کافی نیست. بلکه کاربردپذیری و دسترس‌پذیری، درج یک `<label>` ضمنی یا صریح را الزامی می‌کند:

```html
<!-- inaccessible -->
<p>Enter your name: <input id="name" type="text" size="30" /></p>

<!-- implicit label -->
<p>
  <label>Enter your name: <input id="name" type="text" size="30" /></label>
</p>

<!-- explicit label -->
<p>
  <label for="name">Enter your name: </label>
  <input id="name" type="text" size="30" />
</p>
```

مثال اول دسترس‌ناپذیر است: هیچ رابطه‌ای بین متن راهنما و عنصر `<input>` وجود ندارد.

علاوه بر یک نام دسترس‌پذیر، label ناحیهٔ هدف بزرگ‌تری برای کاربران ماوس و صفحه‌های لمسی فراهم می‌کند تا روی آن کلیک کنند یا آن را لمس کنند. با جفت‌کردن یک `<label>` با یک `<input>`، کلیک روی هرکدام باعث فوکوس شدن `<input>` می‌شود. اگر برای «label کردن» input خود از متن ساده استفاده کنید، این اتفاق نمی‌افتد. قرار دادن متن راهنما در بخش فعال‌سازی input برای افرادی که مشکلات کنترل حرکتی دارند مفید است.

به‌عنوان توسعه‌دهنده وب، مهم است که هرگز فرض نکنیم کاربران همه چیزهایی را که ما می‌دانیم می‌دانند. تنوع افرادی که از وب—و به‌تبع آن از وب‌سایت شما—استفاده می‌کنند، عملاً تضمین می‌کند که برخی از بازدیدکنندگان، فرآیندهای فکری و/یا شرایطی متفاوت داشته باشند و بدون labelهای واضح و درست، فرم‌های شما را بسیار متفاوت از شما تفسیر کنند.

#### placeholderها دسترس‌پذیر نیستند

attribute [`placeholder`](#placeholder) به شما اجازه می‌دهد متنی را مشخص کنید که وقتی `<input>` خالی است، در خود ناحیهٔ محتوای عنصر ظاهر می‌شود. هرگز نباید برای درک فرم‌هایتان به placeholder وابسته باشید. placeholder یک label نیست و نباید به‌عنوان جایگزین آن استفاده شود، چون واقعاً جایگزین نیست. placeholder برای ارائه یک راهنمایی (hint) درباره اینکه مقدار واردشده باید چه شکلی باشد استفاده می‌شود، نه برای توضیح یا متن راهنما.

placeholder نه‌تنها برای صفحه‌خوان‌ها دسترس‌پذیر نیست، بلکه به محض اینکه کاربر متنی را در کنترل فرم وارد کند، یا اگر کنترل فرم از قبل مقداری داشته باشد، placeholder ناپدید می‌شود. مرورگرهایی که قابلیت ترجمه خودکار صفحه دارند ممکن است هنگام ترجمه از کنار attributeها بگذرند؛ یعنی ممکن است `placeholder` ترجمه نشود.

> [!NOTE]
> در صورت امکان از attribute [`placeholder`](#placeholder) استفاده نکنید. اگر لازم است یک عنصر `<input>` را برچسب‌گذاری کنید، از عنصر `<label>` استفاده کنید.

### اعتبارسنجی سمت کلاینت

> [!WARNING]
> اعتبارسنجی سمت کلاینت مفید است، اما تضمین نمی‌کند که سرور داده معتبر دریافت کند. اگر داده باید در قالب خاصی باشد، _همیشه_ آن را در سمت سرور هم بررسی کنید و اگر قالب نامعتبر بود، یک [`400` HTTP response](/en-US/docs/Web/HTTP/Reference/Status/400) برگردانید.

علاوه بر استفاده از CSS برای استایل‌دهی به inputها بر اساس stateهای `:valid` یا `:invalid` (که به وضعیت فعلی هر input بستگی دارد)، همانطور که در بخش [شبه‌کلاس‌های UI](#ui_pseudo-classes) اشاره شد، مرورگر اعتبارسنجی سمت کلاینت را هنگام تلاش برای ارسال فرم فراهم می‌کند. هنگام ارسال فرم، اگر یک کنترل فرم از پسِ محدودیت‌های اعتبارسنجی (constraint validation) برنیاید، مرورگرهای پشتیبان اولین کنترل فرم نامعتبر را با پیام خطا نمایش می‌دهند؛ پیامی که یا بر اساس نوع خطا به‌صورت پیش‌فرض است یا پیامی که شما تنظیم کرده‌اید.

بعضی از نوع‌های `input` و سایر attributeها محدودیت‌هایی روی مقادیر معتبر یک input اعمال می‌کنند. برای مثال، `<input type="number" min="2" max="10" step="2">` یعنی فقط اعداد ۲، ۴، ۶، ۸ یا ۱۰ معتبر هستند. چندین خطا ممکن است رخ دهد، از جمله خطای `rangeUnderflow` اگر مقدار کمتر از ۲ باشد، `rangeOverflow` اگر بیشتر از ۱۰ باشد، `stepMismatch` اگر مقدار عددی بین ۲ و ۱۰ باشد اما یک عدد زوج نباشد (با الزامات attribute `step` مطابقت نداشته باشد)، یا `typeMismatch` اگر مقدار عدد نباشد.

برای نوع‌های `input` که دامنه مقادیر ممکن آن‌ها دوره‌ای است (یعنی در بالاترین مقدار ممکن، مقادیر به جای پایان یافتن به ابتدا برمی‌گردند)، ممکن است مقادیر propertyهای [`max`](#max) و [`min`](#min) معکوس شوند، که نشان می‌دهد محدوده مقادیر مجاز از `min` شروع می‌شود، به کمترین مقدار ممکن می‌پیچد و سپس تا رسیدن به `max` ادامه می‌یابد. این ویژگی به‌ویژه برای تاریخ‌ها و زمان‌ها مفید است، مثلاً وقتی می‌خواهید محدوده از ۸ شب تا ۸ صبح باشد:

```html
<input type="time" min="20:00" max="08:00" name="overnight" />
```

attributeهای خاص و مقادیر آن‌ها می‌توانند به خطای خاصی از نوع `ValidityState` منجر شوند:

<table class="no-markdown">
  <caption>
    خطاهای شیء ValidityState به attributeهای <code>&lt;input&gt;</code> و مقادیر آن‌ها بستگی دارد:
  </caption>
  <thead>
    <tr>
      <th scope="col">Attribute (ویژگی)</th>
      <th scope="col">خاصیت مربوطه (Relevant property)</th>
      <th scope="col">توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="#max"><code>max</code></a></td>
      <td><code>validityState.rangeOverflow</code></td>
      <td>
        زمانی رخ می‌دهد که مقدار از حداکثر مقدار تعریف‌شده توسط attribute <code>max</code> بیشتر باشد.
      </td>
    </tr>
    <tr>
      <td><a href="#maxlength"><code>maxlength</code></a></td>
      <td><code>validityState.tooLong</code></td>
      <td>
        زمانی رخ می‌دهد که تعداد کاراکترها از تعداد مجاز تعریف‌شده توسط property <code>maxlength</code> بیشتر باشد.
      </td>
    </tr>
    <tr>
      <td><a href="#min"><code>min</code></a></td>
      <td><code>validityState.rangeUnderflow</code></td>
      <td>
        زمانی رخ می‌دهد که مقدار از حداقل مقدار تعریف‌شده توسط attribute <code>min</code> کمتر باشد.
      </td>
    </tr>
    <tr>
      <td><a href="#minlength"><code>minlength</code></a></td>
      <td><code>validityState.tooShort</code></td>
      <td>
        زمانی رخ می‌دهد که تعداد کاراکترها از تعداد مورد نیاز تعریف‌شده توسط property <code>minlength</code> کمتر باشد.
      </td>
    </tr>
    <tr>
      <td><a href="#pattern"><code>pattern</code></a></td>
      <td><code>validityState.patternMismatch</code></td>
      <td>
        زمانی رخ می‌دهد که یک attribute <code>pattern</code> با یک عبارت منظم معتبر وجود داشته باشد و <code>value</code> با آن مطابقت نداشته باشد.
      </td>
    </tr>
    <tr>
      <td><a href="#required"><code>required</code></a></td>
      <td><code>validityState.valueMissing</code></td>
      <td>
        زمانی رخ می‌دهد که attribute <code>required</code> وجود داشته باشد اما مقدار <code>null</code> باشد یا دکمه رادیو یا چک‌باکس علامت‌گذاری نشده باشد.
      </td>
    </tr>
    <tr>
      <td><a href="#step"><code>step</code></a></td>
      <td><code>validityState.stepMismatch</code></td>
      <td>
        مقدار با گام افزایش مطابقت ندارد. پیش‌فرض گام <code>1</code> است، بنابراین در <code>type="number"</code> اگر <code>step</code> ذکر نشود، فقط اعداد صحیح معتبر هستند. <code>step="any"</code> هرگز این خطا را ایجاد نمی‌کند.
      </td>
    </tr>
    <tr>
      <td><a href="#type"><code>type</code></a></td>
      <td><code>validityState.typeMismatch</code></td>
      <td>
        زمانی رخ می‌دهد که مقدار از نوع صحیحی نباشد، مثلاً یک ایمیل حاوی <code>@</code> نباشد یا یک URL دارای پروتکل نباشد.
      </td>
    </tr>
  </tbody>
</table>

اگر یک کنترل فرم ویژگی `required` را نداشته باشد، مقدار خالی یا رشتهٔ خالی نامعتبر (invalid) محسوب نمی‌شود. حتی اگر سایر ویژگی‌های محدودکننده (به‌جز `required`) وجود داشته باشند، رشتهٔ خالی خطایی ایجاد نمی‌کند.

می‌توانیم برای مقادیر پذیرفته‌شده محدودیت تعیین کنیم؛ مرورگرهای پشتیبانی‌شده این مقادیر را به‌صورت داخلی اعتبارسنجی می‌کنند و در صورت وجود خطا هنگام ارسال فرم به کاربر هشدار می‌دهند.

علاوه بر خطاهایی که در جدول بالا توضیح داده شد، اینترفیس `validityState` سه ویژگی boolean فقط‌خواندنی به نام‌های `badInput`، `valid` و `customError` دارد. آبجکت validity شامل موارد زیر است:

- `validityState.valueMissing`
- `validityState.typeMismatch`
- `validityState.patternMismatch`
- `validityState.tooLong`
- `validityState.tooShort`
- `validityState.rangeUnderflow`
- `validityState.rangeOverflow`
- `validityState.stepMismatch`
- `validityState.badInput`
- `validityState.valid`
- `validityState.customError`

مقدار `true` در هرکدام از این ویژگی‌های Boolean نشان می‌دهد که آن دلیل خاص برای نامعتبر بودن عنصر برقرار است. تنها استثنا ویژگی `valid` است که اگر مقدار عنصر با تمام محدودیت‌ها مطابقت داشته باشد، `true` خواهد بود.

اگر خطایی وجود داشته باشد، مرورگرهای پشتیبانی‌شده هم به کاربر هشدار می‌دهند و هم از ارسال فرم جلوگیری می‌کنند. یک نکتهٔ احتیاط: اگر پیام خطای سفارشی (custom error) روی یک مقدار truthy (هر چیزی به‌جز رشتهٔ خالی یا `null`) تنظیم شود، ارسال فرم مسدود خواهد شد. اگر پیام خطای سفارشی وجود نداشته باشد و هیچ‌کدام از ویژگی‌های دیگر `true` نباشند، `valid` برابر `true` خواهد بود و فرم قابل ارسال است.

```js
function validate(input) {
  let validityState = input.validity;
  if (validityState.valueMissing) {
    input.setCustomValidity("A value is required");
  } else if (validityState.rangeUnderflow) {
    input.setCustomValidity("Your value is too low");
  } else if (validityState.rangeOverflow) {
    input.setCustomValidity("Your value is too high");
  } else {
    input.setCustomValidity("");
  }
}
```

خط آخر که پیام اعتبارسنجی سفارشی را روی رشتهٔ خالی تنظیم می‌کند، حیاتی است. اگر کاربر خطایی مرتکب شود و پیام سفارشی تنظیم شده باشد، فرم تا وقتی که پیام به `null` تغییر نکند، حتی با مقادیر معتبر، ارسال نخواهد شد.

#### مثال خطای اعتبارسنجی سفارشی

اگر می‌خواهید وقتی یک فیلد اعتبارسنجی را رد می‌کند، پیام خطای سفارشی نمایش دهید، باید از [Constraint Validation API](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation#validating_forms_using_javascript) استفاده کنید که روی عنصر `<input>` و عناصر مرتبط در دسترس است. فرم زیر را در نظر بگیرید:

```html
<form>
  <label for="name">Enter username (upper and lowercase letters): </label>
  <input type="text" name="name" id="name" required pattern="[A-Za-z]+" />
  <button>Submit</button>
</form>
```

ویژگی‌های پایهٔ اعتبارسنجی HTML باعث می‌شوند اگر فرم را بدون مقدار یا با مقداری که با `pattern` مطابقت ندارد ارسال کنید، پیام خطای پیش‌فرض نمایش داده شود.

اگر می‌خواهید به‌جای آن پیام‌های خطای سفارشی نمایش دهید، می‌توانید از جاوااسکریپت زیر استفاده کنید:

```js
const nameInput = document.querySelector("input");

nameInput.addEventListener("input", () => {
  nameInput.setCustomValidity("");
  nameInput.checkValidity();
});

nameInput.addEventListener("invalid", () => {
  if (nameInput.value === "") {
    nameInput.setCustomValidity("Enter your username!");
  } else {
    nameInput.setCustomValidity(
      "Usernames can only contain upper and lowercase letters. Try again!",
    );
  }
});
```

ما هر بار که مقدار عنصر input تغییر می‌کند، وضعیت معتبر بودن آن را با اجرای متد `checkValidity()` در event handler رویداد `input` بررسی می‌کنیم.

اگر مقدار نامعتبر باشد، رویداد `invalid` صادر می‌شود و تابع event handler مربوط به آن اجرا می‌گردد. داخل این تابع، با استفاده از یک بلوک `if ()` تشخیص می‌دهیم که آیا مقدار به دلیل خالی بودن نامعتبر است یا به خاطر مطابقت نداشتن با pattern، و سپس یک پیام خطای اعتبارسنجی سفارشی (custom validity error message) تنظیم می‌کنیم.

در نتیجه، اگر هنگام فشردن دکمه submit مقدار input نامعتبر باشد، یکی از پیام‌های خطای سفارشی نمایش داده می‌شود.

اگر مقدار معتبر باشد، فرم همان‌طور که انتظار دارید ارسال می‌شود. برای این کار باید اعتبارسنجی سفارشی با فراخوانی `setCustomValidity()` با یک رشته خالی لغو شود. بنابراین این کار را هر بار که رویداد `input` صادر می‌شود انجام می‌دهیم. اگر این کار را انجام ندهید و قبلاً یک اعتبارسنجی سفارشی تنظیم شده باشد، input به‌عنوان نامعتبر ثبت می‌شود، حتی اگر در زمان ارسال مقدار معتبری داشته باشد.

> [!NOTE]
> همیشه محدودیت‌های ورودی را هم در سمت کلاینت و هم در سمت سرور اعتبارسنجی کنید. اعتبارسنجی محدودیت‌ها (Constraint validation) نیاز به اعتبارسنجی در _سمت سرور_ را برطرف نمی‌کند. مقادیر نامعتبر همچنان می‌توانند توسط مرورگرهای قدیمی یا افراد مخرب ارسال شوند.

> [!NOTE]
> فایرفاکس برای چندین نسخه از یک attribute اختصاصی خطا به نام `x-moz-errormessage` پشتیبانی می‌کرد که به شما اجازه می‌داد پیام‌های خطای سفارشی را به شکلی مشابه تنظیم کنید. این قابلیت از نسخه ۶۶ حذف شده است (رجوع کنید به [بگ ۱۵۱۳۸۹۰ فایرفاکس](https://bugzil.la/1513890)).

### بومی‌سازی (Localization)

ورودی‌های مجاز برای برخی از انواع `<input>` به locale بستگی دارد. در بعضی localeها عدد `1,000.00` معتبر است، در حالی که در localeهای دیگر روش معتبر وارد کردن این عدد `1.000,00` است.

فایرفاکس برای تعیین locale موردنظر جهت اعتبارسنجی ورودی کاربر (حداقل برای `type="number"`) از روش‌های اکتشافی زیر استفاده می‌کند:

- زبان مشخص‌شده توسط attribute `lang` یا `xml:lang` روی عنصر یا هر یک از والدهای آن را امتحان می‌کند.
- زبان مشخص‌شده توسط هر هدر HTTP `Content-Language` را امتحان می‌کند.
- اگر هیچ‌کدام مشخص نشده باشد، از locale مرورگر استفاده می‌کند.

## دسترس‌پذیری (Accessibility)

### برچسب‌ها (Labels)

وقتی input اضافه می‌کنید، یک الزام دسترس‌پذیری این است که برچسب (label) هم در کنار آن قرار دهید. این کار لازم است تا افرادی که از فناوری‌های کمکی استفاده می‌کنند بتوانند بفهمند input برای چیست. همچنین، کلیک کردن یا لمس کردن یک label، فوکوس را به کنترل فرم مرتبط با آن می‌دهد. این کار دسترس‌پذیری و قابلیت استفاده را برای کاربران بینا بهبود می‌بخشد و ناحیه‌ای که کاربر می‌تواند برای فعال‌سازی کنترل فرم کلیک یا لمس کند را بزرگ‌تر می‌کند. این موضوع به‌ویژه برای دکمه‌های رادیویی و چک‌باکس‌ها که کوچک هستند مفید (و حتی لازم) است. برای اطلاعات بیشتر درباره برچسب‌ها به طور کلی به [Labels](#labels) مراجعه کنید.

مثال زیر نحوه关联 `<label>` با عنصر `<input>` را به سبک بالا نشان می‌دهد. باید به `<input>` یک attribute به نام `id` بدهید. سپس `<label>` به یک attribute به نام `for` نیاز دارد که مقدارش با `id` ورودی یکسان باشد.

```html
<label for="peas">Do you like peas?</label>
<input type="checkbox" name="peas" id="peas" />
```

### اندازه (Size)

عناصر تعاملی مانند input فرم باید ناحیه‌ای به اندازه کافی بزرگ برای فعال‌سازی آسان فراهم کنند. این کار به گروه‌های مختلفی از افراد کمک می‌کند، از جمله افرادی که مشکلات کنترلی حرکتی دارند و افرادی که از ورودی‌های غیردقیق مانند قلم یا انگشت استفاده می‌کنند. حداقل اندازه تعاملی ۴۴×۴۴ [پیکسل CSS](https://w3c.github.io/wcag/guidelines/22/#dfn-css-pixels) توصیه می‌شود.

- [Understanding Success Criterion 2.5.5: Target Size | W3C Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
- [Target Size and 2.5.5 | Adrian Roselli](https://adrianroselli.com/2019/06/target-size-and-2-5-5.html)
- [Quick test: Large touch targets - The A11Y Project](https://www.a11yproject.com/posts/large-touch-targets/)

| ویژگی | توضیحات |
|-------|----------|
| **دسته‌بندی محتوا (Content categories)** | [محتوای جریانی (Flow content)](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), listed, submittable, resettable, عنصر مرتبط با فرم (form-associated element), [محتوای عبارتی (Phrasing content)](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content). اگر [`type`](#type) برابر `hidden` نباشد، عنصر قابل برچسب‌گذاری (labelable element) و محتوای لمسی (palpable content). |
| **محتوای مجاز (Permitted content)** | هیچ; این یک عنصر void است. |
| **حذف تگ (Tag omission)** | باید یک تگ شروع داشته باشد و نباید تگ پایانی داشته باشد. |
| **والدین مجاز (Permitted parents)** | هر عنصری که [محتوای عبارتی (Phrasing content)](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را می‌پذیرد. |
| **نقش ARIA ضمنی (Implicit ARIA role)** | <ul><li>`type=button`: [`button`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)</li><li>`type=checkbox`: [`checkbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)</li><li>`type=email`<ul><li>بدون attribute `list`: [`textbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)</li><li>با attribute `list`: [`combobox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)</li></ul></li><li>`type=image`: [`button`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)</li><li>`type=number`: [`spinbutton`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)</li><li>`type=radio`: [`radio`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)</li><li>`type=range`: [`slider`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)</li><li>`type=reset`: [`button`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)</li><li>`type=search`<ul><li>بدون attribute `list`: [`searchbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)</li><li>با attribute `list`: [`combobox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)</li></ul></li><li>`type=submit`: [`button`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)</li><li>`type=tel`<ul><li>بدون attribute `list`: [`textbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)</li><li>با attribute `list`: [`combobox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)</li></ul></li><li>`type=text`<ul><li>بدون attribute `list`: [`textbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)</li><li>با attribute `list`: [`combobox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)</li></ul></li><li>`type=url`<ul><li>بدون attribute `list`: [`textbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)</li><li>با attribute `list`: [`combobox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)</li></ul></li><li>`type=color|date|datetime-local|file|hidden|month|password|time|week`: [نقش متناظری وجود ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role)</li></ul> |
| **نقش‌های ARIA مجاز (Permitted ARIA roles)** | <ul><li>`type=button`: [`checkbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role), [`combobox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role), [`link`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role), [`menuitem`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role), [`menuitemcheckbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role), [`menuitemradio`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role), [`option`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role), [`radio`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role), [`switch`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role), [`tab`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)</li><li>`type=checkbox`: [`button`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) (در صورت استفاده با `aria-pressed`), [`menuitemcheckbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role), [`option`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role), [`switch`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)</li><li>`type=image`: [`link`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role), [`menuitem`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role), [`menuitemcheckbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role), [`menuitemradio`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role), [`radio`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role), [`switch`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)</li><li>`type=radio`: [`menuitemradio`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)</li><li>`type=text` بدون attribute `list`: [`combobox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role), [`searchbox`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role), [`spinbutton`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)</li><li>`type=color|date|datetime-local|email|file|hidden|month|number|password|range|reset|search|submit|tel|url|week` یا `type=text` با attribute `list`: هیچ `role` مجاز نیست</li></ul> |
| **رابط DOM (DOM interface)** | `HTMLInputElement` |

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- ویژگی CSS {{cssxref("appearance")}}
- [Your first HTML form](/en-US/docs/Learn_web_development/Extensions/Forms/Your_first_form)
- [How to structure an HTML form](/en-US/docs/Learn_web_development/Extensions/Forms/How_to_structure_a_web_form)
- [The native form widgets](/en-US/docs/Learn_web_development/Extensions/Forms/Basic_native_form_controls)
- [Sending form data](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)
- [Form constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [Styling HTML forms](/en-US/docs/Learn_web_development/Extensions/Forms/Styling_web_forms)