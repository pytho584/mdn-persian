---
title: "ARIA: listbox role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: listbox role"
short-title: listbox
slug: Web/Accessibility/ARIA/Reference/Roles/listbox_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#listbox
  - https://www.w3.org/WAI/ARIA/apg/patterns/listbox/examples/listbox-scrollable/
sidebar: accessibilitysidebar
---

نقش `listbox` برای فهرست‌هایی استفاده می‌شود که کاربر می‌تواند یک یا چند آیتم ثابت را از آن‌ها انتخاب کند و بر خلاف عناصر HTML {{HTMLElement('select')}}، ممکن است شامل تصاویر باشند.

## توضیحات

نقش `listbox` برای شناسایی عنصری استفاده می‌شود که یک فهرست ایجاد می‌کند که کاربر می‌تواند یک یا چند آیتم ثابت را از آن انتخاب کند، مشابه عنصر HTML {{HTMLElement('select')}}. برخلاف {{HTMLElement('select')}}، یک listbox می‌تواند شامل تصاویر باشد. Listboxها شامل فرزندانی با نقش [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role) یا عناصری با نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) هستند که به نوبه خود شامل فرزندانی با نقش `option` می‌باشند.

به شدت توصیه می‌شود از عنصر select HTML، یا یک گروه دکمه رادیویی در صورت امکان انتخاب تنها یک آیتم، یا یک گروه چک‌باکس در صورت امکان انتخاب چند آیتم استفاده کنید، زیرا تعاملات صفحه‌کلید زیادی برای مدیریت فوکوس همه فرزندان وجود دارد و عناصر بومی HTML این قابلیت را به صورت رایگان در اختیار شما قرار می‌دهند.

عناصر با نقش `listbox` دارای مقدار ضمنی [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) برابر با `vertical` هستند.

هنگامی که یک فهرست با Tab فوکوس می‌شود، اولین آیتم در فهرست در صورت عدم انتخاب قبلی، انتخاب خواهد شد. کلیدهای بالا/پایین در فهرست حرکت می‌کنند و فشار دادن Shift + بالا/پایین باعث حرکت و گسترش انتخاب می‌شود. تایپ یک یا چند حرف در آیتم‌های فهرست حرکت می‌کند (همان حرف به هر آیتمی که با آن شروع می‌شود می‌رود، حروف مختلف به اولین آیتمی که با آن رشته کامل شروع می‌شود می‌روند). اگر آیتم فعلی دارای یک منوی زمینه مرتبط باشد، Shift+F10 آن منو را راه‌اندازی می‌کند. اگر آیتم‌های فهرست قابل علامت‌گذاری باشند، می‌توان از Space برای تغییر وضعیت [چک‌باکس‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role) استفاده کرد. برای آیتم‌های فهرست قابل انتخاب، Space انتخاب آن‌ها را تغییر می‌دهد، Shift+Space برای انتخاب آیتم‌های متوالی استفاده می‌شود، Ctrl+Arrow بدون انتخاب حرکت می‌کند و Ctrl+Space برای انتخاب آیتم‌های غیرمتوالی استفاده می‌شود. توصیه می‌شود از یک چک‌باکس، پیوند یا روش دیگر برای انتخاب همه آیتم‌ها استفاده شود و Ctrl+A می‌تواند به عنوان کلید میانبر این کار استفاده شود.

هنگامی که نقش listbox به یک عنصر اضافه می‌شود یا چنین عنصری قابل مشاهده می‌شود، صفحه‌خوان‌ها برچسب و نقش listbox را هنگامی که فوکوس می‌گیرد اعلام می‌کنند. اگر یک گزینه یا آیتم در داخل فهرست فوکوس شود، پس از آن اعلام می‌شود و به دنبال آن موقعیت آیتم در فهرست (در صورت پشتیبانی صفحه‌خوان) اعلام می‌شود. با حرکت فوکوس در داخل فهرست، صفحه‌خوان آیتم‌های مربوطه را اعلام می‌کند.

### نقش‌ها، حالات و ویژگی‌های ARIA مرتبط

#### نقش‌های مرتبط

- نقش [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
  - : یک یا چند گزینه تو در تو الزامی است. تمام گزینه‌های انتخاب شده دارای [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) برابر با `true` هستند. تمام گزینه‌هایی که انتخاب نشده‌اند دارای [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) برابر با `false` هستند. اگر یک گزینه قابل انتخاب نباشد، [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) را حذف کنید.
- نقش [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)
  - : بخشی که شامل عناصر `listitem` است.

#### حالات و ویژگی‌ها

- [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant)
  - : رشته `id` عنصر فعال فعلی در داخل listbox را نگه می‌دارد. اگر آن یک عنصر گزینه باشد، آنگاه این `id` گزینه‌ای است که آخرین بار با آن تعامل شده است، صرف نظر از اینکه آن گزینه دارای مقدار [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) برابر با `true` باشد یا نه. فقط مقدار یک `id` را می‌گیرد، حتی در یک listbox چند انتخابی. اگر `id` به یک فرزند DOM از listbox اشاره نکند، آنگاه آن `id` باید در میان شناسه‌های موجود در ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) گنجانده شود.
