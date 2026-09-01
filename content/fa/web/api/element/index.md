```markdown
---
title: Element
slug: Web/API/Element
page-type: web-api-interface
browser-compat: api.Element
---

{{APIRef("DOM")}}

**`Element`** عمومی‌ترین کلاس پایه است که تمام اشیاء عنصر (یعنی اشیایی که عناصر را نمایش می‌دهند) در یک {{DOMxRef("Document")}} از آن ارث‌‌بری می‌کنند. این کلاس فقط دارای متدها و ویژگی‌های مشترک بین همه انواع عناصر است. کلاس‌های خاص‌تر از `Element` ارث‌بری می‌کنند.

برای مثال، رابط {{DOMxRef("HTMLElement")}} رابط پایه برای عناصر HTML است. به طور مشابه، رابط {{DOMxRef("SVGElement")}} پایه تمام عناصر SVG، و رابط {{DOMxRef("MathMLElement")}} رابط پایه عناصر MathML است. بیشتر قابلیت‌ها در سطوح پایین‌تر سلسله‌مراتب کلاس‌ها مشخص می‌شوند.

زبان‌های خارج از حوزه پلتفرم وب، مانند XUL از طریق رابط `XULElement`، نیز `Element` را پیاده‌سازی می‌کنند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

`Element` ویژگی‌ها را از رابط والد خود، {{DOMxRef("Node")}}، و به تبع آن از والد آن رابط، {{DOMxRef("EventTarget")}}، به ارث می‌برد.

- {{DOMxRef("Element.activeViewTransition")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک نمونه {{domxref("ViewTransition")}} را برمی‌گرداند که نمایانگر [view transition](/en-US/docs/Web/API/View_Transition_API) در حال اجرا بر روی عنصر است.
- {{DOMxRef("Element.assignedSlot")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("HTMLSlotElement")}} را برمی‌گرداند که نمایانگر {{htmlelement("slot")}}ای است که گره در آن درج شده است.
- {{DOMxRef("Element.attributes")}} {{ReadOnlyInline}}
  - : یک شیء {{DOMxRef("NamedNodeMap")}} شامل ویژگی‌های تخصیص‌یافته عنصر HTML متناظر را برمی‌گرداند.
- {{domxref("Element.childElementCount")}} {{ReadOnlyInline}}
  - : تعداد عناصر فرزند این عنصر را برمی‌گرداند.
- {{domxref("Element.children")}} {{ReadOnlyInline}}
  - : عناصر فرزند این عنصر را برمی‌گرداند.
- {{DOMxRef("Element.classList")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("DOMTokenList")}} شامل لیست ویژگی‌های کلاس را برمی‌گرداند.
- {{DOMxRef("Element.className")}}
  - : یک رشته که کلاس عنصر را نمایش می‌دهد.
- {{DOMxRef("Element.clientHeight")}} {{ReadOnlyInline}}
  - : یک عدد که ارتفاع داخلی عنصر را نمایش می‌دهد برمی‌گرداند.
- {{DOMxRef("Element.clientLeft")}} {{ReadOnlyInline}}
  - : یک عدد که عرض حاشیه چپ عنصر را نمایش می‌دهد برمی‌گرداند.
- {{DOMxRef("Element.clientTop")}} {{ReadOnlyInline}}
  - : یک عدد که عرض حاشیه بالای عنصر را نمایش می‌دهد برمی‌گرداند.
- {{DOMxRef("Element.clientWidth")}} {{ReadOnlyInline}}
  - : یک عدد که عرض داخلی عنصر را نمایش می‌دهد برمی‌گرداند.
- {{DOMxRef("Element.currentCSSZoom")}} {{ReadOnlyInline}}
  - : یک عدد که اندازه بزرگنمایی مؤثر عنصر را نشان می‌دهد، یا اگر عنصر رندر نشده باشد، 1.0 را برمی‌گرداند.
- {{DOMxRef("Element.customElementRegistry")}} {{ReadOnlyInline}}
  - : شیء {{domxref("CustomElementRegistry")}} مرتبط با این عنصر را برمی‌گرداند، یا اگر تنظیم نشده باشد، `null` را.
- {{DOMxRef("Element.elementTiming")}} {{Experimental_Inline}}
  - : یک رشته که منعکس‌کننده ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) است و عنصر را برای مشاهده در API {{domxref("PerformanceElementTiming")}} علامت‌گذاری می‌کند.
- {{domxref("Element.firstElementChild")}} {{ReadOnlyInline}}
  - : اولین عنصر فرزند این عنصر را برمی‌گرداند.
- {{DOMxRef("Element.id")}}
  - : یک رشته که شناسه عنصر را نمایش می‌دهد.
- {{DOMxRef("Element.innerHTML")}}
  - : یک رشته که نشانه‌گذاری محتوای عنصر را نمایش می‌دهد.
- {{domxref("Element.lastElementChild")}} {{ReadOnlyInline}}
  - : آخرین عنصر فرزند این عنصر را برمی‌گرداند.
- {{DOMxRef("Element.localName")}} {{ReadOnlyInline}}
  - : یک رشته که بخش محلی نام واجد شرایط عنصر را نمایش می‌دهد.
- {{DOMxRef("Element.namespaceURI")}} {{ReadOnlyInline}}
  - : URI فضای نام عنصر، یا اگر فضای نامی نداشته باشد، `null`.
- {{DOMxRef("Element.nextElementSibling")}} {{ReadOnlyInline}}
  - : یک `Element`، عنصری که بلافاصله بعد از عنصر داده شده در درخت می‌آید، یا اگر خواهر/برادر گره‌ای وجود نداشته باشد، `null`.
- {{DOMxRef("Element.outerHTML")}}
  - : یک رشته که نشانه‌گذاری عنصر شامل محتوای آن را نمایش می‌دهد. هنگامی که به عنوان setter استفاده می‌شود، عنصر را با گره‌های تجزیه شده از رشته داده شده جایگزین می‌کند.
- {{DOMxRef("Element.part")}}
  - : شناسه‌های بخش عنصر (یعنی تنظیم شده با استفاده از ویژگی `part`) را نمایش می‌دهد، که به عنوان یک {{domxref("DOMTokenList")}} برگردانده می‌شود.
- {{DOMxRef("Element.prefix")}} {{ReadOnlyInline}}
  - : یک رشته که پیشوند فضای نام عنصر را نمایش می‌دهد، یا اگر پیشوندی مشخص نشده باشد، `null`.
- {{DOMxRef("Element.previousElementSibling")}} {{ReadOnlyInline}}
  - : یک `Element`، عنصری که بلافاصله قبل از عنصر داده شده در درخت می‌آید، یا اگر عنصر خواهر/برادری وجود نداشته باشد، `null`.
- {{DOMxRef("Element.scrollHeight")}} {{ReadOnlyInline}}
  - : یک عدد که ارتفاع نمای پیمایش یک عنصر را برمی‌گرداند.
- {{DOMxRef("Element.scrollLeft")}}
  - : یک عدد که افست پیمایش چپ عنصر را نمایش می‌دهد.
- {{DOMxRef("Element.scrollLeftMax")}} {{Non-standard_Inline}} {{ReadOnlyInline}}
  - : یک عدد که حداکثر افست پیمایش چپ ممکن برای عنصر را برمی‌گرداند.
- {{DOMxRef("Element.scrollTop")}}
  - : یک عدد که تعداد پیکسل‌های پیمایش عمودی بالای عنصر را نمایش می‌دهد.
- {{DOMxRef("Element.scrollTopMax")}} {{Non-standard_Inline}} {{ReadOnlyInline}}
  - : یک عدد که حداکثر افست پیمایش بالا ممکن برای عنصر را برمی‌گرداند.
- {{DOMxRef("Element.scrollWidth")}} {{ReadOnlyInline}}
  - : یک عدد که عرض نمای پیمایش عنصر را برمی‌گرداند.
- {{DOMxRef("Element.shadowRoot")}} {{ReadOnlyInline}}
  - : ریشه سایه باز میزبانی شده توسط عنصر را برمی‌گرداند، یا اگر ریشه سایه باز وجود نداشته باشد، null.
- {{DOMxRef("Element.slot")}}
  - : نام slot DOM سایه که عنصر در آن درج شده است را برمی‌گرداند.
- {{DOMxRef("Element.tagName")}} {{ReadOnlyInline}}
  - : یک رشته با نام برچسب برای عنصر داده شده را برمی‌گرداند.

### ویژگی‌های نمونه شامل شده از ARIA

_رابط `Element` همچنین شامل ویژگی‌های زیر است._

- {{domxref("Element.ariaAtomic")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic) است، که نشان می‌دهد آیا فناوری‌های کمکی تمام یا فقط بخشی از ناحیه تغییر یافته را بر اساس اعلان‌های تغییر تعریف شده توسط ویژگی [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant) ارائه خواهند داد.
- {{domxref("Element.ariaAutoComplete")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete) است، که نشان می‌دهد آیا وارد کردن متن می‌تواند باعث نمایش یک یا چند پیش‌بینی از مقدار مورد نظر کاربر برای یک کادر ترکیبی، کادر جستجو یا کادر متن شود و نحوه ارائه پیش‌بینی‌ها در صورت انجام را مشخص می‌کند.
- {{domxref("Element.ariaBrailleLabel")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-braillelabel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel) است، که برچسب بریل عنصر را تعریف می‌کند.
- {{domxref("Element.ariaBrailleRoleDescription")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-brailleroledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription) است، که توضیحات نقش بریل ARIA عنصر را تعریف می‌کند.
- {{domxref("Element.ariaBusy")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy) است، که نشان می‌دهد آیا یک عنصر در حال تغییر است، زیرا فناوری‌های کمکی ممکن است بخواهند تا پایان تغییرات صبر کنند تا آنها را به کاربر نمایش دهند.
- {{domxref("Element.ariaChecked")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) است، که وضعیت فعلی "checked" (علامت‌خورده) چک‌باکس‌ها، دکمه‌های رادیویی و سایر ویجت‌هایی که حالت علامت‌خورده دارند را نشان می‌دهد.
- {{domxref("Element.ariaColCount")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) است، که تعداد ستون‌ها در یک جدول، شبکه یا شبکه درختی را تعریف می‌کند.
- {{domxref("Element.ariaColIndex")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) است، که ایندکس یا موقعیت ستون یک عنصر را نسبت به تعداد کل ستون‌ها در یک جدول، شبکه یا شبکه درختی تعریف می‌کند.
- {{domxref("Element.ariaColIndexText")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-colindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindextext) است، که یک جایگزین متنی قابل خواندن برای انسان از aria-colindex تعریف می‌کند.
- {{domxref("Element.ariaColSpan")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan) است، که تعداد ستون‌های تحت پوشش یک سلول یا سلول شبکه در یک جدول، شبکه یا شبکه درختی را تعریف می‌کند.
- {{domxref("Element.ariaCurrent")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-current`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-current) است، که عنصر نماینده آیتم جاری در یک ظرف یا مجموعه عناصر مرتبط را نشان می‌دهد.
- {{domxref("Element.ariaDescription")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description) است، که یک مقدار رشته‌ای را تعریف می‌کند که عنصر جاری را توصیف یا حاشیه‌نویسی می‌کند.
- {{domxref("Element.ariaDisabled")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) است، که نشان می‌دهد عنصر قابل درک است اما غیرفعال است، بنابراین قابل ویرایش یا عملکرد نیست.
- {{domxref("Element.ariaExpanded")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) است، که نشان می‌دهد آیا یک عنصر گروه‌بندی که متعلق یا کنترل‌شده توسط این عنصر است، باز یا بسته شده است.
- {{domxref("Element.ariaHasPopup")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) است، که در دسترس بودن و نوع عنصر پاپ‌آپ تعاملی، مانند منو یا دیالوگ، که می‌تواند توسط یک عنصر فعال شود را نشان می‌دهد.
- {{domxref("Element.ariaHidden")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden) است، که نشان می‌دهد آیا عنصر در معرض یک API دسترسی‌پذیری قرار دارد یا خیر.
- {{domxref("Element.ariaInvalid")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid) است، که نشان می‌دهد مقدار وارد شده با فرمت مورد انتظار برنامه مطابقت ندارد.
- {{domxref("Element.ariaKeyShortcuts")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-keyshortcuts`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-keyshortcuts) است، که میانبرهای صفحه‌کلیدی را که نویسنده برای فعال کردن یا تمرکز بر یک عنصر پیاده‌سازی کرده است، نشان می‌دهد.
- {{domxref("Element.ariaLabel")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) است، که یک مقدار رشته‌ای را تعریف می‌کند که عنصر جاری را برچسب‌گذاری می‌کند.
- {{domxref("Element.ariaLevel")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level) است، که سطح سلسله‌مراتبی یک عنصر را در یک ساختار تعریف می‌کند.
- {{domxref("Element.ariaLive")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) است، که نشان می‌دهد یک عنصر به‌روزرسانی خواهد شد، و انواع به‌روزرسانی‌هایی را که عامل کاربر، فناوری‌های کمکی و کاربر می‌توانند از ناحیه زنده انتظار داشته باشند، توصیف می‌کند.
- {{domxref("Element.ariaModal")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-modal`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-modal) است، که نشان می‌دهد آیا یک عنصر هنگام نمایش، مودال است یا خیر.
- {{domxref("Element.ariaMultiline")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-multiline`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiline) است، که نشان می‌دهد آیا یک جعبه متن چند خط ورودی را می‌پذیرد یا فقط یک خط.
- {{domxref("Element.ariaMultiSelectable")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-multiselectable`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable) است، که نشان می‌دهد کاربر می‌تواند بیش از یک آیتم را از بین فرزندان قابل انتخاب جاری انتخاب کند.
- {{domxref("Element.ariaOrientation")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) است، که نشان می‌دهد جهت‌گیری عنصر افقی، عمودی یا نامشخص/مبهم است.
- {{domxref("Element.ariaPlaceholder")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-placeholder`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-placeholder) است، که یک راهنمای کوتاه را تعریف می‌کند که برای کمک به کاربر در ورود داده‌ها زمانی که کنترل فاقد مقدار است، در نظر گرفته شده است.
- {{domxref("Element.ariaPosInSet")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) است، که تعداد یا موقعیت یک عنصر را در مجموعه فعلی از آیتم‌های لیست یا آیتم‌های درختی تعریف می‌کند.
- {{domxref("Element.ariaPressed")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) است، که وضعیت فعلی "pressed" (فشرده) دکمه‌های تغییر وضعیت را نشان می‌دهد.
- {{domxref("Element.ariaReadOnly")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly) است، که نشان می‌دهد عنصر قابل ویرایش نیست، اما در غیر این صورت قابل عملکرد است.
- {{domxref("Element.ariaRelevant")}} {{Non-standard_Inline}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant) است، که نشان می‌دهد چه اعلان‌هایی عامل کاربر هنگام تغییر درخت دسترسی‌پذیری در یک ناحیه زنده فعال می‌کند. این برای توصیف تغییراتی در یک ناحیه `aria-live` که مرتبط هستند و باید اعلام شوند، استفاده می‌شود.
- {{domxref("Element.ariaRequired")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required) است، که نشان می‌دهد ورودی کاربر قبل از ارسال فرم در عنصر الزامی است.
- {{domxref("Element.ariaRoleDescription")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) است، که یک توضیح قابل خواندن برای انسان و بومی‌سازی شده توسط نویسنده برای نقش یک عنصر تعریف می‌کند.
- {{domxref("Element.ariaRowCount")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) است، که تعداد کل ردیف‌ها را در یک جدول، شبکه یا شبکه درختی تعریف می‌کند.
- {{domxref("Element.ariaRowIndex")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) است، که ایندکس یا موقعیت ردیف یک عنصر را نسبت به تعداد کل ردیف‌ها در یک جدول، شبکه یا شبکه درختی تعریف می‌کند.
- {{domxref("Element.ariaRowIndexText")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-rowindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext) است، که یک جایگزین متنی قابل خواندن برای انسان از aria-rowindex تعریف می‌کند.
- {{domxref("Element.ariaRowSpan")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan) است، که تعداد ردیف‌های تحت پوشش یک سلول یا سلول شبکه در یک جدول، شبکه یا شبکه درختی را تعریف می‌کند.
- {{domxref("Element.ariaSelected")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) است، که وضعیت فعلی "selected" (انتخاب‌شده) عناصری که حالت انتخاب‌شده دارند را نشان می‌دهد.
- {{domxref("Element.ariaSetSize")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) است، که تعداد آیتم‌ها را در مجموعه فعلی از آیتم‌های لیست یا آیتم‌های درختی تعریف می‌کند.
- {{domxref("Element.ariaSort")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) است، که نشان می‌دهد آیا آیتم‌ها در یک جدول یا شبکه به ترتیب صعودی یا نزولی مرتب شده‌اند.
- {{domxref("Element.ariaValueMax")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-valueMax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) است، که حداکثر مقدار مجاز برای یک ویجت محدوده را تعریف می‌کند.
- {{domxref("Element.ariaValueMin")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-valueMin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) است، که حداقل مقدار مجاز برای یک ویجت محدوده را تعریف می‌کند.
- {{domxref("Element.ariaValueNow")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-valueNow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) است، که مقدار فعلی برای یک ویجت محدوده را تعریف می‌کند.
- {{domxref("Element.ariaValueText")}}
  - : یک رشته که منعکس‌کننده ویژگی [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext) است، که جایگزین متنی قابل خواندن برای انسان از `aria-valuenow` برای یک ویجت محدوده را تعریف می‌کند.
- {{domxref("Element.role")}}
  - : یک رشته که منعکس‌کننده ویژگی [`role`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) به‌صریح تنظیم‌شده است، که نقش معنایی عنصر را ارائه می‌دهد.

#### ویژگی‌های نمونه منعکس‌شده از ارجاعات عناصر ARIA

این ویژگی‌ها عناصری را که با ارجاع `id` در ویژگی‌های متناظر مشخص شده‌اند منعکس می‌کنند، اما با برخی ملاحظات. برای اطلاعات بیشتر، [ارجاعات عناصر منعکس‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) را در راهنمای _ویژگی‌های منعکس‌شده_ ببینید.

- {{domxref("Element.ariaActiveDescendantElement")}}
  - : عنصری که عنصر فعال فعلی را هنگامی که تمرکز روی یک ویجت [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)، [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)، [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) یا [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role) است، نشان می‌دهد.
    منعکس‌کننده ویژگی [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) است.
- {{domxref("Element.ariaControlsElements")}}
  - : آرایه‌ای از عناصری که محتوا یا حضور آنها توسط عنصری که روی آن اعمال شده کنترل می‌شود.
    منعکس‌کننده ویژگی [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) است.
- {{domxref("Element.ariaDescribedByElements")}}
  - : آرایه‌ای از عناصری که حاوی توضیحات دسترسی‌پذیر برای عنصری هستند که روی آن اعمال شده است.
    منعکس‌کننده ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) است.
- {{domxref("Element.ariaDetailsElements")}}
  - : آرایه‌ای از عناصری که جزئیات دسترسی‌پذیر را برای عنصری که روی آن اعمال شده فراهم می‌کنند.
    منعکس‌کننده ویژگی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) است.
- {{domxref("Element.ariaErrorMessageElements")}}
  - : آرایه‌ای از عناصری که یک پیام خطا برای عنصری که روی آن اعمال شده فراهم می‌کنند.
    منعکس‌کننده ویژگی [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage) است.
- {{domxref("Element.ariaFlowToElements")}}
  - : آرایه‌ای از عناصری که عنصر بعدی (یا عناصر بعدی) را در یک ترتیب خواندن جایگزین از محتوا شناسایی می‌کنند، که ترتیب خواندن عمومی پیش‌فرض را به صلاحدید کاربر لغو می‌کند.
    منعکس‌کننده ویژگی [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto) است.
- {{domxref("Element.ariaLabelledByElements")}}
  - : آرایه‌ای از عناصری که نام دسترسی‌پذیر را برای عنصری که روی آن اعمال شده فراهم می‌کنند.
    منعکس‌کننده ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) است.
- {{domxref("Element.ariaOwnsElements")}}
  - : آرایه‌ای از عناصر متعلق به عنصری که این روی آن اعمال شده است.
    این برای تعریف یک رابطه بصری، عملکردی یا زمینه‌ای بین یک والد و عناصر فرزند آن زمانی استفاده می‌شود که سلسله‌مراتب DOM نمی‌تواند برای نمایش رابطه استفاده شود.
    منعکس‌کننده ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) است.

## روش‌های نمونه

`Element` روش‌ها را از والدین خود {{DOMxRef("Node")}} و والد خود یعنی {{DOMxRef("EventTarget")}} به ارث می‌برد.

- {{DOMxRef("Element.after()")}}
  - : یک مجموعه از اشیاء {{domxref("Node")}} یا رشته‌ها را در لیست فرزندان والد `Element`، درست بعد از `Element` درج می‌کند.
- {{DOMxRef("Element.animate()")}}
  - : یک روش میانبر برای ایجاد و اجرای یک انیمیشن روی یک عنصر. نمونه شیء Animation ایجاد شده را برمی‌گرداند.
- {{DOMxRef("Element.ariaNotify()")}}
  - : مشخص می‌کند که یک رشته متن معین باید توسط صفحه‌خوان اعلام شود.
- {{DOMxRef("Element.append()")}}
  - : یک مجموعه از اشیاء {{domxref("Node")}} یا رشته‌ها را بعد از آخرین فرزند عنصر درج می‌کند.
- {{DOMxRef("Element.attachShadow()")}}
  - : یک درخت DOM سایه را به عنصر مشخص شده متصل می‌کند و یک ارجاع به {{DOMxRef("ShadowRoot")}} آن برمی‌گرداند.
- {{DOMxRef("Element.before()")}}
  - : یک مجموعه از اشیاء {{domxref("Node")}} یا رشته‌ها را در لیست فرزندان والد `Element`، درست قبل از `Element` درج می‌کند.
- {{DOMxRef("Element.checkVisibility()")}}
  - : برمی‌گرداند که آیا یک عنصر انتظار می‌رود قابل مشاهده باشد یا خیر، بر اساس بررسی‌های قابل تنظیم.
- {{DOMxRef("Element.closest()")}}
  - : `Element`ای را برمی‌گرداند که نزدیک‌ترین جد عنصر جاری (یا خود عنصر جاری) است که با انتخاب‌گرهای داده شده در پارامتر مطابقت دارد.
- {{DOMxRef("Element.computedStyleMap()")}}
  - : یک رابط {{DOMxRef("StylePropertyMapReadOnly")}} را برمی‌گرداند که یک نمایش فقط خواندنی از یک بلوک اعلان CSS ارائه می‌دهد که جایگزینی برای {{DOMxRef("CSSStyleDeclaration")}} است.
- {{DOMxRef("Element.getAnimations()")}}
  - : یک آرایه از اشیاء Animation را که در حال حاضر روی عنصر فعال هستند، برمی‌گرداند.
- {{DOMxRef("Element.getAttribute()")}}
  - : مقدار ویژگی نام‌دار را از گره جاری بازیابی می‌کند و آن را به عنوان یک رشته برمی‌گرداند.
- {{DOMxRef("Element.getAttributeNames()")}}
  - : یک آرایه از نام ویژگی‌ها را از عنصر جاری برمی‌گرداند.
- {{DOMxRef("Element.getAttributeNode()")}}
  - : نمایش گره‌ای ویژگی نام‌دار را از گره جاری بازیابی می‌کند و آن را به عنوان یک {{DOMxRef("Attr")}} برمی‌گرداند.
- {{DOMxRef("Element.getAttributeNodeNS()")}}
  - : نمایش گره‌ای ویژگی با نام و فضای نام مشخص شده را از گره جاری بازیابی می‌کند و آن را به عنوان یک {{DOMxRef("Attr")}} برمی‌گرداند.
- {{DOMxRef("Element.getAttributeNS()")}}
  - : مقدار ویژگی با فضای نام و نام مشخص شده را از گره جاری بازیابی می‌کند و آن را به عنوان یک رشته برمی‌گرداند.
- {{DOMxRef("Element.getBoundingClientRect()")}}
  - : اندازه یک عنصر و موقعیت آن را نسبت به viewport برمی‌گرداند.
- {{domxref("Element.getBoxQuads()")}} {{Experimental_Inline}}
  - : یک لیست از اشیاء {{domxref("DOMQuad")}} که نمایانگر قطعات CSS گره هستند را برمی‌گرداند.
- {{DOMxRef("Element.getClientRects()")}}
  - : یک مجموعه از مستطیل‌ها را برمی‌گرداند که مستطیل‌های محدودکننده برای هر خط متن در یک کلاینت را نشان می‌دهند.
- {{DOMxRef("Element.getElementsByClassName()")}}
  - : یک {{DOMxRef("HTMLCollection")}} زنده را برمی‌گرداند که شامل تمام نوادگان عنصر جاری است که دارای لیست کلاس‌های داده شده در پارامتر هستند.
- {{DOMxRef("Element.getElementsByTagName()")}}
  - : یک {{DOMxRef("HTMLCollection")}} زنده را برمی‌گرداند که شامل تمام عناصر نواده، از یک نام برچسب خاص، از عنصر جاری است.
- {{DOMxRef("Element.getElementsByTagNameNS()")}}
  - : یک {{DOMxRef("HTMLCollection")}} زنده را برمی‌گرداند که شامل تمام عناصر نواده، از یک نام برچسب و فضای نام خاص، از عنصر جاری است.
- {{DOMxRef("Element.getHTML()")}}
  - : محتوای DOM عنصر را به عنوان یک رشته HTML، به صورت اختیاری شامل هر DOM سایه، برمی‌گرداند.
- {{DOMxRef("Element.hasAttribute()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا عنصر ویژگی مشخص شده را دارد یا خیر.
- {{DOMxRef("Element.hasAttributeNS()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا عنصر ویژگی مشخص شده را در فضای نام مشخص شده دارد یا خیر.
- {{DOMxRef("Element.hasAttributes()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا عنصر یک یا چند ویژگی HTML دارد یا خیر.
- {{DOMxRef("Element.hasPointerCapture()")}}
  - : نشان می‌دهد آیا عنصری که روی آن فراخوانی شده است، capture اشاره‌گر را برای اشاره‌گر شناسایی شده توسط شناسه اشاره‌گر داده شده دارد یا خیر.
- {{DOMxRef("Element.insertAdjacentElement()")}}
  - : یک گره عنصر داده شده را در موقعیت مشخصی نسبت به عنصری که روی آن فراخوانی شده است، درج می‌کند.
- {{DOMxRef("Element.insertAdjacentHTML()")}}
  - : متن را به عنوان HTML یا XML تجزیه می‌کند و گره‌های حاصل را در موقعیت داده شده در درخت درج می‌کند.
- {{DOMxRef("Element.insertAdjacentText()")}}
  - : یک گره متنی داده شده را در موقعیت مشخصی نسبت به عنصری که روی آن فراخوانی شده است، درج می‌کند.
- {{DOMxRef("Element.matches()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا عنصر با رشته انتخاب‌گر مشخص شده انتخاب می‌شود یا خیر.
- {{DOMxRef("Element.moveBefore()")}}
  - : یک {{domxref("Node")}} داده شده را در داخل گره فراخواننده به عنوان یک فرزند مستقیم، قبل از یک گره مرجع داده شده، بدون حذف و سپس درج گره، جابه‌جا می‌کند.
- {{DOMxRef("Element.prepend()")}}
  - : یک مجموعه از اشیاء {{domxref("Node")}} یا رشته‌ها را قبل از اولین فرزند عنصر درج می‌کند.
- {{DOMxRef("Element.pseudo()")}} {{experimental_inline}}
  - : یک شیء {{domxref("CSSPseudoElement")}} را برمی‌گرداند که نمایانگر [pseudo-element](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) [CSS](/en-US/docs/Web/CSS) از نوع مشخص شده مرتبط با عنصر است.
- {{DOMxRef("Element.querySelector()")}}
  - : اولین {{DOMxRef("Node")}} را که با رشته انتخاب‌گر مشخص شده نسبت به عنصر مطابقت دارد، برمی‌گرداند.
- {{DOMxRef("Element.querySelectorAll()")}}
  - : یک {{DOMxRef("NodeList")}} از گره‌هایی را که با رشته انتخاب‌گر مشخص شده نسبت به عنصر مطابقت دارند، برمی‌گرداند.
- {{DOMxRef("Element.releasePointerCapture()")}}
  - : capture اشاره‌گر که قبلاً برای یک {{DOMxRef("PointerEvent")}} خاص تنظیم شده بود را آزاد می‌کند (متوقف می‌کند).
- {{DOMxRef("Element.remove()")}}
  - : عنصر را از لیست فرزندان والدش حذف می‌کند.
- {{DOMxRef("Element.removeAttribute()")}}
  - : ویژگی نام‌دار را از گره جاری حذف می‌کند.
- {{DOMxRef("Element.removeAttributeNode()")}}
  - : نمایش گره‌ای ویژگی نام‌دار را از گره جاری حذف می‌کند.
- {{DOMxRef("Element.removeAttributeNS()")}}
  - : ویژگی با نام و فضای نام مشخص شده را از گره جاری حذف می‌کند.
- {{DOMxRef("Element.replaceChildren()")}}
  - : فرزندان موجود یک {{domxref("Node")}} را با یک مجموعه جدید مشخص شده از فرزندان جایگزین می‌کند.
- {{DOMxRef("Element.replaceWith()")}}
  - : عنصر را در لیست فرزندان والدش با یک مجموعه از اشیاء {{domxref("Node")}} یا رشته‌ها جایگزین می‌کند.
- {{DOMxRef("Element.requestFullscreen()")}}
  - : به صورت ناهمزمان از مرورگر می‌خواهد تا عنصر را تمام‌صفحه کند.
- {{DOMxRef("Element.requestPointerLock()")}}
  - : امکان درخواست ناهمزمان قفل شدن اشاره‌گر روی عنصر داده شده را فراهم می‌کند.
- {{domxref("Element.scroll()")}}
  - : به یک مجموعه مختصات خاص در داخل یک عنصر داده شده پیمایش می‌کند.
- {{domxref("Element.scrollBy()")}}
  - : یک عنصر را به میزان داده شده پیمایش می‌کند.
- {{DOMxRef("Element.scrollIntoView()")}}
  - : صفحه را پیمایش می‌کند تا عنصر وارد view شود.
- {{DOMxRef("Element.scrollIntoViewIfNeeded()")}} {{Non-standard_Inline}}
  - : عنصر جاری را به ناحیه قابل مشاهده پنجره مرورگر پیمایش می‌کند اگر قبلاً در ناحیه قابل مشاهده پنجره مرورگر نباشد. **به جای آن از استاندارد {{DOMxRef("Element.scrollIntoView()")}} استفاده کنید.**
- {{domxref("Element.scrollTo()")}}
  - : به یک مجموعه مختصات خاص در داخل یک عنصر داده شده پیمایش می‌کند.
- {{DOMxRef("Element.setAttribute()")}}
  - : مقدار یک ویژگی نام‌دار از گره جاری را تنظیم می‌کند.
- {{DOMxRef("Element.setAttributeNode()")}}
  - : نمایش گره‌ای ویژگی نام‌دار را از گره جاری تنظیم می‌کند.
- {{DOMxRef("Element.setAttributeNodeNS()")}}
  - : نمایش گره‌ای ویژگی با نام و فضای نام مشخص شده را از گره جاری تنظیم می‌کند.
- {{DOMxRef("Element.setAttributeNS()")}}
  - : مقدار ویژگی با نام و فضای نام مشخص شده را از گره جاری تنظیم می‌کند.
- {{DOMxRef("Element.setCapture()")}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : capture رویداد ماوس را تنظیم می‌کند و تمام رویدادهای ماوس را به این عنصر هدایت می‌کند.
- {{DOMxRef("Element.setHTML()")}} {{SecureContext_Inline}}
  - : یک رشته HTML را تجزیه و [پالایش (sanitize)](/en-US/docs/Web/API/HTML_Sanitizer_API) می‌کند تا یک قطعه سند ایجاد کند، که سپس زیردرخت اصلی عنصر را در DOM جایگزین می‌کند.
- {{DOMxRef("Element.setHTMLUnsafe()")}}
  - : یک رشته HTML را بدون پالایش به یک قطعه سند تجزیه می‌کند، که سپس زیردرخت اصلی عنصر را در DOM جایگزین می‌کند. رشته HTML ممکن است شامل ریشه‌های سایه اعلانی باشد، که اگر HTML با استفاده از [`Element.innerHTML`](/en-US/docs/Web/API/Element/innerHTML) تنظیم می‌شد، به عنوان عناصر template تجزیه می‌شدند.
- {{DOMxRef("Element.setPointerCapture()")}}
  - : یک عنصر خاص را به عنوان هدف capture رویدادهای [اشاره‌گر](/en-US/docs/Web/API/Pointer_events) آینده تعیین می‌کند.
- {{DOMxRef("Element.startViewTransition()")}} {{experimental_inline}}
  - : یک [view transition](/en-US/docs/Web/API/View_Transition_API) جدید [در محدوده عنصر](/en-US/docs/Web/API/View_Transition_API/Using_element-scoped) در همان سند (SPA) شروع می‌کند و یک شیء {{domxref("ViewTransition")}} برای نمایش آن برمی‌گرداند.
- {{DOMxRef("Element.toggleAttribute()")}}
  - : یک ویژگی بولی را تغییر می‌دهد، اگر وجود داشته باشد آن را حذف می‌کند و اگر وجود نداشته باشد آن را اضافه می‌کند، روی عنصر مشخص شده.

## رویدادها

با استفاده از `addEventListener()` یا با تخصیص یک شنونده رویداد به ویژگی `oneventname` این رابط به این رویدادها گوش دهید.

- {{domxref("Element/afterscriptexecute_event","afterscriptexecute")}} {{Non-standard_Inline}} {{deprecated_inline}}
  - : هنگامی که یک اسکریپت اجرا شده است، فعال می‌شود.
- {{domxref("Element/beforeinput_event", "beforeinput")}}
  - : هنگامی که مقدار یک عنصر ورودی در شرف تغییر است، فعال می‌شود.
- {{domxref("Element/beforematch_event", "beforematch")}}
  - : روی یک عنصر که در حالت [_hidden until found_](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) است، زمانی که مرورگر در شرف آشکار کردن محتوای آن است زیرا کاربر محتوا را از طریق ویژگی "یافتن در صفحه" یا از طریق پیمایش قطعه پیدا کرده است، فعال می‌شود.
- {{domxref("Element/beforescriptexecute_event","beforescriptexecute")}} {{Non-standard_Inline}} {{deprecated_inline}}
  - : هنگامی که یک اسکریپت در شرف اجرا است، فعال می‌شود.
- {{domxref("Element/beforexrselect_event", "beforexrselect")}} {{Experimental_Inline}}
  - : قبل از ارسال رویدادهای انتخاب WebXR ({{domxref("XRSession/select_event", "select")}}, {{domxref("XRSession/selectstart_event", "selectstart")}}, {{domxref("XRSession/selectend_event", "selectend")}}) فعال می‌شود.
- {{domxref("Element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}}
  - : روی هر عنصری که {{cssxref("content-visibility", "content-visibility: auto")}} روی آن تنظیم شده است، زمانی که شروع یا توقف می‌کند [برای کاربر مرتبط باشد](/en-US/docs/Web/CSS/Guides/Containment/Using#relevant_to_the_user) و [محتوای خود را رد کند](/en-US/docs/Web/CSS/Guides/Containment/Using#skips_its_contents)، فعال می‌شود.
- {{domxref("Element/input_event","input")}}
  - : هنگامی که مقدار یک عنصر در نتیجه مستقیم یک اقدام کاربر تغییر می‌کند، فعال می‌شود.
- {{domxref("Element/securitypolicyviolation_event","securitypolicyviolation")}}
  - : هنگامی که یک [سیاست امنیت محتوا](/en-US/docs/Web/HTTP/Guides/CSP) نقض می‌شود، فعال می‌شود.
- {{domxref("Element/wheel_event","wheel")}}
  - : هنگامی که کاربر یک دکمه چرخ روی یک دستگاه اشاره‌گر (معمولاً ماوس) را می‌چرخاند، فعال می‌شود.

### رویدادهای انیمیشن

- {{domxref("Element/animationcancel_event", "animationcancel")}}
  - : هنگامی که یک انیمیشن به طور غیرمنتظره‌ای لغو می‌شود، فعال می‌شود.
- {{domxref("Element/animationend_event", "animationend")}}
  - : هنگامی که یک انیمیشن به طور عادی کامل شده است، فعال می‌شود.
- {{domxref("Element/animationiteration_event", "animationiteration")}}
  - : هنگامی که یک تکرار انیمیشن کامل شده است، فعال می‌شود.
- {{domxref("Element/animationstart_event", "animationstart")}}
  - : هنگامی که یک انیمیشن شروع می‌شود، فعال می‌شود.

### رویدادهای کلیپ‌بورد

- {{domxref("Element/copy_event", "copy")}}
  - : هنگامی که کاربر یک اقدام کپی را از طریق رابط کاربری مرورگر آغاز می‌کند، فعال می‌شود.
- {{domxref("Element/cut_event", "cut")}}
  - : هنگامی که کاربر یک اقدام برش را از طریق رابط کاربری مرورگر آغاز می‌کند، فعال می‌شود.
- {{domxref("Element/paste_event", "paste")}}
  - : هنگامی که کاربر یک اقدام چسباندن را از طریق رابط کاربری مرورگر آغاز می‌کند، فعال می‌شود.

### رویدادهای ترکیب

- {{domxref("Element/compositionend_event", "compositionend")}}
  - : هنگامی که یک سیستم ترکیب متن مانند یک {{glossary("input method editor")}} جلسه ترکیب جاری را کامل یا لغو می‌کند، فعال می‌شود.
- {{domxref("Element/compositionstart_event", "compositionstart")}}
  - : هنگامی که یک سیستم ترکیب متن مانند یک {{glossary("input method editor")}} یک جلسه ترکیب جدید را شروع می‌کند، فعال می‌شود.
- {{domxref("Element/compositionupdate_event", "compositionupdate")}}
  - : هنگامی که یک کاراکتر جدید در زمینه یک جلسه ترکیب متنی که توسط یک سیستم ترکیب متن مانند یک {{glossary("input method editor")}} کنترل می‌شود، دریافت می‌شود، فعال می‌شود.

### رویدادهای فوکوس

- {{domxref("Element/blur_event", "blur")}}
  - : هنگامی که یک عنصر فوکوس خود را از دست داده است، فعال می‌شود.
- {{domxref("Element/focus_event", "focus")}}
  - : هنگامی که یک عنصر فوکوس گرفته است، فعال می‌شود.
- {{domxref("Element/focusin_event", "focusin")}}
  - : هنگامی که یک عنصر فوکوس گرفته است، پس از {{domxref("Element/focus_event", "focus")}}، فعال می‌شود.
- {{domxref("Element/focusout_event", "focusout")}}
  - : هنگامی که یک عنصر فوکوس خود را از دست داده است، پس از {{domxref("Element/blur_event", "blur")}}، فعال می‌شود.

### رویدادهای تمام‌صفحه

- {{domxref("Element/fullscreenchange_event", "fullscreenchange")}}
  - : به یک `Element` هنگامی که به حالت [تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API/Guide) وارد یا از آن خارج می‌شود، ارسال می‌شود.
- {{domxref("Element/fullscreenerror_event", "fullscreenerror")}}
  - : به یک `Element` در صورت بروز خطا در حین تلاش برای تغییر آن به حالت [تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API/Guide) یا خارج شدن از آن، ارسال می‌شود.

### رویدادهای صفحه‌کلید

- {{domxref("Element/keydown_event", "keydown")}}
  - : هنگامی که یک کلید فشار داده می‌شود، فعال می‌شود.
- {{domxref("Element/keypress_event", "keypress")}} {{Deprecated_Inline}}
  - : هنگامی که یک کلید که یک مقدار کاراکتر تولید می‌کند، فشار داده می‌شود، فعال می‌شود.
- {{domxref("Element/keyup_event", "keyup")}}
  - : هنگامی که یک کلید رها می‌شود، فعال می‌شود.

### رویدادهای ماوس

- {{domxref("Element/auxclick_event", "auxclick")}}
  - : هنگامی که یک دکمه دستگاه اشاره‌گر غیراصلی (مثلاً هر دکمه ماوس به جز دکمه چپ) روی یک عنصر فشار داده شده و رها می‌شود، فعال می‌شود.
- {{domxref("Element/click_event", "click")}}
  - : هنگامی که یک دکمه دستگاه اشاره‌گر (مثلاً دکمه اصلی ماوس) روی یک عنصر فشار داده شده و رها می‌شود، فعال می‌شود.
- {{domxref("Element/contextmenu_event", "contextmenu")}}
  - : هنگامی که کاربر سعی می‌کند یک منوی زمینه را باز کند، فعال می‌شود.
- {{domxref("Element/dblclick_event", "dblclick")}}
  - : هنگامی که یک دکمه دستگاه اشاره‌گر (مثلاً دکمه اصلی ماوس) دو بار روی یک عنصر کلیک می‌شود، فعال می‌شود.
- {{domxref("Element/DOMActivate_event", "DOMActivate")}} {{Deprecated_Inline}}
  - : زمانی رخ می‌دهد که یک عنصر فعال می‌شود، برای مثال، از طریق کلیک ماوس یا فشار دادن کلید.
- {{domxref("Element/DOMMouseScroll_event", "DOMMouseScroll")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : زمانی رخ می‌دهد که چرخ ماوس یا دستگاه مشابهی کار می‌کند و مقدار انباشته پیمایش از آخرین رویداد بیش از 1 خط یا 1 صفحه است.
- {{domxref("Element/mousedown_event", "mousedown")}}
  - : هنگامی که یک دکمه دستگاه اشاره‌گر روی یک عنصر فشار داده می‌شود، فعال می‌شود.
- {{domxref("Element/mouseenter_event", "mouseenter")}}
  - : هنگامی که یک دستگاه اشاره‌گر (معمولاً ماوس) به عنصری که شنونده به آن متصل است منتقل می‌شود، فعال می‌شود.
- {{domxref("Element/mouseleave_event", "mouseleave")}}
  - : هنگامی که اشاره‌گر یک دستگاه اشاره‌گر (معمولاً ماوس) از عنصری که شنونده به آن متصل است خارج می‌شود، فعال می‌شود.
- {{domxref("Element/mousemove_event", "mousemove")}}
  - : هنگامی که یک دستگاه اشاره‌گر (معمولاً ماوس) در حال حرکت بر روی یک عنصر است، فعال می‌شود.
- {{domxref("Element/mouseout_event", "mouseout")}}
  - : هنگامی که یک دستگاه اشاره‌گر (معمولاً ماوس) از عنصری که شنونده به آن متصل است یا از یکی از فرزندان آن خارج می‌شود، فعال می‌شود.
- {{domxref("Element/mouseover_event", "mouseover")}}
  - : هنگامی که یک دستگاه اشاره‌گر به عنصری که شنونده به آن متصل است یا به یکی از فرزندان آن منتقل می‌شود، فعال می‌شود.
- {{domxref("Element/mouseup_event", "mouseup")}}
  - : هنگامی که یک دکمه دستگاه اشاره‌گر روی یک عنصر رها می‌شود، فعال می‌شود.
- {{domxref("Element/mousewheel_event", "mousewheel")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : هنگامی که چرخ ماوس یا دستگاه مشابهی کار می‌کند، فعال می‌شود.
- {{domxref("Element/MozMousePixelScroll_event", "MozMousePixelScroll")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : هنگامی که چرخ ماوس یا دستگاه مشابهی کار می‌کند، فعال می‌شود.
- {{domxref("Element/webkitmouseforcechanged_event", "webkitmouseforcechanged")}} {{Non-standard_Inline}}
  - : هر بار که مقدار فشار روی صفحه لمسی ترک‌پد تغییر می‌کند، فعال می‌شود.
- {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}} {{Non-standard_Inline}}
  - : پس از رویداد mousedown به محض اینکه فشار کافی برای واجد شرایط بودن به عنوان یک "کلیک فشاری" اعمال شده است، فعال می‌شود.
- {{domxref("Element/webkitmouseforcewillbegin_event", "webkitmouseforcewillbegin")}} {{Non-standard_Inline}}
  - : قبل از رویداد {{domxref("Element/mousedown_event", "mousedown")}} فعال می‌شود.
- {{domxref("Element/webkitmouseforceup_event", "webkitmouseforceup")}} {{Non-standard_Inline}}
  - : پس از رویداد {{domxref("Element/webkitmouseforcedown_event", "webkitmouseforcedown")}} به محض اینکه فشار به اندازه کافی برای پایان دادن به "کلیک فشاری" کاهش یافته است، فعال می‌شود.

### رویدادهای اشاره‌گر

- {{domxref("Element/gotpointercapture_event", "gotpointercapture")}}
  - : هنگامی که یک عنصر یک اشاره‌گر را با استفاده از {{domxref("Element/setPointerCapture", "setPointerCapture()")}} ضبط می‌کند، فعال می‌شود.
- {{domxref("Element/lostpointercapture_event", "lostpointercapture")}}
  - : هنگامی که یک [اشاره‌گر ضبط‌شده](/en-US/docs/Web/API/Pointer_events#pointer_capture) آزاد می‌شود، فعال می‌شود.
- {{domxref("Element/pointercancel_event", "pointercancel")}}
  - : هنگامی که یک رویداد اشاره‌گر لغو می‌شود، فعال می‌شود.
- {{domxref("Element/pointerdown_event", "pointerdown")}}
  - : هنگامی که یک اشاره‌گر فعال می‌شود، فعال می‌شود.
- {{domxref("Element/pointerenter_event", "pointerenter")}}
  - : هنگامی که یک اشاره‌گر به داخل مرزهای تست ضربه یک عنصر یا یکی از نوادگان آن منتقل می‌شود، فعال می‌شود.
- {{domxref("Element/pointerleave_event", "pointerleave")}}
  - : هنگامی که یک اشاره‌گر از مرزهای تست ضربه یک عنصر خارج می‌شود، فعال می‌شود.
- {{domxref("Element/pointermove_event", "pointermove")}}
  - : هنگامی که یک اشاره‌گر مختصات خود را تغییر می‌دهد، فعال می‌شود.
- {{domxref("Element/pointerout_event", "pointerout")}}
  - : هنگامی که یک اشاره‌گر از مرزهای _تست ضربه_ یک عنصر خارج می‌شود (در میان دلایل دیگر)، فعال می‌شود.
- {{domxref("Element/pointerover_event", "pointerover")}}
  - : هنگامی که یک اشاره‌گر به داخل مرزهای تست ضربه یک عنصر منتقل می‌شود، فعال می‌شود.
- {{domxref("Element/pointerrawupdate_event", "pointerrawupdate")}}
  - : هنگامی که یک اشاره‌گر هر ویژگی‌ای را که باعث فعال شدن رویدادهای {{domxref("Element/pointerdown_event", "pointerdown")}} یا {{domxref("Element/pointerup_event", "pointerup")}} نمی‌شود، تغییر می‌دهد، فعال می‌شود.
- {{domxref("Element/pointerup_event", "pointerup")}}
  - : هنگامی که یک اشاره‌گر دیگر فعال نیست، فعال می‌شود.

### رویدادهای پیمایش

- {{domxref("Element/scroll_event", "scroll")}}
  - : هنگامی که نمای سند یا یک عنصر پیمایش شده است، فعال می‌شود.
- {{domxref("Element/scrollend_event", "scrollend")}}
  - : هنگامی که نمای سند پیمایش را کامل کرده است، فعال می‌شود.
- {{domxref("Element/scrollsnapchange_event", "scrollsnapchange")}} {{experimental_inline}}
  - : روی ظرف پیمایش در پایان یک عملیات پیمایش زمانی که یک هدف جدید snap پیمایش انتخاب شده است، فعال می‌شود.
- {{domxref("Element/scrollsnapchanging_event", "scrollsnapchanging")}} {{experimental_inline}}
  - : روی ظرف پیمایش هنگامی که مرورگر تشخیص می‌دهد یک هدف جدید snap پیمایش در انتظار است، یعنی زمانی که حرکت پیمایش فعلی پایان یابد انتخاب خواهد شد، فعال می‌شود.

### رویدادهای لمسی

- {{domxref("Element/gesturechange_event","gesturechange")}} {{Non-standard_Inline}}
  - : هنگامی که انگشتان در طول یک حرکت لمسی حرکت می‌کنند، فعال می‌شود.
- {{domxref("Element/gestureend_event","gestureend")}} {{Non-standard_Inline}}
  - : هنگامی که دیگر انگشتان متعددی با سطح لمسی در تماس نیستند، بنابراین حرکت پایان می‌یابد، فعال می‌شود.
- {{domxref("Element/gesturestart_event","gesturestart")}} {{Non-standard_Inline}}
  - : هنگامی که انگشتان متعدد با سطح لمسی تماس برقرار می‌کنند، بنابراین یک حرکت جدید شروع می‌شود، فعال می‌شود.
- {{domxref("Element/touchcancel_event", "touchcancel")}}
  - : هنگامی که یک یا چند نقطه لمسی به روشی خاص پیاده‌سازی مختل شده‌اند (به عنوان مثال، تعداد نقاط لمسی بیش از حد ایجاد شده است)، فعال می‌شود.
- {{domxref("Element/touchend_event", "touchend")}}
  - : هنگامی که یک یا چند نقطه لمسی از سطح لمسی حذف می‌شوند، فعال می‌شود.
- {{domxref("Element/touchmove_event", "touchmove")}}
  - : هنگامی که یک یا چند نقطه لمسی در امتداد سطح لمسی حرکت می‌کنند، فعال می‌شود.
- {{domxref("Element/touchstart_event", "touchstart")}}
  - : هنگامی که یک یا چند نقطه لمسی روی سطح لمسی قرار می‌گیرند، فعال می‌شود.

### رویدادهای انتقال

- {{domxref("Element/transitioncancel_event", "transitioncancel")}}
  - : یک {{domxref("Event")}} که هنگامی که یک [انتقال CSS](/en-US/docs/Web/CSS/Guides/Transitions) لغو شده است، فعال می‌شود.
- {{domxref("Element/transitionend_event", "transitionend")}}
  - : یک {{domxref("Event")}} که هنگامی که یک [انتقال CSS](/en-US/docs/Web/CSS/Guides/Transitions) پخش آن به پایان رسیده است، فعال می‌شود.
- {{domxref("Element/transitionrun_event", "transitionrun")}}
  - : یک {{domxref("Event")}} که هنگامی که یک [انتقال CSS](/en-US/docs/Web/CSS/Guides/Transitions) ایجاد می‌شود (یعنی زمانی که به مجموعه انتقال‌های در حال اجرا اضافه می‌شود)، هرچند لزوماً شروع نشده است، فعال می‌شود.
- {{domxref("Element/transitionstart_event", "transitionstart")}}
  - : یک {{domxref("Event")}} که هنگامی که یک [انتقال CSS](/en-US/docs/Web/CSS/Guides/Transitions) شروع به انتقال کرده است، فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
```