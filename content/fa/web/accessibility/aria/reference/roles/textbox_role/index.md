---
title: "ARIA: textbox role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: textbox role"
short-title: textbox
slug: Web/Accessibility/ARIA/Reference/Roles/textbox_role
page-type: aria-role
sidebar: accessibilitysidebar
---

نقش `textbox` برای شناسایی عنصری استفاده می‌شود که امکان ورود متن آزاد را فراهم می‌کند. در صورت امکان، به جای استفاده از این نقش، از عنصر {{HTMLElement("input")}} با [type="text"](/en-US/docs/Web/HTML/Reference/Elements/input/text) برای ورودی تک‌خطی، یا از عنصر {{HTMLElement("textarea")}} برای ورودی چندخطی استفاده کنید.

## توضیحات

وقتی عنصری نقش `textbox` را داشته باشد، مرورگر یک رویداد textbox قابل دسترس به فناوری‌های کمکی می‌فرستد که می‌توانند کاربر را از آن مطلع کنند.

حالت پیش‌فرض یک ورودی تک‌خطی است که در آن کلیدهای <kbd>Return</kbd> یا <kbd>Enter</kbd> فرم را ارسال می‌کنند؛ در این حالت ترجیحاً از HTML {{HTMLElement("input")}} با `type="text"` استفاده کنید. برای ایجاد یک جعبه متن چندخطی که از شکست خط پشتیبانی می‌کند، مانند HTML {{HTMLElement("textarea")}}، ویژگی `aria-multiline="true"` را تنظیم کنید. افزودن ویژگی HTML `contenteditable` اطمینان می‌دهد که گره متنی قابل ویرایش است.

```html
<!-- فیلد ورود متن -->
<div id="txtboxLabel">کد پستی پنج‌رقمی خود را وارد کنید</div>
<div
  role="textbox"
  contenteditable="true"
  aria-placeholder="کد پستی پنج‌رقمی"
  aria-labelledby="txtboxLabel"></div>

<!-- ناحیه متن چندخطی -->
<div id="txtboxMultilineLabel">برچسب‌های مقاله را وارد کنید</div>
<div
  role="textbox"
  contenteditable="true"
  aria-multiline="true"
  aria-labelledby="txtboxMultilineLabel"
  aria-required="true"></div>
```

عناصر معنایی مختصرتر هستند و برای پشتیبانی از ویژگی‌های textbox به جاوااسکریپت نیاز ندارند.

```html
<label for="txtbox">کد پستی پنج‌رقمی خود را وارد کنید</label>
<input type="text" placeholder="کد پستی پنج‌رقمی" id="txtbox" />

<!-- ناحیه متن چندخطی -->
<label for="txtboxMultiline">برچسب‌های مقاله را وارد کنید</label>
<textarea id="txtboxMultiline" required></textarea>
```

در جایی که فیلد متنی فقط‌خواندنی است، این موضوع را با تنظیم `aria-readonly="true"` روی عنصر مشخص کنید.

### ویژگی‌های ARIA مرتبط

- ویژگی [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant)
  - : با گرفتن مقدار شناسه عنصری که یا فرزند عنصر دارای فوکوس DOM است یا فرزند منطقی است که با ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) مشخص شده، نشان می‌دهد که آن عنصر چه زمانی فوکوس دارد، وقتی بخشی از یک ابزارک ترکیبی مانند [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role) است. به عنوان مثال، در یک combobox، فوکوس ممکن است روی textbox باقی بماند در حالی که مقدار `aria-activedescendant` روی عنصر textbox به فرزندی از listbox بازشو که توسط textbox کنترل می‌شود اشاره دارد. این ویژگی باید با تغییر فوکوس به صورت برنامه‌نویسی به‌روزرسانی شود.
