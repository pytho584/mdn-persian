---
title: "Global attributes"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes"
translated_by: "n8n + AI"
---

**Global attributes** attributeهایی هستند که در تمام عناصر HTML مشترکند؛ می‌توان از آن‌ها روی هر عنصری استفاده کرد، هرچند ممکن است روی برخی عناصر تأثیری نداشته باشند.

Global attributes را می‌توان روی تمام [عناصر HTML](/en-US/docs/Web/HTML/Reference/Elements) اعمال کرد، _حتی آن‌هایی که در استاندارد تعریف نشده‌اند_. یعنی هر عنصر غیراستاندارد هم باید این attributeها را قبول کند، هرچند استفاده از آن عناصر باعث می‌شود سند دیگر با HTML5 سازگار نباشد. مثلاً مرورگرهای سازگار با HTML5 محتوایی را که با `<foo hidden>…</foo>` مشخص شده پنهان می‌کنند، حتی اگر `<foo>` یک عنصر معتبر HTML نباشد.

علاوه بر global attributes پایه HTML، attributeهای سراسری زیر نیز وجود دارند:

- `xml:lang` و `xml:base` — این‌ها از مشخصات XHTML به ارث رسیده و منسوخ شده‌اند، اما به دلایل سازگاری نگه داشته شده‌اند.
- attribute [`role`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) مربوط به ARIA و چندین حالت و ویژگی [`aria-*`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes) که برای دسترسی‌پذیری (accessibility) استفاده می‌شوند.
- [attributeهای مدیریت رویداد (event handler)](#list_of_global_event_handler_attributes) که در ادامه فهرست شده‌اند.

## فهرست global attributes

- [`accesskey`](/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey)
  - : راهنمایی برای ایجاد یک میانبر صفحه‌کلید برای عنصر جاری فراهم می‌کند. این attribute شامل فهرستی از کاراکترها است که با فاصله از هم جدا شده‌اند. مرورگر باید اولین کاراکتری را که در چیدمان صفحه‌کلید وجود دارد استفاده کند.
- [`anchor`](/en-US/docs/Web/HTML/Reference/Global_attributes/anchor)
  - : یک عنصر موقعیت‌یاب (positioned element) را به یک عنصر لنگر (anchor element) متصل می‌کند. مقدار این attribute برابر [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) عنصری است که می‌خواهید عنصر موقعیت‌یاب به آن لنگر شود. سپس می‌توان عنصر را [با استفاده از CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using) موقعیت‌یابی کرد.
- [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize)
  - : مشخص می‌کند که آیا متن ورودی به‌طور خودکار با حرف بزرگ شروع شود یا خیر، و اگر بله، به چه صورت.
- [`autocorrect`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect)
  - : کنترل می‌کند که آیا متن ورودی به‌طور خودکار برای اشتباهات املایی تصحیح شود یا خیر. این attribute را می‌توان روی عناصری که متن قابل ویرایش دارند اعمال کرد، به جز عناصر `<input>` با attribute از نوع [`type="password"`](/en-US/docs/Web/HTML/Reference/Elements/input/password), [`type="email"`](/en-US/docs/Web/HTML/Reference/Elements/input/email) یا [`type="url"`](/en-US/docs/Web/HTML/Reference/Elements/input/url).
- [`autofocus`](/en-US/docs/Web/HTML/Reference/Global_attributes/autofocus)
  - : نشان می‌دهد که یک عنصر باید هنگام بارگذاری صفحه یا به محض نمایش `<dialog>`ای که عضوی از آن است، فوکس بگیرد. این attribute از نوع boolean است و مقدار پیش‌فرض false.
- [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class)
  - : فهرستی از کلاس‌های عنصر که با فاصله از هم جدا شده‌اند. کلاس‌ها به CSS و JavaScript اجازه می‌دهند عناصر خاصی را از طریق [class selectors](/en-US/docs/Web/CSS/Reference/Selectors/Class_selectors) یا توابعی مانند متد `Document.getElementsByClassName()` انتخاب و به آن‌ها دسترسی پیدا کنند.
- [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable)
  - : یک attribute از نوع [enumerated](/en-US/docs/Glossary/Enumerated) که مشخص می‌کند آیا عنصر باید توسط کاربر قابل ویرایش باشد یا خیر. اگر چنین باشد، مرورگر ویجت خود را تغییر می‌دهد تا ویرایش امکان‌پذیر شود. این attribute باید یکی از مقادیر زیر را بگیرد:
    - `true` یا _رشته خالی_ که نشان می‌دهد عنصر باید قابل ویرایش باشد.
    - `false` که نشان می‌دهد عنصر نباید قابل ویرایش باشد.
    - `plaintext-only` که نشان می‌دهد متن خام عنصر قابل ویرایش است، اما قالب‌بندی rich text غیرفعال است.

- [`data-*`](/en-US/docs/Web/HTML/Reference/Global_attributes/data-*)
  - : دستهای از ویژگیها به نام ویژگی‌های داده سفارشی (custom data attributes) می‌سازند که امکان تبادل اطلاعات اختصاصی بین [HTML](/en-US/docs/Web/HTML) و نمایش {{glossary("DOM")}} آن را فراهم می‌کنند و اسکریپت‌ها می‌توانند از آن‌ها استفاده کنند. همه این داده‌های سفارشی از طریق رابط {{DOMxRef("HTMLElement")}} عنصری که ویژگی روی آن تنظیم شده در دسترس هستند. خاصیت {{DOMxRef("HTMLElement.dataset")}} به آن‌ها دسترسی می‌دهد.
- [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir)
  - : یک ویژگی شمارشی (enumerated) که جهت‌گیری متن عنصر را مشخص می‌کند. می‌تواند مقادیر زیر را داشته باشد:
    - `ltr` به معنی _چپ به راست_ است و برای زبان‌هایی استفاده می‌شود که از چپ به راست نوشته می‌شوند (مانند انگلیسی)؛
    - `rtl` به معنی _راست به چپ_ است و برای زبان‌هایی استفاده می‌شود که از راست به چپ نوشته می‌شوند (مانند عربی)؛
    - `auto` که تصمیم را به عامل کاربر (user agent) می‌سپارد. یک الگوریتم ساده استفاده می‌کند و کاراکترهای داخل عنصر را تجزیه می‌کند تا به کاراکتری با جهت‌گیری قوی برسد، سپس همان جهت‌گیری را به کل عنصر اعمال می‌کند.
- [`draggable`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable)
  - : یک ویژگی شمارشی که مشخص می‌کند آیا می‌توان عنصر را با استفاده از [Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API) کشید. می‌تواند مقادیر زیر را داشته باشد:
    - `true` یعنی عنصر قابل کشیدن است؛
    - `false` یعنی عنصر قابل کشیدن نیست.
- [`enterkeyhint`](/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint)
  - : راهنمایی برای این‌که چه برچسب یا نمادی برای کلید Enter در صفحه‌کلیدهای مجازی نمایش داده شود.
- [`exportparts`](/en-US/docs/Web/HTML/Reference/Global_attributes/exportparts)
  - : برای صادر کردن انتقالی (transitively) بخش‌های shadow از یک درخت shadow تو در تو به درخت light دربرگیرنده استفاده می‌شود.
- [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden)
  - : یک ویژگی شمارشی که نشان می‌دهد عنصر هنوز یا دیگر _مرتبط_ نیست. مثلاً می‌توان از آن برای پنهان کردن عناصری از صفحه استفاده کرد که تا تکمیل فرایند ورود به سیستم قابل استفاده نیستند. مرورگر چنین عناصری را رندر نمی‌کند. این ویژگی نباید برای پنهان کردن محتوایی استفاده شود که به‌طور مشروع قابل نمایش است.
- [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id)
  - : یک شناسه یکتا (ID) تعریف می‌کند که باید در کل سند منحصر‌به‌فرد باشد. هدف آن شناسایی عنصر هنگام لینک‌دهی (با استفاده از fragment identifier)، اسکریپت‌نویسی یا استایل‌دهی (با CSS) است.
- [`inert`](/en-US/docs/Web/HTML/Reference/Global_attributes/inert)
  - : یک مقدار بولی که باعث می‌شود مرورگر رویدادهای ورودی کاربر را برای عنصر نادیده بگیرد. وقتی رویدادهای کلیک وجود دارند مفید است.
- [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode)
  - : به مرورگرها راهنمایی می‌کند که هنگام ویرایش این عنصر یا محتوای آن از چه نوع پیکربندی صفحه‌کلید مجازی استفاده شود. عمدتاً روی عناصر {{HTMLElement("input")}} استفاده می‌شود، اما در حالت [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) روی هر عنصری قابل استفاده است.
- [`is`](/en-US/docs/Web/HTML/Reference/Global_attributes/is)
  - : به شما اجازه می‌دهد مشخص کنید که یک عنصر HTML استاندارد مانند یک عنصر داخلی سفارشی‌سازی‌شده (customized built-in element) ثبت‌شده رفتار کند (برای جزئیات بیشتر به [Using custom elements](/en-US/docs/Web/API/Web_components/Using_custom_elements) مراجعه کنید).

> [!NOTE]
> ویژگی‌های `item*` بخشی از [ویژگی WHATWG HTML Microdata](https://html.spec.whatwg.org/multipage/microdata.html#microdata) هستند.

- [`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid)
  - : شناسهٔ یکتای جهانی (global identifier) یک آیتم.

- [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop)
  - : برای افزودن ویژگی‌ها (properties) به یک آیتم استفاده می‌شود. هر المان HTML می‌تواند یک attribute به نام `itemprop` داشته باشد که از یک جفت نام و مقدار تشکیل شده است.

- [`itemref`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemref)
  - : ویژگی‌هایی که فرزند مستقیم المان دارای `itemscope` نیستند، می‌توانند از طریق `itemref` به آن آیتم متصل شوند. این attribute یک لیست از `id` المان‌ها (نه `itemid`) را ارائه می‌دهد که ویژگی‌های اضافی را در جای دیگری از سند مشخص می‌کند.

- [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope)
  - : `itemscope` (معمولاً) همراه با [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype) کار می‌کند تا مشخص کند HTML داخل یک بلوک به یک آیتم خاص مربوط است. `itemscope` خود آیتم را ایجاد می‌کند و محدودهٔ `itemtype` مرتبط با آن را تعریف می‌کند. `itemtype` یک URL معتبر از یک واژگان (vocabulary) مانند [schema.org](https://schema.org/) است که آیتم و زمینهٔ ویژگی‌های آن را توصیف می‌کند.

- [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype)
  - : نشانی اینترنتی واژگانی (vocabulary) را مشخص می‌کند که برای تعریف `itemprop`ها (ویژگی‌های آیتم) در ساختار داده استفاده می‌شود. [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope) برای تعیین محدوده‌ای از ساختار داده که واژگان تعیین‌شده توسط `itemtype` در آن فعال است، به کار می‌رود.

- [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang)
  - : زبان یک المان را مشخص می‌کند؛ زبانی که المان‌های غیرقابل ویرایش به آن هستند، یا زبانی که المان‌های قابل ویرایش باید توسط کاربر به آن نوشته شوند. این attribute باید یک برچسب زبان معتبر BCP 47 باشد. `xml:lang` بر آن اولویت دارد.

- [`nonce`](/en-US/docs/Web/HTML/Reference/Global_attributes/nonce)
  - : یک nonce رمزنگاری («عددی که یک بار استفاده می‌شود») که می‌تواند توسط [Content Security Policy](/en-US/docs/Web/HTTP/Guides/CSP) برای تعیین اینکه آیا یک درخواست خاص مجاز به اجرا است یا خیر، استفاده شود.

- [`part`](/en-US/docs/Web/HTML/Reference/Global_attributes/part)
  - : یک لیست جدا شده با فاصله از نام‌های part مربوط به المان. نام‌های part به CSS اجازه می‌دهند تا المان‌های خاصی را در یک shadow tree از طریق شبه‌المان {{CSSxRef("::part")}} انتخاب و استایل‌دهی کند.

- [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
  - : برای تعیین یک المان به عنوان المان popover استفاده می‌شود (به Popover API مراجعه کنید). المان‌های popover با `display: none` پنهان می‌شوند تا زمانی که توسط یک المان فراخوان/کنترل (مانند `<button>` یا `<input type="button">` با attribute `popovertarget`) یا فراخوانی `HTMLElement.showPopover()` باز شوند.

- [`role`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles)
  - : نقش‌ها (roles) معنای معنایی (semantic meaning) محتوا را تعریف می‌کنند و به screen readerها و سایر ابزارها امکان می‌دهند تا محتوا را به گونه‌ای ارائه و تعامل با آن را پشتیبانی کنند که با انتظارات کاربر از آن نوع شیء هماهنگ باشد. نقش‌ها با استفاده از `role="role_type"` به المان‌های HTML اضافه می‌شوند، که در آن `role_type` نام یک نقش در مشخصات ARIA است.

- [`slot`](/en-US/docs/Web/HTML/Reference/Global_attributes/slot)
  - : یک slot در shadow tree [shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM) را به یک المان اختصاص می‌دهد: المانی که attribute `slot` دارد به slot ایجاد شده توسط المان `<slot>` اختصاص می‌یابد، به شرطی که مقدار attribute `name` آن `<slot>` با مقدار `slot` المان مطابقت داشته باشد.

- [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck)
  - : یک attribute شمارشی (enumerated) که تعیین می‌کند آیا المان می‌تواند از نظر غلط‌های املایی بررسی شود یا خیر. مقادیر ممکن عبارتند از:
    - رشتهٔ خالی یا `true` که نشان می‌دهد المان باید در صورت امکان از نظر غلط‌های املایی بررسی شود.
    - `false` که نشان می‌دهد المان نباید از نظر غلط‌های املایی بررسی شود.

- [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style)
  - : شامل اعلان‌های استایل CSS است که روی عنصر اعمال می‌شوند. توجه داشته باشید که توصیه می‌شود استایل‌ها در فایل(های) جداگانه تعریف شوند. این ویژگی و عنصر `<style>` عمدتاً برای استایل‌دهی سریع به کار می‌روند؛ مثلاً برای اهداف آزمایشی.

- [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex)
  - : یک ویژگی عددی است که مشخص می‌کند آیا عنصر می‌تواند فوکوس ورودی بگیرد (یعنی *focusable* باشد)، آیا باید در ناوبری متوالی با صفحه‌کلید شرکت کند و اگر چنین است، در چه موقعیتی. می‌تواند مقادیر زیر را بگیرد:
    - یک *مقدار منفی* یعنی عنصر باید قابل فوکوس باشد، اما نباید از طریق ناوبری متوالی با صفحه‌کلید قابل دسترسی باشد.
    - `0` یعنی عنصر باید قابل فوکوس و از طریق ناوبری متوالی با صفحه‌کلید قابل دسترسی باشد، اما ترتیب نسبی آن توسط قرارداد پلتفرم تعیین می‌شود.
    - یک *مقدار مثبت* یعنی عنصر باید قابل فوکوس و از طریق ناوبری متوالی با صفحه‌کلید قابل دسترسی باشد؛ عناصر به ترتیب صعودی مقدار [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) فوکوس می‌شوند. اگر چند عنصر مقدار tabindex یکسانی داشته باشند، ترتیب نسبی آن‌ها بر اساس موقعیت‌شان در سند تعیین می‌شود.

- [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title)
  - : شامل متنی است که اطلاعات راهنما درباره عنصر را ارائه می‌دهد. این اطلاعات معمولاً (اما نه لزوماً) به‌صورت tooltip به کاربر نمایش داده می‌شود.

- [`translate`](/en-US/docs/Web/HTML/Reference/Global_attributes/translate)
  - : یک ویژگی enumerated (شمارشی) است که مشخص می‌کند آیا مقادیر ویژگی‌های عنصر و مقادیر گره‌های فرزند `Text` آن هنگام بومی‌سازی صفحه ترجمه شوند یا بدون تغییر بمانند. می‌تواند مقادیر زیر را داشته باشد:
    - رشته خالی یا `yes`: یعنی عنصر ترجمه خواهد شد.
    - `no`: یعنی عنصر ترجمه نخواهد شد.

- [`virtualkeyboardpolicy`](/en-US/docs/Web/HTML/Reference/Global_attributes/virtualkeyboardpolicy)
  - : یک ویژگی enumerated (شمارشی) است که برای کنترل رفتار صفحه‌کلید مجازی روی صفحه در دستگاه‌هایی مانند تبلت‌ها، تلفن‌های همراه یا دستگاه‌های دیگری که ممکن است صفحه‌کلید فیزیکی در دسترس نباشد، استفاده می‌شود؛ برای عناصری که محتوایشان قابل ویرایش است (مثلاً عنصر `<input>` یا `<textarea>`، یا عنصری که ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) روی آن تنظیم شده است). می‌تواند مقادیر زیر را داشته باشد:
    - `auto` یا رشته خالی: صفحه‌کلید مجازی را به‌طور خودکار وقتی عنصر فوکوس می‌شود یا روی آن ضربه زده می‌شود، نمایش می‌دهد.
    - `manual`: فوکوس و ضربه روی عنصر را از وضعیت صفحه‌کلید مجازی جدا می‌کند.

- [`writingsuggestions`](/en-US/docs/Web/HTML/Reference/Global_attributes/writingsuggestions)
  - : یک ویژگی enumerated (شمارشی) است که مشخص می‌کند آیا پیشنهادهای نوشتاری ارائه‌شده توسط مرورگر باید در محدوده عنصر فعال شوند یا نه. می‌تواند مقادیر زیر را داشته باشد:
    - `false`: پیشنهادهای نوشتاری مرورگر را غیرفعال می‌کند.
    - `true` یا رشته خالی: پیشنهادهای نوشتاری را فعال می‌کند.

## لیست ویژگی‌های مدیریت رویداد سراسری

استفاده از ویژگی‌های مدیریت رویداد HTML توصیه نمی‌شود؛ برای آشنایی با نحوه عملکرد آن‌ها به [مرجع ویژگی‌های HTML](/en-US/docs/Web/HTML/Reference/Attributes#event_handler_attributes) مراجعه کنید.

با وجود اینکه attributeهای زیر روی همهٔ elementها اعمال میشوند، روی همهٔ آنها کارایی ندارند. برای مثال، attribute با نام `onvolumechange` روی همهٔ elementها پذیرفته میشود و یک event listener برای رویداد `volumechange` متصل میکند، اما فقط media elementها هستند که رویداد `volumechange` را از سمت browser دریافت میکنند. برای سایر elementها، تنها راه استفاده از `EventTarget.dispatchEvent()` است تا این رویداد را بهصورت دستی ارسال کنید. [بعضی از attributeها](/en-US/docs/Web/HTML/Reference/Elements/body#event_attributes) را میتوان روی `body` تنظیم کرد، اما در این حالت بهجای آن، رویدادها روی `window` شنیده میشوند.

- [`onabort`](/en-US/docs/Web/API/HTMLMediaElement/abort_event)
- [`onanimationcancel`](/en-US/docs/Web/API/Element/animationcancel_event)
- [`onanimationend`](/en-US/docs/Web/API/Element/animationend_event)
- [`onanimationiteration`](/en-US/docs/Web/API/Element/animationiteration_event)
- [`onanimationstart`](/en-US/docs/Web/API/Element/animationstart_event)
- [`onauxclick`](/en-US/docs/Web/API/Element/auxclick_event)
- [`onbeforeinput`](/en-US/docs/Web/API/Element/beforeinput_event)
- [`onbeforematch`](/en-US/docs/Web/API/Element/beforematch_event)
- [`onbeforetoggle`](/en-US/docs/Web/API/HTMLElement/beforetoggle_event)
- [`onblur`](/en-US/docs/Web/API/Element/blur_event)
- [`oncancel`](/en-US/docs/Web/API/HTMLInputElement/cancel_event)
- [`oncanplay`](/en-US/docs/Web/API/HTMLMediaElement/canplay_event)
- [`oncanplaythrough`](/en-US/docs/Web/API/HTMLMediaElement/canplaythrough_event)
- [`onchange`](/en-US/docs/Web/API/HTMLElement/change_event)
- [`onclick`](/en-US/docs/Web/API/Element/click_event)
- [`onclose`](/en-US/docs/Web/API/HTMLDialogElement/close_event)
- [`oncommand`](/en-US/docs/Web/API/HTMLElement/command_event)
- [`oncontentvisibilityautostatechange`](/en-US/docs/Web/API/Element/contentvisibilityautostatechange_event)
- [`oncontextlost`](/en-US/docs/Web/API/HTMLCanvasElement/contextlost_event)
- [`oncontextmenu`](/en-US/docs/Web/API/Element/contextmenu_event)
- [`oncontextrestored`](/en-US/docs/Web/API/HTMLCanvasElement/contextrestored_event)
- [`oncopy`](/en-US/docs/Web/API/Element/copy_event)
- [`oncuechange`](/en-US/docs/Web/API/HTMLTrackElement/cuechange_event)
- [`oncut`](/en-US/docs/Web/API/Element/cut_event)
- [`ondblclick`](/en-US/docs/Web/API/Element/dblclick_event)
- [`ondrag`](/en-US/docs/Web/API/HTMLElement/drag_event)
- [`ondragend`](/en-US/docs/Web/API/HTMLElement/dragend_event)
- [`ondragenter`](/en-US/docs/Web/API/HTMLElement/dragenter_event)
- [`ondragleave`](/en-US/docs/Web/API/HTMLElement/dragleave_event)
- [`ondragover`](/en-US/docs/Web/API/HTMLElement/dragover_event)
- [`ondragstart`](/en-US/docs/Web/API/HTMLElement/dragstart_event)
- [`ondrop`](/en-US/docs/Web/API/HTMLElement/drop_event)
- [`ondurationchange`](/en-US/docs/Web/API/HTMLMediaElement/durationchange_event)
- [`onemptied`](/en-US/docs/Web/API/HTMLMediaElement/emptied_event)
- [`onended`](/en-US/docs/Web/API/HTMLMediaElement/ended_event)
- [`onerror`](/en-US/docs/Web/API/HTMLElement/error_event)
- [`onfocus`](/en-US/docs/Web/API/Element/focus_event)
- [`onfocusin`](/en-US/docs/Web/API/Element/focusin_event)
- [`onfocusout`](/en-US/docs/Web/API/Element/focusout_event)
- [`onformdata`](/en-US/docs/Web/API/HTMLFormElement/formdata_event)
- [`onfullscreenchange`](/en-US/docs/Web/API/Element/fullscreenchange_event)
- [`onfullscreenerror`](/en-US/docs/Web/API/Element/fullscreenerror_event)
- [`ongesturechange`](/en-US/docs/Web/API/Element/gesturechange_event)
- [`ongestureend`](/en-US/docs/Web/API/Element/gestureend_event)
- [`ongesturestart`](/en-US/docs/Web/API/Element/gesturestart_event)
- [`ongotpointercapture`](/en-US/docs/Web/API/Element/gotpointercapture_event)
- [`oninput`](/en-US/docs/Web/API/Element/input_event)
- [`oninvalid`](/en-US/docs/Web/API/HTMLInputElement/invalid_event)
- [`onkeydown`](/en-US/docs/Web/API/Element/keydown_event)
- [`onkeypress`](/en-US/docs/Web/API/Element/keypress_event)
- [`onkeyup`](/en-US/docs/Web/API/Element/keyup_event)
- [`onload`](/en-US/docs/Web/API/HTMLElement/load_event)
- [`onloadeddata`](/en-US/docs/Web/API/HTMLMediaElement/loadeddata_event)
- [`onloadedmetadata`](/en-US/docs/Web/API/HTMLMediaElement/loadedmetadata_event)
- [`onloadstart`](/en-US/docs/Web/API/HTMLMediaElement/loadstart_event)
- [`onlostpointercapture`](/en-US/docs/Web/API/Element/lostpointercapture_event)
- [`onmousedown`](/en-US/docs/Web/API/Element/mousedown_event)
- [`onmouseenter`](/en-US/docs/Web/API/Element/mouseenter_event)
- [`onmouseleave`](/en-US/docs/Web/API/Element/mouseleave_event)
- [`onmousemove`](/en-US/docs/Web/API/Element/mousemove_event)
- [`onmouseout`](/en-US/docs/Web/API/Element/mouseout_event)
- [`onmouseover`](/en-US/docs/Web/API/Element/mouseover_event)
- [`onmouseup`](/en-US/docs/Web/API/Element/mouseup_event)
- [`onmousewheel`](/en-US/docs/Web/API/Element/mousewheel_event)
- [`onpaste`](/en-US/docs/Web/API/Element/paste_event)
- [`onpause`](/en-US/docs/Web/API/HTMLMediaElement/pause_event)
- [`onplay`](/en-US/docs/Web/API/HTMLMediaElement/play_event)
- [`onplaying`](/en-US/docs/Web/API/HTMLMediaElement/playing_event)
- [`onpointercancel`](/en-US/docs/Web/API/Element/pointercancel_event)
- [`onpointerdown`](/en-US/docs/Web/API/Element/pointerdown_event)
- [`onpointerenter`](/en-US/docs/Web/API/Element/pointerenter_event)
- [`onpointerleave`](/en-US/docs/Web/API/Element/pointerleave_event)
- [`onpointermove`](/en-US/docs/Web/API/Element/pointermove_event)
- [`onpointerout`](/en-US/docs/Web/API/Element/pointerout_event)
- [`onpointerover`](/en-US/docs/Web/API/Element/pointerover_event)
- [`onpointerrawupdate`](/en-US/docs/Web/API/Element/pointerrawupdate_event)
- [`onpointerup`](/en-US/docs/Web/API/Element/pointerup_event)
- [`onprogress`](/en-US/docs/Web/API/HTMLMediaElement/progress_event)
- [`onratechange`](/en-US/docs/Web/API/HTMLMediaElement/ratechange_event)
- [`onreset`](/en-US/docs/Web/API/HTMLFormElement/reset_event)
- [`onresize`](/en-US/docs/Web/API/HTMLVideoElement/resize_event)
- [`onscroll`](/en-US/docs/Web/API/Element/scroll_event)
- [`onscrollend`](/en-US/docs/Web/API/Element/scrollend_event)
- [`onscrollsnapchange`](/en-US/docs/Web/API/Element/scrollsnapchange_event)
- [`onscrollsnapchanging`](/en-US/docs/Web/API/Element/scrollsnapchanging_event)
- [`onsecuritypolicyviolation`](/en-US/docs/Web/API/Element/securitypolicyviolation_event)
- [`onseeked`](/en-US/docs/Web/API/HTMLMediaElement/seeked_event)
- [`onseeking`](/en-US/docs/Web/API/HTMLMediaElement/seeking_event)
- [`onselect`](/en-US/docs/Web/API/HTMLInputElement/select_event)
- [`onselectionchange`](/en-US/docs/Web/API/HTMLInputElement/selectionchange_event)
- [`onselectstart`](/en-US/docs/Web/API/Node/selectstart_event)
- [`onslotchange`](/en-US/docs/Web/API/HTMLSlotElement/slotchange_event)
- [`onstalled`](/en-US/docs/Web/API/HTMLMediaElement/stalled_event)
- [`onsubmit`](/en-US/docs/Web/API/HTMLFormElement/submit_event)
- [`onsuspend`](/en-US/docs/Web/API/HTMLMediaElement/suspend_event)
- [`ontimeupdate`](/en-US/docs/Web/API/HTMLMediaElement/timeupdate_event)
- [`ontoggle`](/en-US/docs/Web/API/HTMLElement/toggle_event)
- [`ontouchcancel`](/en-US/docs/Web/API/Element/touchcancel_event)
- [`ontouchend`](/en-US/docs/Web/API/Element/touchend_event)
- [`ontouchmove`](/en-US/docs/Web/API/Element/touchmove_event)
- [`ontouchstart`](/en-US/docs/Web/API/Element/touchstart_event)
- [`ontransitioncancel`](/en-US/docs/Web/API/Element/transitioncancel_event)
- [`ontransitionend`](/en-US/docs/Web/API/Element/transitionend_event)
- [`ontransitionrun`](/en-US/docs/Web/API/Element/transitionrun_event)
- [`ontransitionstart`](/en-US/docs/Web/API/Element/transitionstart_event)
- [`onvolumechange`](/en-US/docs/Web/API/HTMLMediaElement/volumechange_event)
- [`onwaiting`](/en-US/docs/Web/API/HTMLMediaElement/waiting_event)
- [`onwebkitmouseforcechanged`](/en-US/docs/Web/API/Element/webkitmouseforcechanged_event)
- [`onwebkitmouseforcedown`](/en-US/docs/Web/API/Element/webkitmouseforcedown_event)
- [`onwebkitmouseforceup`](/en-US/docs/Web/API/Element/webkitmouseforceup_event)
- [`onwebkitmouseforcewillbegin`](/en-US/docs/Web/API/Element/webkitmouseforcewillbegin_event)
- [`onwheel`](/en-US/docs/Web/API/Element/wheel_event)

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- رابط Element که امکان پرسوجوی بیشتر attributeهای سراسری را فراهم میکند.