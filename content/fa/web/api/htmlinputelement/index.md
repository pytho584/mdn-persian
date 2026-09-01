---
title: HTMLInputElement
slug: Web/API/HTMLInputElement
page-type: web-api-interface
browser-compat: api.HTMLInputElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLInputElement`** ویژگی‌ها و روش‌های ویژه‌ای را برای دستکاری گزینه‌ها، طرح‌بندی و نمایش عناصر {{HTMLElement("input")}} فراهم می‌کند.

{{InheritanceDiagram}}

## Instance properties

_همچنین ویژگی‌های رابط والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

برخی ویژگی‌ها فقط برای انواع عنصر ورودی که صفت‌های متناظر را پشتیبانی می‌کنند اعمال می‌شوند.

- {{domxref("HTMLInputElement.align", "align")}} {{Deprecated_Inline}}
  - : رشته‌ای که ترازبندی عنصر را نمایش می‌دهد. _به جای آن از CSS استفاده کنید._

- {{domxref("HTMLInputElement.alpha", "alpha")}} {{experimental_inline}}
  - : یک مقدار بولی که صفت [`alpha`](/en-US/docs/Web/HTML/Reference/Elements/input/color#alpha) عنصر را نمایش می‌دهد و نشان می‌دهد که آیا مؤلفه آلفای رنگ می‌تواند توسط کاربر نهایی دستکاری شود و لزومی ندارد که کاملاً کدر باشد.

- {{domxref("HTMLInputElement.colorSpace", "colorSpace")}}
  - : رشته‌ای که صفت [`colorspace`](/en-US/docs/Web/HTML/Reference/Elements/input/color#colorspace) عنصر را نشان می‌دهد و {{glossary("color space")}} رنگ CSS سریال‌شده (sRGB یا display-p3) را مشخص می‌کند.

- {{domxref("HTMLInputElement.defaultValue", "defaultValue")}}
  - : رشته‌ای که مقدار پیش‌فرض را همان‌طور که در HTML سازنده این شیء مشخص شده، نمایش می‌دهد.

- {{domxref("HTMLInputElement.dirName", "dirName")}}
  - : رشته‌ای که جهت (directionality) عنصر را نمایش می‌دهد.

- {{domxref("HTMLInputElement.incremental", "incremental")}} {{Non-standard_Inline}}
  - : یک مقدار بولی که حالت شلیک رویداد جستجو را نشان می‌دهد؛ اگر `true` باشد، رویداد با هر بار فشردن کلید یا کلیک بر دکمه لغو شلیک می‌شود؛ در غیر این صورت، هنگام فشردن <kbd>Enter</kbd> شلیک می‌شود.

- {{domxref("HTMLInputElement.labels", "labels")}} {{ReadOnlyInline}}
  - : فهرستی از عناصر {{ HTMLElement("label") }} را برمی‌گرداند که برچسب‌های این عنصر هستند.

- {{domxref("HTMLInputElement.list", "list")}} {{ReadOnlyInline}}
  - : عنصری را که صفت [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list) به آن اشاره می‌کند برمی‌گرداند. اگر هیچ عنصر HTML در همان درخت یافت نشود، این ویژگی ممکن است `null` باشد.

- {{domxref("HTMLInputElement.multiple", "multiple")}}
  - : یک مقدار بولی که صفت [`multiple`](/en-US/docs/Web/HTML/Reference/Elements/input#multiple) عنصر را نمایش می‌دهد و نشان می‌دهد که آیا بیش از یک مقدار ممکن است (مثلاً چند فایل).

- {{domxref("HTMLInputElement.name", "name")}}
  - : رشته‌ای که صفت [`name`](/en-US/docs/Web/HTML/Reference/Elements/input#name) عنصر را نشان می‌دهد؛ شامل نامی که عنصر را هنگام ارسال فرم شناسایی می‌کند.

- {{domxref("HTMLInputElement.popoverTargetAction", "popoverTargetAction")}}
  - : عملیات مورد نظر (`"hide"`، `"show"` یا `"toggle"`) روی یک عنصر popover که توسط یک عنصر {{HTMLElement("input")}} از نوع `type="button"` کنترل می‌شود را دریافت و تنظیم می‌کند. این ویژگی مقدار صفت HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/input#popovertargetaction) را منعکس می‌کند.

- {{domxref("HTMLInputElement.popoverTargetElement", "popoverTargetElement")}}
  - : عنصر popover را که قرار است از طریق یک عنصر {{HTMLElement("input")}} از نوع `type="button"` کنترل شود، دریافت و تنظیم می‌کند. معادل جاوااسکریپتی صفت HTML [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/input#popovertarget) است.

- {{domxref("HTMLInputElement.step", "step")}}
  - : رشته‌ای که صفت [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) عنصر را نشان می‌دهد؛ این صفت با [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) کار می‌کند تا افزایش‌های مجاز برای تنظیم یک مقدار عددی یا تاریخ-زمان را محدود کند. می‌تواند رشته `any` یا یک عدد اعشاری مثبت باشد. اگر روی `any` تنظیم نشده باشد، کنترل فقط مقادیری را می‌پذیرد که مضربی از مقدار step و بزرگ‌تر از حداقل باشند.

- {{domxref("HTMLInputElement.type", "type")}}
  - : رشته‌ای که صفت [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) عنصر را نشان می‌دهد و نوع کنترلی که نمایش داده می‌شود را مشخص می‌کند. برای مقادیر ممکن، به مستندات صفت [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) مراجعه کنید.

- {{domxref("HTMLInputElement.useMap", "useMap")}} {{Deprecated_Inline}}
  - : رشته‌ای که یک نقشه تصویر سمت کلاینت را نشان می‌دهد.

- {{domxref("HTMLInputElement.value", "value")}}
  - : رشته‌ای که مقدار فعلی کنترل را نشان می‌دهد. اگر کاربر مقداری متفاوت از مقدار مورد انتظار وارد کند، ممکن است این ویژگی یک رشته خالی برگرداند.

- {{domxref("HTMLInputElement.valueAsDate", "valueAsDate")}}
  - : یک {{jsxref("Date")}} که مقدار عنصر را به‌صورت تاریخ تفسیر می‌کند، یا اگر تبدیل ممکن نباشد `null` است.

- {{domxref("HTMLInputElement.valueAsNumber", "valueAsNumber")}}
  - : عددی که مقدار عنصر را نشان می‌دهد و به ترتیب به‌صورت یکی از موارد زیر تفسیر می‌شود: یک مقدار زمانی، یک عدد، یا اگر تبدیل ممکن نباشد `NaN`.

### Instance properties related to the parent form

- {{domxref("HTMLInputElement.form", "form")}} {{ReadOnlyInline}}
  - : یک ارجاع به عنصر والد {{HTMLElement("form")}} برمی‌گرداند.

- {{domxref("HTMLInputElement.formAction", "formAction")}}
  - : رشته‌ای که صفت [`formaction`](/en-US/docs/Web/HTML/Reference/Elements/input#formaction) عنصر را نشان می‌دهد؛ شامل URL برنامه‌ای که اطلاعات ارسالی عنصر را پردازش می‌کند. این ویژگی صفت [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) فرم والد را لغو می‌کند.

- {{domxref("HTMLInputElement.formEnctype", "formEnctype")}}
  - : رشته‌ای که صفت [`formenctype`](/en-US/docs/Web/HTML/Reference/Elements/input#formenctype) عنصر را نشان می‌دهد؛ شامل نوع محتوایی که برای ارسال فرم به سرور استفاده می‌شود. این ویژگی صفت [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) فرم والد را لغو می‌کند.

- {{domxref("HTMLInputElement.formMethod", "formMethod")}}
  - : رشته‌ای که صفت [`formmethod`](/en-US/docs/Web/HTML/Reference/Elements/input#formmethod) عنصر را نشان می‌دهد؛ شامل روش HTTP که مرورگر برای ارسال فرم استفاده می‌کند. این ویژگی صفت [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) فرم والد را لغو می‌کند.

- {{domxref("HTMLInputElement.formNoValidate", "formNoValidate")}}
  - : یک مقدار بولی که صفت [`formnovalidate`](/en-US/docs/Web/HTML/Reference/Elements/input#formnovalidate) عنصر را نشان می‌دهد و مشخص می‌کند که فرم هنگام ارسال نباید اعتبارسنجی شود. این ویژگی صفت [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) فرم والد را لغو می‌کند.

- {{domxref("HTMLInputElement.formTarget", "formTarget")}}
  - : رشته‌ای که صفت [`formtarget`](/en-US/docs/Web/HTML/Reference/Elements/input#formtarget) عنصر را نشان می‌دهد؛ شامل یک نام یا کلیدواژه که محل نمایش پاسخ دریافتی پس از ارسال فرم را مشخص می‌کند. این ویژگی صفت [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) فرم والد را لغو می‌کند.

### Instance properties that apply to any type of input element that is not hidden

- {{domxref("HTMLInputElement.disabled", "disabled")}}
  - : یک مقدار بولی که صفت [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/input#disabled) عنصر را نشان می‌دهد و مشخص می‌کند که کنترل برای تعامل در دسترس نیست. مقادیر ورودی همراه با فرم ارسال نخواهند شد. همچنین به [`readonly`](/en-US/docs/Web/HTML/Reference/Elements/input#readonly) مراجعه کنید.

- {{domxref("HTMLInputElement.required", "required")}}
  - : یک مقدار بولی که صفت [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) عنصر را نشان می‌دهد و مشخص می‌کند که کاربر باید قبل از ارسال فرم یک مقدار وارد کند.

- {{domxref("HTMLInputElement.validationMessage", "validationMessage")}} {{ReadOnlyInline}}
  - : یک پیام محلی‌سازی‌شده را برمی‌گرداند که محدودیت‌های اعتبارسنجی‌ای را توصیف می‌کند که کنترل آن‌ها را برآورده نمی‌کند (در صورت وجود). اگر کنترل کاندیدای اعتبارسنجی محدودیت نباشد ({{domxref("HTMLInputElement.willValidate", "willValidate")}} برابر `false` باشد) یا محدودیت‌های خود را برآورده کند، این رشته خالی است. این مقدار را می‌توان با متد {{domxref("HTMLInputElement.setCustomValidity()", "setCustomValidity()")}} تنظیم کرد.

- {{domxref("HTMLInputElement.validity", "validity")}} {{ReadOnlyInline}}
  - : وضعیت اعتبارسنجی فعلی عنصر را برمی‌گرداند.

- {{domxref("HTMLInputElement.willValidate", "willValidate")}} {{ReadOnlyInline}}
  - : برمی‌گرداند که آیا عنصر کاندیدای اعتبارسنجی محدودیت است یا خیر. اگر هر شرایطی آن را از اعتبارسنجی محدودیت منع کند، `false` است؛ از جمله: `type` آن یکی از `hidden`، `reset` یا `button` باشد، دارای یک جد {{HTMLElement("datalist")}} باشد یا ویژگی `disabled` آن `true` باشد.

### Instance properties that apply only to elements of type checkbox or radio

- {{domxref("HTMLInputElement.checked", "checked")}}
  - : یک مقدار بولی که وضعیت فعلی عنصر را نشان می‌دهد.

- {{domxref("HTMLInputElement.defaultChecked", "defaultChecked")}}
  - : یک مقدار بولی که وضعیت پیش‌فرض یک دکمه رادیویی یا چک‌باکس را همان‌طور که در HTML سازنده این شیء مشخص شده، نشان می‌دهد.

- {{domxref("HTMLInputElement.indeterminate", "indeterminate")}}
  - : یک مقدار بولی که نشان می‌دهد چک‌باکس یا دکمه رادیویی در حالت نامعین (indeterminate) قرار دارد یا خیر. برای چک‌باکس‌ها، اثر آن این است که ظاهر چک‌باکس به‌گونه‌ای محو/خاکستری می‌شود که نشان دهد حالت آن نامعین است (نه تیک خورده و نه بدون تیک). این ویژگی بر مقدار صفت `checked` تأثیر نمی‌گذارد و کلیک روی چک‌باکس مقدار را روی `false` قرار می‌دهد.

### Instance properties that apply only to elements of type image

- {{domxref("HTMLInputElement.alt", "alt")}}
  - : رشته‌ای که صفت [`alt`](/en-US/docs/Web/HTML/Reference/Elements/input#alt) عنصر را نشان می‌دهد؛ شامل متن جایگزین برای استفاده.

- {{domxref("HTMLInputElement.height", "height")}}
  - : رشته‌ای که صفت [`height`](/en-US/docs/Web/HTML/Reference/Elements/input#height) عنصر را نشان می‌دهد؛ ارتفاع تصویر نمایش‌داده‌شده برای دکمه را تعریف می‌کند.

- {{domxref("HTMLInputElement.src", "src")}}
  - : رشته‌ای که صفت [`src`](/en-US/docs/Web/HTML/Reference/Elements/input#src) عنصر را نشان می‌دهد؛ یک URI برای مکان تصویری که روی دکمه ارسال گرافیکی نمایش داده می‌شود را مشخص می‌کند.

- {{domxref("HTMLInputElement.width", "width")}}
  - : رشته‌ای که صفت [`width`](/en-US/docs/Web/HTML/Reference/Elements/input#width) عنصر را نشان می‌دهد؛ عرض تصویر نمایش‌داده‌شده برای دکمه را تعریف می‌کند.

### Instance properties that apply only to elements of type file

- {{domxref("HTMLInputElement.accept", "accept")}}
  - : رشته‌ای که صفت [`accept`](/en-US/docs/Web/HTML/Reference/Elements/input#accept) عنصر را نشان می‌دهد؛ شامل فهرستی از انواع فایل که با کاما جدا شده‌اند و می‌توانند انتخاب شوند.

- {{domxref("HTMLInputElement.capture", "capture")}}
  - : رشته‌ای که صفت [`capture`](/en-US/docs/Web/HTML/Reference/Elements/input#capture) عنصر را نشان می‌دهد؛ روش ورودی ضبط رسانه را در کنترل‌های بارگذاری فایل مشخص می‌کند.

- {{domxref("HTMLInputElement.files", "files")}}
  - : یک {{domxref("FileList")}} که فایل‌های انتخاب‌شده برای بارگذاری را نشان می‌دهد.

- {{domxref("HTMLInputElement.webkitdirectory", "webkitdirectory")}}
  - : یک مقدار بولی که صفت [`webkitdirectory`](/en-US/docs/Web/HTML/Reference/Elements/input#webkitdirectory) را نشان می‌دهد. اگر `true` باشد، رابط انتخاب فایل‌سیستم فقط دایرکتوری‌ها را به‌جای فایل‌ها می‌پذیرد.

- {{domxref("HTMLInputElement.webkitEntries", "webkitEntries")}} {{ReadOnlyInline}}
  - : فایل‌ها یا دایرکتوری‌های انتخاب‌شده فعلی را توصیف می‌کند.

### Instance properties that apply only to visible elements containing text or numbers

- {{domxref("HTMLInputElement.autocomplete", "autocomplete")}}
  - : رشته‌ای که صفت [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete) عنصر را نشان می‌دهد و مشخص می‌کند که آیا مقدار کنترل می‌تواند به‌طور خودکار توسط مرورگر تکمیل شود.

- {{domxref("HTMLInputElement.max", "max")}}
  - : رشته‌ای که صفت [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) عنصر را نشان می‌دهد؛ شامل حداکثر مقدار (عددی یا تاریخ-زمان) برای این مورد است که نباید از مقدار حداقل آن (صفت [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min)) کمتر باشد.

- {{domxref("HTMLInputElement.maxLength", "maxLength")}}
  - : عددی که صفت [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/input#maxlength) عنصر را نشان می‌دهد؛ شامل حداکثر تعداد نویسه‌ها (بر حسب نقاط کد یونیکد) که مقدار می‌تواند داشته باشد.

- {{domxref("HTMLInputElement.min", "min")}}
  - : رشته‌ای که صفت [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) عنصر را نشان می‌دهد؛ شامل حداقل مقدار (عددی یا تاریخ-زمان) برای این مورد است که نباید از حداکثر مقدار آن (صفت [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max)) بیشتر باشد.

- {{domxref("HTMLInputElement.minLength", "minLength")}}
  - : عددی که صفت [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/input#minlength) عنصر را نشان می‌دهد؛ شامل حداقل تعداد نویسه‌ها (بر حسب نقاط کد یونیکد) که مقدار می‌تواند داشته باشد.

- {{domxref("HTMLInputElement.pattern", "pattern")}}
  - : رشته‌ای که صفت [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) عنصر را نشان می‌دهد؛ شامل یک عبارت باقاعده که مقدار کنترل بر اساس آن بررسی می‌شود. برای توصیف الگو به کمک کاربر، از صفت [`title`](/en-US/docs/Web/HTML/Reference/Elements/input#title) استفاده کنید. این صفت فقط زمانی اعمال می‌شود که مقدار صفت [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) یکی از `text`، `search`، `tel`، `url` یا `email` باشد.

- {{domxref("HTMLInputElement.placeholder", "placeholder")}}
  - : رشته‌ای که صفت [`placeholder`](/en-US/docs/Web/HTML/Reference/Elements/input#placeholder) عنصر را نشان می‌دهد؛ شامل راهنمایی برای کاربر درباره آنچه می‌توان در کنترل وارد کرد. متن placeholder نباید شامل بازگشت به ابتدای سطر (carriage return) یا تغذیه خط (line-feed) باشد. این صفت فقط زمانی اعمال می‌شود که مقدار صفت [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) یکی از `text`، `search`، `tel`، `url` یا `email` باشد.

- {{domxref("HTMLInputElement.readOnly", "readOnly")}}
  - : یک مقدار بولی که صفت [`readonly`](/en-US/docs/Web/HTML/Reference/Elements/input#readonly) عنصر را نشان می‌دهد و مشخص می‌کند که کاربر نمی‌تواند مقدار کنترل را تغییر دهد. اگر [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) برابر `hidden`، `range`، `color`، `checkbox`، `radio`، `file` یا یکی از انواع دکمه باشد، این ویژگی نادیده گرفته می‌شود.

- {{domxref("HTMLInputElement.selectionDirection", "selectionDirection")}}
  - : رشته‌ای که جهتی را که انتخاب در آن انجام شده است نشان می‌دهد. مقادیر ممکن عبارتند از: `forward` (انتخاب در جهت شروع به پایانِ locale فعلی انجام شده)، `backward` (جهت مخالف) یا `none` (جهت ناشناخته است).

- {{domxref("HTMLInputElement.selectionEnd", "selectionEnd")}}
  - : عددی که اندیس پایان متن انتخاب‌شده را نشان می‌دهد. وقتی انتخابی وجود نداشته باشد، این ویژگی offset نویسه بلافاصله پس از موقعیت فعلی مکان‌نمای ورودی متن را برمی‌گرداند.

- {{domxref("HTMLInputElement.selectionStart", "selectionStart")}}
  - : عددی که اندیس آغاز متن انتخاب‌شده را نشان می‌دهد. وقتی چیزی انتخاب نشده باشد، این ویژگی موقعیت مکان‌نمای ورودی متن (caret) را در داخل عنصر {{HTMLElement("input")}} برمی‌گرداند.

- {{domxref("HTMLInputElement.size", "size")}}
  - : عددی که صفت [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) عنصر را نشان می‌دهد؛ شامل اندازه بصری کنترل. این مقدار بر حسب پیکسل است مگر اینکه مقدار [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) برابر `text` یا `password` باشد، که در آن صورت یک عدد صحیح از تعداد نویسه‌هاست. فقط زمانی اعمال می‌شود که [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) روی `text`، `search`، `tel`، `url`، `email` یا `password` تنظیم شده باشد.

## Instance methods

_همچنین روش‌های رابط والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLInputElement.checkValidity()", "checkValidity()")}}
  - : یک مقدار بولی برمی‌گرداند که اگر عنصر کاندیدای اعتبارسنجی محدودیت باشد و محدودیت‌های خود را برآورده نکند، `false` است. در این حالت، یک رویداد {{domxref("HTMLInputElement/invalid_event", "invalid")}} نیز روی عنصر شلیک می‌کند. اگر عنصر کاندیدای اعتبارسنجی محدودیت نباشد یا محدودیت‌های خود را برآورده کند، `true` برمی‌گرداند.

- {{domxref("HTMLInputElement.reportValidity()", "reportValidity()")}}
  - : متد `checkValidity()` را اجرا می‌کند و اگر false برگرداند (برای ورودی نامعتبر یا عدم وجود صفت pattern)، به کاربر گزارش می‌دهد که ورودی نامعتبر است، به همان شیوه‌ای که گویی فرم را ارسال کرده‌اید.

- {{domxref("HTMLInputElement.select()", "select()")}}
  - : تمام متن داخل عنصر ورودی را انتخاب می‌کند و آن را فوکوس می‌کند تا کاربر بتواند بعداً تمام محتوای آن را جایگزین کند.

- {{domxref("HTMLInputElement.setCustomValidity()", "setCustomValidity()")}}
  - : یک پیام اعتبارسنجی سفارشی برای عنصر تنظیم می‌کند. اگر این پیام رشته خالی نباشد، عنصر از خطای اعتبارسنجی سفارشی رنج می‌برد و اعتبارسنجی نمی‌شود.

- {{domxref("HTMLInputElement.setRangeText()", "setRangeText()")}}
  - : یک بازه از متن در عنصر ورودی را با متن جدید جایگزین می‌کند.

- {{domxref("HTMLInputElement.setSelectionRange()", "setSelectionRange()")}}
  - : یک بازه از متن در عنصر ورودی را انتخاب می‌کند (اما آن را فوکوس نمی‌کند).

- {{domxref("HTMLInputElement.showPicker()", "showPicker()")}}
  - : یک انتخابگر مرورگر برای تاریخ، زمان، رنگ و فایل‌ها نمایش می‌دهد.

- {{domxref("HTMLInputElement.stepDown()", "stepDown()")}}
  - : مقدار [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) را به اندازه ([`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) \* n) کاهش می‌دهد؛ اگر n مشخص نشده باشد، پیش‌فرض آن 1 است.