- ویژگی [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete)
  - : نشان می‌دهد که آیا و چگونه ورودی کاربر در فیلد می‌تواند نمایش پیش‌بینی مقدار مورد نظر را فعال کند. این ویژگی مقادیر زیر را پشتیبانی می‌کند:
    - `inline`: متن پیش‌بینی‌شده بعد از مکان‌نما درج می‌شود.
    - `list`: متن پیش‌بینی‌شده به صورت مجموعه‌ای از مقادیر ارائه می‌شود.
    - `both`: متن پیش‌بینی‌شده به صورت مجموعه‌ای از مقادیر ارائه می‌شود، همراه با متنی که برای تکمیل یک مقدار لازم است و بعد از مکان‌نما درج می‌شود.
    - `none` (پیش‌فرض): متن پیش‌بینی‌شده ارائه نمی‌شود.

    اگر مقدار `list` یا `both` تنظیم شده باشد، ویژگی‌های [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) و [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) نیز باید شامل شوند. مقدار `aria-controls` شناسه عنصری است که فهرست مقادیر پیشنهادی را در بر می‌گیرد. علاوه بر این، یا خود textbox یا یک عنصر شامل با نقش `combobox` دارای مقدار `aria-haspopup` است که با نقش عنصر حاوی فهرست مقادیر پیشنهادی مطابقت دارد.

- ویژگی [`aria-multiline`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiline)
  - : اگر `aria-multiline="true"` تنظیم شود، فناوری کمکی به کاربر اطلاع می‌دهد که textbox از ورودی چندخطی پشتیبانی می‌کند، با این انتظار که کلیدهای <kbd>Enter</kbd> یا <kbd>Return</kbd> یک شکست خط ایجاد کنند نه ارسال فرم. ARIA رفتار عنصر را تغییر نمی‌دهد؛ بلکه این ویژگی باید توسط توسعه‌دهنده کنترل شود. اگر مقدار false تنظیم شود، یا ویژگی حذف شود و پیش‌فرض false باشد، انتظار کاربر این است که کنترل یک جعبه متن تک‌خطی است و کلیدهای <kbd>Enter</kbd> یا <kbd>Return</kbd> فرم را ارسال می‌کنند.

- ویژگی [`aria-placeholder`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-placeholder)
  - : نشان‌دهنده یک راهنما (کلمه یا عبارت) برای کاربر درباره آنچه باید در فیلد متنی وارد کند است. راهنما باید یک مقدار نمونه یا توضیح کوتاهی از قالب مورد انتظار باشد. این اطلاعات نباید به عنوان جایگزینی برای برچسب استفاده شود: برچسب قابل فوکوس، دائمی است، نوع اطلاعات مورد انتظار را نشان می‌دهد و ناحیه ضربه را برای تنظیم فوکوس روی کنترل افزایش می‌دهد، در حالی که متن placeholder فقط یک راهنمای موقت درباره مقدار مورد انتظار است که اگر به اشتباه پیاده‌سازی شود می‌تواند دسترس‌پذیری را کاهش دهد. placeholder باید زمانی قابل مشاهده باشد که مقدار کنترل رشته خالی است، مانند زمانی که کنترل برای اولین بار فوکوس می‌گیرد و زمانی که کاربران مقدار قبلاً وارد شده را حذف می‌کنند. به جای استفاده از `aria-placeholder`، از عنصر معنایی `<input type="text">` یا `<textarea>` با ویژگی `placeholder` استفاده کنید.
- ویژگی [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly)
  - : نشان می‌دهد که کاربر نمی‌تواند مقدار فیلد متن را تغییر دهد. به جای استفاده از `aria-readonly`، از عنصر معنایی `<input type="text">` یا `<textarea>` با ویژگی `readonly` استفاده کنید.
- ویژگی [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required)
  - : نشان می‌دهد که قبل از ارسال فرم باید مقداری برای فیلد فراهم شود. به جای استفاده از `aria-required`، از عنصر معنایی `<input type="text">` یا `<textarea>` با ویژگی `required` استفاده کنید.

### تعاملات صفحه‌کلید

در استفاده تک‌خطی (زمانی که `aria-multiline` برابر `false` است یا استفاده نشده)، کلید Return یا Enter فرم را ارسال می‌کند. در استفاده چندخطی (زمانی که `aria-multiline` برابر `true` است)، کلید Return یا Enter یک شکست خط درج می‌کند.

