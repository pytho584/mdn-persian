---
title: "HTMLElement"
---

---
title: HTMLElement
slug: Web/API/HTMLElement
page-type: web-api-interface
browser-compat: api.HTMLElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLElement`** نمایانگر هر المان [HTML](/en-US/docs/Web/HTML) است. برخی المان‌ها مستقیماً این رابط را پیاده‌سازی می‌کنند و برخی دیگر از طریق رابطی که از آن ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌های والد خود، {{DOMxRef("Element")}} را به ارث می‌برد._

- {{DOMxRef("HTMLElement.accessKey")}}
  - : رشته‌ای که کلید دسترسی اختصاص‌یافته به المان را نشان می‌دهد.
- {{DOMxRef("HTMLElement.accessKeyLabel")}} {{ReadOnlyInline}}
  - : رشته‌ای حاوی کلید دسترسی اختصاص‌یافته به المان را برمی‌گرداند.
- {{DOMxRef("HTMLElement.anchorElement")}} {{ReadOnlyInline}}&nbsp;{{non-standard_inline}} {{experimental_inline}}
  - : ارجاعی به المان لنگر (anchor) را برمی‌گرداند؛ یا اگر المان لنگر نداشته باشد، `null` را برمی‌گرداند.
- {{DOMxRef("HTMLElement.attributeStyleMap")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("StylePropertyMap")}} که اعلان‌های (declarations) ویژگی [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) المان را نشان می‌دهد.
- {{domxref("HTMLElement.autocapitalize")}}
  - : رشته‌ای که رفتار حروف بزرگ (capitalization) المان را برای ورودی کاربر نشان می‌دهد. مقادیر معتبر عبارت‌اند از: `none`، `off`، `on`، `characters`، `words`، `sentences`.
- {{domxref("HTMLElement.autofocus")}}
  - : مقدار بولی که ویژگی سراسری HTML [`autofocus`](/en-US/docs/Web/HTML/Reference/Elements/select#autofocus) را منعکس می‌کند؛ این ویژگی مشخص می‌کند که آیا کنترل باید هنگام بارگذاری صفحه فوکوس بگیرد یا، اگر روی المانی داخل عناصر {{htmlelement("dialog")}} یا عناصری که ویژگی popover آن‌ها تنظیم شده است تعیین شده باشد، هنگام نمایش dialog یا popover فوکوس بگیرد.
- {{domxref("HTMLElement.autocorrect")}}
  - : یک مقدار بولی که نشان می‌دهد آیا متنی که کاربر وارد می‌کند باید به‌صورت خودکار تصحیح شود یا نه. این ویژگی، ویژگی سراسری HTML [`autocorrect`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect) را منعکس می‌کند.
- {{DOMxRef("HTMLElement.contentEditable")}}
  - : رشته‌ای که مقدار `true` به این معناست که المان قابل ویرایش است و مقدار `false` به این معناست که قابل ویرایش نیست.
- {{DOMxRef("HTMLElement.dataset")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("DOMStringMap")}} برمی‌گرداند که اسکریپت می‌تواند با آن [ویژگی‌های داده سفارشی](/en-US/docs/Web/HTML/How_to/Use_data_attributes) (`data-*`) المان را بخواند و بنویسد.
- {{DOMxRef("HTMLElement.dir")}}
  - : رشته‌ای که ویژگی سراسری `dir` را منعکس می‌کند و جهت (directionality) المان را نشان می‌دهد. مقادیر ممکن عبارت‌اند از `"ltr"`، `"rtl"` و `"auto"`.
- {{DOMxRef("HTMLElement.draggable")}}
  - : مقدار بولی که نشان می‌دهد آیا المان قابل کشیدن (drag) است یا نه.
- {{DOMxRef("HTMLElement.editContext")}} {{experimental_inline}}
  - : {{DOMxRef("EditContext")}} مرتبط با المان را برمی‌گرداند، یا اگر وجود نداشته باشد `null` را برمی‌گرداند.
- {{DOMxRef("HTMLElement.enterKeyHint")}}
  - : رشته‌ای که تعیین می‌کند برای کلید Enter در صفحه‌کلیدهای مجازی چه برچسب عملی (یا آیکنی) نمایش داده شود.
- {{DOMxRef("HTMLElement.hidden")}}
  - : مقدار رشته‌ای یا بولی که مقدار ویژگی [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) المان را منعکس می‌کند.
- {{DOMxRef("HTMLElement.inert")}}
  - : مقدار بولی که نشان می‌دهد آیا عامل کاربر (user agent) باید برای رویدادهای تعامل کاربر، جست‌وجوی متن در صفحه («یافتن در صفحه») و انتخاب متن، طوری رفتار کند که گویی گره مورد نظر وجود ندارد.
- {{DOMxRef("HTMLElement.innerText")}}
  - : محتوای متنی رندر شدهٔ یک گره و فرزندان آن را نشان می‌دهد.
    به‌عنوان getter، متنی را تقریب می‌زند که کاربر اگر محتویات المان را با نشانگر انتخاب کند و سپس در کلیپ‌بورد کپی کند، دریافت می‌کند.
    به‌عنوان setter، محتوای داخل المان انتخاب‌شده را با مقدار داده‌شده جایگزین می‌کند و هر شکست خط را به عناصر {{HTMLElement("br")}} تبدیل می‌کند.
- {{DOMxRef("HTMLElement.inputMode")}}
  - : مقدار رشته‌ای که مقدار ویژگی [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode) المان را منعکس می‌کند.
- {{DOMxRef("HTMLElement.isContentEditable")}} {{ReadOnlyInline}}
  - : مقدار بولی برمی‌گرداند که نشان می‌دهد آیا محتوای المان قابل ویرایش است یا نه.
- {{DOMxRef("HTMLElement.lang")}}
  - : رشته‌ای که زبان ویژگی‌ها، متن و محتویات یک المان را نشان می‌دهد.
- {{DOMxRef("HTMLElement.nonce")}}
  - : عدد رمزنگاری یکبارمصرف (nonce) را برمی‌گرداند که Content Security Policy از آن استفاده می‌کند تا تعیین کند آیا یک واکشی (fetch) مشخص مجاز به انجام است یا خیر.
- {{DOMxRef("HTMLElement.offsetHeight")}} {{ReadOnlyInline}}
  - : یک `double` شامل ارتفاع یک المان، نسبت به چیدمان (layout) را برمی‌گرداند.
- {{DOMxRef("HTMLElement.offsetLeft")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند: فاصله از حاشیه چپ این المان تا حاشیه چپ `offsetParent` آن.
- {{DOMxRef("HTMLElement.offsetParent")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("Element")}} که المانی است که تمام محاسبات offset در حال حاضر بر اساس آن انجام می‌شود.
- {{DOMxRef("HTMLElement.offsetTop")}} {{ReadOnlyInline}}
  - : یک `double` برمی‌گرداند: فاصله از حاشیه بالای این المان تا حاشیه بالای `offsetParent` آن.
- {{DOMxRef("HTMLElement.offsetWidth")}} {{ReadOnlyInline}}
  - : یک `double` شامل عرض یک المان، نسبت به چیدمان، برمی‌گرداند.
- {{DOMxRef("HTMLElement.outerText")}}
  - : محتوای متنی رندر شدهٔ یک گره و فرزندان آن را نشان می‌دهد.
    به‌عنوان getter، همانند {{DOMxRef("HTMLElement.innerText")}} است (محتوای متنی رندر شدهٔ یک المان و فرزندان آن را نشان می‌دهد).
    به‌عنوان setter، گره انتخاب‌شده و محتویات آن را با مقدار داده‌شده جایگزین می‌کند و هر شکست خط را به عناصر {{HTMLElement("br")}} تبدیل می‌کند.
- {{domxref("HTMLElement.popover")}}
  - : وضعیت popover یک المان را از طریق JavaScript (`"auto"`، `"hint"` یا `"manual"`) می‌خواند و تنظیم می‌کند و می‌تواند برای تشخیص قابلیت (feature detection) استفاده شود. مقدار ویژگی سراسری HTML [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) را منعکس می‌کند.
- {{DOMxRef("HTMLElement.spellcheck")}}
  - : مقدار بولی که راهنمای [غلط‌یاب املایی](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) را کنترل می‌کند. این ویژگی روی همه المان‌های HTML در دسترس است، هرچند روی همه آن‌ها تأثیر نمی‌گذارد.
- {{DOMxRef("HTMLElement.style")}}
  - : یک {{DOMxRef("CSSStyleDeclaration")}} که اعلان‌های ویژگی [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) المان را نشان می‌دهد.
- {{DOMxRef("HTMLElement.tabIndex")}}
  - : یک `long` که موقعیت المان در ترتیب پیمایش با Tab را نشان می‌دهد.
- {{DOMxRef("HTMLElement.title")}}
  - : رشته‌ای شامل متنی که وقتی نشانگر ماوس روی المان است در جعبه بازشو (popup) ظاهر می‌شود.
- {{DOMxRef("HTMLElement.translate")}}
  - : مقدار بولی که وضعیت ترجمه را نشان می‌دهد.
- {{DOMxRef("HTMLElement.virtualKeyboardPolicy")}} {{Experimental_Inline}}
  - : رشته‌ای که رفتار صفحه‌کلید مجازی روی صفحه را در دستگاه‌هایی مانند تبلت‌ها، تلفن‌های همراه یا سایر دستگاه‌هایی که ممکن است صفحه‌کلید فیزیکی در دسترس نباشد، نشان می‌دهد، اگر محتوای المان قابل ویرایش باشد (مثلاً یک المان {{htmlelement("input")}} یا {{htmlelement("textarea")}} باشد، یا المانی که ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) آن تنظیم شده است).
- {{DOMxRef("HTMLElement.writingSuggestions")}}
  - : رشته‌ای که نشان می‌دهد آیا پیشنهادهای نوشتاری ارائه‌شده توسط مرورگر باید در محدوده (scope) المان فعال باشند یا نه.

## متدهای نمونه

_همچنین متدهای والد خود، {{DOMxRef("Element")}} را به ارث می‌برد._

- {{DOMxRef("HTMLElement.attachInternals()")}}
  - : یک شیء {{DOMxRef("ElementInternals")}} برمی‌گرداند و به یک المان سفارشی امکان مشارکت در فرم‌های HTML را می‌دهد.
- {{DOMxRef("HTMLElement.blur()")}}
  - : فوکوس صفحه‌کلید را از المان فوکوشدهٔ فعلی حذف می‌کند.
- {{DOMxRef("HTMLElement.click()")}}
  - : یک رویداد کلیک ماوس به المان ارسال می‌کند.
- {{DOMxRef("HTMLElement.focus()")}}
  - : المان را به فوکوس فعلی صفحه‌کلید تبدیل می‌کند.
- {{DOMxRef("HTMLElement.hidePopover()")}}
  - : یک المان popover را با حذف آن از {{glossary("top layer")}} و اعمال استایل `display: none` پنهان می‌کند.
- {{DOMxRef("HTMLElement.showPopover()")}}
  - : یک المان popover را با افزودن آن به {{glossary("top layer")}} و حذف `display: none;` از استایل‌هایش نمایش می‌دهد.
- {{DOMxRef("HTMLElement.togglePopover()")}}
  - : یک المان popover را بین حالت پنهان و حالت نمایش‌داده‌شده تغییر وضعیت می‌دهد.

## رویدادها

به این رویدادها با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با تخصیص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید.

_همچنین، رویدادهای والد خود، {{DOMxRef("Element")}} را به ارث می‌برد._

- {{DOMxRef("HTMLElement/change_event", "change")}}
  - : زمانی رخ می‌دهد که `value` یک المان {{HTMLElement("input")}}، {{HTMLElement("select")}} یا {{HTMLElement("textarea")}} توسط کاربر تغییر کرده و تأیید (commit) شده باشد. برخلاف رویداد {{domxref("Element/input_event", "input")}}، رویداد `change` لزوماً برای هر تغییر در `value` یک المان رخ نمی‌دهد.
- {{domxref("HTMLElement/command_event", "command")}}
  - : روی المانی رخ می‌دهد که از طریق یک {{domxref("HTMLButtonElement", "button")}} با مقادیر معتبر {{domxref("HTMLButtonElement.commandForElement", "commandForElement")}} و {{domxref("HTMLButtonElement.command", "command")}} کنترل می‌شود، هر زمان که با دکمه تعامل شود (مثلاً روی آن کلیک شود).
- {{DOMxRef("HTMLElement/error_event", "error")}}
  - : زمانی رخ می‌دهد که یک منبع (resource) نتواند بارگذاری شود یا قابل استفاده نباشد.
- {{DOMxRef("HTMLElement/load_event", "load")}}
  - : برای المان‌های حاوی یک منبع، زمانی که منبع با موفقیت بارگذاری شود، رخ می‌دهد.

### رویدادهای کشیدن و رها کردن

- {{DOMxRef("HTMLElement/drag_event", "drag")}}
  - : این رویداد زمانی رخ می‌دهد که یک المان یا انتخاب متنی در حال کشیده شدن است.
- {{DOMxRef("HTMLElement/dragend_event", "dragend")}}
  - : این رویداد زمانی رخ می‌دهد که عملیات کشیدن در حال پایان یافتن است (با رها کردن دکمه ماوس یا فشردن کلید Escape).
- {{DOMxRef("HTMLElement/dragenter_event", "dragenter")}}
  - : این رویداد زمانی رخ می‌دهد که یک المان کشیده‌شده یا انتخاب متنی وارد یک هدف رهاسازی معتبر می‌شود.
- {{DOMxRef("HTMLElement/dragleave_event", "dragleave")}}
  - : این رویداد زمانی رخ می‌دهد که یک المان کشیده‌شده یا انتخاب متنی از یک هدف رهاسازی معتبر خارج می‌شود.
- {{DOMxRef("HTMLElement/dragover_event", "dragover")}}
  - : این رویداد به‌طور مداوم زمانی رخ می‌دهد که یک المان یا انتخاب متنی در حال کشیده شدن است و نشانگر ماوس روی یک هدف رهاسازی معتبر قرار دارد (هر ۵۰ میلی‌ثانیه وقتی ماوس حرکت نمی‌کند، و در غیر این صورت بسیار سریع‌تر، بین حدوداً ۵ میلی‌ثانیه (حرکت آهسته) و ۱ میلی‌ثانیه (حرکت سریع). این الگوی رخ‌دادن با رویداد {{domxref("Element/mouseover_event", "mouseover")}} متفاوت است).
- {{DOMxRef("HTMLElement/dragstart_event", "dragstart")}}
  - : این رویداد زمانی رخ می‌دهد که کاربر شروع به کشیدن یک المان یا انتخاب متنی می‌کند.
- {{DOMxRef("HTMLElement/drop_event", "drop")}}
  - : این رویداد زمانی رخ می‌دهد که یک المان یا انتخاب متنی روی یک هدف رهاسازی معتبر رها می‌شود.

### رویدادهای فراخوانندهٔ علاقه‌مندی (interest invoker)

- {{domxref("HTMLElement.interest_event", "interest")}} {{experimental_inline}} {{non-standard_inline}}
  - : روی المان هدف یک [فراخ