- {{domxref("HTMLInputElement.stepUp()", "stepUp()")}}
  - : مقدار [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) را به اندازه ([`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) \* n) افزایش می‌دهد؛ اگر n مشخص نشده باشد، پیش‌فرض آن 1 است.

## Events

_همچنین رویدادهای رابط والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

به این رویدادها با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید:

- {{domxref("HTMLInputElement/cancel_event", "cancel")}} event
  - : وقتی کاربر گفتگوی انتخاب فایل را از طریق کلید <kbd>Esc</kbd> یا دکمه لغو می‌بندد و همچنین وقتی کاربر همان فایل‌هایی را که قبلاً انتخاب شده بودند دوباره انتخاب می‌کند، شلیک می‌شود.
- {{domxref("HTMLInputElement/invalid_event", "invalid")}} event
  - : وقتی یک عنصر در طول اعتبارسنجی محدودیت، محدودیت‌های خود را برآورده نمی‌کند، شلیک می‌شود.
- {{domxref("HTMLInputElement/search_event", "search")}} event {{Non-standard_Inline}}
  - : وقتی یک جستجو روی یک {{HTMLElement("input")}} از نوع `type="search"` آغاز می‌شود، شلیک می‌شود.
- {{domxref("HTMLInputElement/select_event", "select")}} event
  - : وقتی متنی انتخاب شده است، شلیک می‌شود.
- {{domxref("HTMLInputElement/selectionchange_event", "selectionchange")}} event
  - : وقتی انتخاب متن در یک عنصر {{HTMLElement("input")}} تغییر کرده است، شلیک می‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- عنصر HTML پیاده‌ساز این رابط: {{HTMLElement("input")}}