### قابلیت‌های جاوااسکریپت

همه ویژگی‌های مرتبط با هر یک از ویژگی‌ها و حالت‌ها باید حفظ شوند و ارسال فرم با فشردن enter یا return در یک textbox تک‌خطی باید مدیریت شود.

- مدیریت رویداد فوکوس و ویژگی aria-activedescendant
  - : اگر در حال پیاده‌سازی یک ابزارک ترکیبی، مانند combobox متشکل از یک جعبه متن و یک listbox هستید، باید ویژگی `aria-activedescendant` را با استفاده از یک مدیریت‌کننده مدیریت کنید. قبل از استفاده از این تکنیک، اطمینان حاصل کنید که مرورگرهایی که باید هدف قرار دهید، در حال حاضر از آن پشتیبانی می‌کنند. برای اطلاعات بیشتر به [مشخصات aria-descendant](https://w3c.github.io/aria/#aria-activedescendant) مراجعه کنید.

> [!NOTE]
> استفاده از عنصر {{HTMLElement("input")}} با type="text" یا عنصر {{HTMLElement("textarea")}} به جای نقش textbox آرایی، روش بهتری است. هنگام استفاده از هر یک از عناصر معنایی، نقش textbox آرایی لازم نیست. به [یادداشت‌هایی درباره استفاده از ARIA در HTML](https://w3c.github.io/using-aria/) مراجعه کنید.

## اثرات احتمالی بر عوامل کاربر و فناوری کمکی

وقتی نقش `textbox` به یک عنصر اضافه می‌شود، یا چنین عنصری قابل مشاهده می‌شود، عامل کاربر باید کارهای زیر را انجام دهد:

- عنصر را به عنوان یک عنصر با نقش textbox در API دسترس‌پذیری سیستم عامل نمایش دهد.
- اگر API دسترس‌پذیری سیستم عامل از آن پشتیبانی می‌کند، یک رویداد textbox قابل دسترس با استفاده از آن API ارسال کند.

محصولات فناوری کمکی باید به چنین رویدادی گوش دهند و کاربر را مطابق آن مطلع کنند:

- صفحه‌خوان‌ها باید برچسب و نقش آن را وقتی فوکوس برای اولین بار روی یک textbox قرار می‌گیرد اعلام کنند. اگر همچنین محتوایی داشته باشد، باید مانند یک textbox معمولی اعلام شود.
- بزرگ‌نمایی‌گرهای صفحه ممکن است textbox را بزرگ کنند.

> [!NOTE]
> ممکن است نظرات در مورد نحوه مدیریت این تکنیک توسط فناوری کمکی متفاوت باشد. اطلاعات ارائه شده در بالا یکی از این نظرات است و ممکن است تجربه متفاوتی داشته باشد.

## مثال‌ها

### مثال ۱: افزودن نقش در کد HTML برای ورودی تک‌خطی

قطعه کد زیر نشان می‌دهد که چگونه نقش textbox مستقیماً در کد منبع HTML اضافه می‌شود.

```html
<div role="textbox" contenteditable="true"></div>
```

### مثال ۲: افزودن نقش در کد HTML برای ورودی چندخطی

قطعه کد زیر نشان می‌دهد که چگونه نقش textbox مستقیماً در کد منبع HTML اضافه می‌شود.

```html
<div role="textbox" contenteditable="true" aria-multiline="true"></div>
```

## بهترین روش‌ها

حتماً ویژگی `contenteditable="true"` را به عنصر HTML که این نقش روی آن اعمال می‌شود اضافه کنید. این کار را حتی اگر `aria-readonly` را روی `true` تنظیم کرده‌اید انجام دهید؛ به این ترتیب، شما منتقل می‌کنید که محتوا اگر فقط‌خواندنی نبود، قابل ویرایش می‌بود.

## همچنین ببینید

- [ARIA: نقش search](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)