- [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns)
  - : این یک فهرست جدا شده با فاصله از شناسه‌های عناصری است که فرزندان DOM listbox نیستند. شناسه‌های ذکر شده در اینجا نمی‌توانند در ویژگی‌های [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) هیچ عنصر دیگری نیز ذکر شوند.

- [`aria-multiselectable`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable)
  - : اگر کاربر می‌تواند بیش از یک گزینه را انتخاب کند، آن را به `true` تنظیم کنید. اگر `true` تنظیم شود، _هر_ گزینه قابل انتخاب باید دارای ویژگی [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) باشد که به `true` یا `false` تنظیم شده است. گزینه‌هایی که _قابل انتخاب نیستند_ _نباید_ ویژگی [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) را داشته باشند. اگر `false` باشد یا حذف شود، فقط گزینه‌ای که در حال حاضر انتخاب شده است (در صورت انتخاب شدن) نیاز به ویژگی [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) دارد و باید `true` تنظیم شود.

- [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required)
  - : یک ویژگی بولی که نشان می‌دهد یک گزینه با مقدار رشته غیر خالی باید انتخاب شود.

- [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly)
  - : کاربر نمی‌تواند تغییر دهد که کدام گزینه‌ها انتخاب یا لغو انتخاب شده‌اند، اما listbox در غیر این صورت قابل استفاده است.

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : یک مقدار رشته‌ای قابل خواندن توسط انسان که listbox را شناسایی می‌کند. اگر یک برچسب قابل مشاهده وجود دارد، باید به جای آن از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای اشاره به آن برچسب استفاده شود.

- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : عنصر یا عناصر قابل مشاهده را در یک فهرست جدا شده با فاصله از شناسه‌های عناصری که listbox را شناسایی می‌کنند، مشخص می‌کند. اگر برچسب قابل مشاهده‌ای وجود ندارد، باید به جای آن از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) برای گنجاندن یک برچسب استفاده شود. (توجه: "labelled" با دو "L" املای صحیح بر اساس قراردادهای API دسترسی‌پذیری است.)

- [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription)
  - : یک مقدار رشته‌ای قابل خواندن توسط انسان که نقش listbox را واضح‌تر شناسایی می‌کند. صفحه‌خوان‌ها اغلب این مقدار را پس از خواندن برچسب (در صورت وجود) به جای گفتن "listbox" برای کاربر می‌خوانند.

### تعاملات صفحه‌کلید

- هنگامی که یک listbox تک انتخابی فوکوس دریافت می‌کند:
  - اگر هیچ یک از گزینه‌ها قبل از دریافت فوکوس listbox انتخاب نشده باشند، اولین گزینه فوکوس دریافت می‌کند. به صورت اختیاری، ممکن است اولین گزینه به طور خودکار انتخاب شود.
  - اگر یک گزینه قبل از دریافت فوکوس listbox انتخاب شده باشد، فوکوس روی گزینه انتخاب شده تنظیم می‌شود.

- هنگامی که یک listbox چند انتخابی فوکوس دریافت می‌کند:
  - اگر هیچ یک از گزینه‌ها قبل از دریافت فوکوس listbox انتخاب نشده باشند، فوکوس روی اولین گزینه تنظیم می‌شود و هیچ تغییر خودکاری در حالت انتخاب وجود ندارد.
  - اگر یک یا چند گزینه قبل از دریافت فوکوس listbox انتخاب شده باشند، فوکوس روی اولین گزینه در فهرست که انتخاب شده است تنظیم می‌شود.

- <kbd>پیکان پایین</kbd>

  : فوکوس را به گزینه بعدی منتقل می‌کند. به صورت اختیاری، در یک listbox تک انتخابی، انتخاب ممکن است همراه با فوکوس حرکت کند.

- <kbd>پیکان بالا</kbd>

  : فوکوس را به گزینه قبلی منتقل می‌کند. به صورت اختیاری، در یک listbox تک انتخابی، انتخاب ممکن است همراه با فوکوس حرکت کند.

- <kbd>Home</kbd>

  (اختیاری): فوکوس را به اولین گزینه منتقل می‌کند. به صورت اختیاری، در یک listbox تک انتخابی، انتخاب ممکن است همراه با فوکوس حرکت کند. پشتیبانی از این کلید برای فهرست‌هایی با بیش از پنج گزینه به شدت توصیه می‌شود.

- <kbd>End</kbd>

  (اختیاری): فوکوس را به آخرین گزینه منتقل می‌کند. به صورت اختیاری، در یک listbox تک انتخابی، انتخاب ممکن است همراه با فوکوس حرکت کند. پشتیبانی از این کلید برای فهرست‌هایی با بیش از پنج گزینه به شدت توصیه می‌شود.

- تایپ پیش‌رو برای همه listboxها به ویژه آن‌هایی که بیش از هفت گزینه دارند توصیه می‌شود:
  - یک کاراکتر تایپ کنید: فوکوس به آیتم بعدی با نامی که با آن کاراکتر شروع می‌شود منتقل می‌شود.
  - چند کاراکتر را به سرعت تایپ کنید: فوکوس به آیتم بعدی با نامی که با رشته کاراکترهای تایپ شده شروع می‌شود منتقل می‌شود.

- **انتخاب چندگانه**: نویسندگان می‌توانند یکی از دو مدل تعامل را برای پشتیبانی از انتخاب چندگانه پیاده‌سازی کنند: یک مدل توصیه شده که نیازی به نگه داشتن کلید اصلاح‌کننده مانند <kbd>Shift</kbd> یا <kbd>Control</kbd> در حین پیمایش فهرست ندارد، یا یک مدل جایگزین که نیاز به نگه داشتن کلیدهای اصلاح‌کننده در حین پیمایش برای جلوگیری از از دست رفتن حالت‌های انتخاب دارد.
  - مدل انتخاب توصیه شده — نگه داشتن کلیدهای اصلاح‌کننده ضروری نیست:
    - <kbd>Space</kbd>: حالت انتخاب گزینه فوکوس شده را تغییر می‌دهد.
    - <kbd>Shift + پیکان پایین</kbd> (اختیاری): فوکوس را به گزینه بعدی منتقل می‌کند و حالت انتخاب آن را تغییر می‌دهد.
    - <kbd>Shift + پیکان بالا</kbd> (اختیاری): فوکوس را به گزینه قبلی منتقل می‌کند و حالت انتخاب آن را تغییر می‌دهد.
    - <kbd>Shift + Space</kbd> (اختیاری): آیتم‌های متوالی از آخرین آیتم انتخاب شده تا آیتم فوکوس شده را انتخاب می‌کند.
    - <kbd>Control + Shift + Home</kbd> (اختیاری): گزینه فوکوس شده و تمام گزینه‌های تا اولین گزینه را انتخاب می‌کند. به صورت اختیاری، فوکوس را به اولین گزینه منتقل می‌کند.
    - <kbd>Control + Shift + End</kbd> (اختیاری): گزینه فوکوس شده و تمام گزینه‌های تا آخرین گزینه را انتخاب می‌کند. به صورت اختیاری، فوکوس را به آخرین گزینه منتقل می‌کند.
    - <kbd>Control + A</kbd> (اختیاری): تمام گزینه‌های موجود در فهرست را انتخاب می‌کند. به صورت اختیاری، اگر همه گزینه‌ها انتخاب شده باشند، ممکن است همه گزینه‌ها را نیز لغو انتخاب کند.

### ویژگی‌های جاوااسکریپت مورد نیاز

#### انتخاب یک گزینه در یک listbox تک انتخابی

هنگامی که کاربر یک گزینه را انتخاب می‌کند، موارد زیر باید رخ دهد:

1. گزینه قبلی انتخاب شده را لغو انتخاب کنید، [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) را به `false` تنظیم کنید یا ویژگی را به طور کلی حذف کنید، و ظاهر گزینه جدیداً لغو انتخاب شده را به حالت انتخاب نشده تغییر دهید.
2. گزینه جدیداً انتخاب شده را انتخاب کنید، `aria-selected="true"` را روی گزینه تنظیم کنید و ظاهر گزینه جدیداً انتخاب شده را به حالت انتخاب شده تغییر دهید.
3. مقدار [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) را در listbox به شناسه گزینه جدیداً انتخاب شده به‌روزرسانی کنید.
4. به صورت بصری حالت‌های محو شدن، فوکوس و انتخاب گزینه را مدیریت کنید.

#### تغییر وضعیت یک گزینه در یک listbox چند انتخابی

هنگامی که کاربر روی یک گزینه کلیک می‌کند، هنگامی که روی یک گزینه فوکوس شده است <kbd>Space</kbd> را فشار می‌دهد، یا به روش دیگری وضعیت یک گزینه را تغییر می‌دهد، موارد زیر باید رخ دهد:

1. حالت [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) گزینه فعلی فوکوس شده را تغییر دهید، حالت `aria-selected` را اگر `false` بود به `true` یا اگر `true` بود به `false` تغییر دهید.
2. ظاهر گزینه را برای منعکس کردن حالت انتخاب آن تغییر دهید.
3. مقدار [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) را در listbox به شناسه گزینه‌ای که کاربر با آن تعامل داشته است به‌روزرسانی کنید، حتی اگر گزینه را به حالت لغو انتخاب تغییر داده باشد.

> [!NOTE]
> اولین قانون استفاده از ARIA این است که اگر می‌توانید از یک ویژگی بومی با معناشناسی و رفتاری که از قبل نیاز دارید استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای دسترسی‌پذیر کردن آن، این کار را انجام دهید. عنصر {{HTMLElement('select')}} با عناصر فرزند {{HTMLElement('option')}} تمام تعاملات مورد نیاز را به صورت بومی مدیریت می‌کند.

## مثال‌ها

### مثال ۱: یک listbox تک انتخابی که از `aria-activedescendant` استفاده می‌کند

قطعه کد زیر، با استفاده از [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant)، نشان می‌دهد که چگونه نقش listbox مستقیماً به کد منبع HTML اضافه می‌شود.

```html
<p id="listbox1label" role="label">Select a color:</p>
<div
  role="listbox"
  tabindex="0"
  id="listbox1"
  aria-labelledby="listbox1label"
  aria-activedescendant="listbox1-1">
  <div role="option" id="listbox1-1" class="selected" aria-selected="true">
    Green
  </div>
  <div role="option" id="listbox1-2">Orange</div>
  <div role="option" id="listbox1-3">Red</div>
  <div role="option" id="listbox1-4">Blue</div>
  <div role="option" id="listbox1-5">Violet</div>
  <div role="option" id="listbox1-6">Periwinkle</div>
</div>
```

```js
const listbox = document.getElementById("listbox1");
listbox.addEventListener("click", listItemClick);
listbox.addEventListener("keydown", listItemKeyEvent);
listbox.addEventListener("keypress", listItemKeyEvent);
```

این می‌توانست به راحتی با عناصر بومی HTML {{HTMLElement('select')}} و {{HTMLElement('label')}} مدیریت شود.

```html
<label for="listbox1">Select a color:</label>
<select id="listbox1">
  <option selected>Green</option>
  <option>Orange</option>
  <option>Red</option>
  <option>Blue</option>
  <option>Violet</option>
  <option>Periwinkle</option>
</select>
```

### مثال‌های بیشتر

- [مثال Listbox قابل پیمایش](https://www.w3.org/WAI/ARIA/apg/patterns/listbox/examples/listbox-scrollable/): listbox تک انتخابی که برای نمایش گزینه‌های بیشتر پیمایش می‌کند، مشابه HTML {{HTMLElement('select')}} با ویژگی `size` بزرگتر از یک.
- [مثال Listbox با گزینه‌های گروه‌بندی شده](https://www.w3.org/WAI/ARIA/apg/patterns/listbox/examples/listbox-grouped/): listbox تک انتخابی با گزینه‌های گروه‌بندی شده، مشابه HTML {{HTMLElement('select')}} با ویژگی `size` تنظیم شده به بزرگتر از `"1"` و گزینه‌های گروه‌بندی شده با عناصر `optgroup`.
- [مثال‌های Listbox با گزینه‌های قابل چیدمان مجدد](https://www.w3.org/WAI/ARIA/apg/patterns/listbox/examples/listbox-rearrangeable/): مثال‌هایی از listboxهای تک انتخابی و چند انتخابی با نوار ابزار همراه که در آن گزینه‌ها می‌توانند اضافه، جابه‌جا و حذف شوند.

## بهترین روش‌ها

- برای دسترسی‌پذیری صفحه‌کلید، نویسندگان باید [فوکوس](https://w3c.github.io/aria/#managingfocus) همه فرزندان این نقش را مدیریت کنند.
- توصیه می‌شود نویسندگان از سبک‌بندی متفاوت برای انتخاب زمانی که فهرست فوکوس ندارد استفاده کنند، به عنوان مثال، یک انتخاب غیرفعال اغلب با رنگ پس‌زمینه روشن‌تر نشان داده می‌شود.
- اگر listbox بخشی از یک ویجت دیگر نیست، باید ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) را تنظیم کند.
- اگر یک یا چند ورودی فرزندان DOM listbox نیستند، ویژگی‌های اضافی `aria-*` باید تنظیم شوند (به [بهترین روش‌های ARIA](https://www.w3.org/WAI/ARIA/apg/patterns/listbox/) مراجعه کنید).
- اگر دلیل معتبری برای [باز کردن](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) listbox وجود دارد، نقش [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role) ممکن است مناسب‌تر باشد.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement('select')}}
- عنصر HTML {{HTMLElement('label')}}
- عنصر HTML {{HTMLElement('option')}}
- [ARIA: نقش `combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [ARIA: نقش `option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
- [ARIA: نقش `list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)
- [ARIA: نقش `listitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role)
- [بهترین روش‌های ARIA – Listbox](https://www.w3.org/WAI/ARIA/apg/patterns/listbox/)