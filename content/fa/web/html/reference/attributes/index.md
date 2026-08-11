---
title: "HTML attribute reference"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes"
translated_by: "n8n + AI"
---

## فهرست attributeها

المنت‌های HTML دارای **attribute** هستند؛ این‌ها مقادیر اضافی هستند که رفتار المنت‌ها را تنظیم می‌کنند یا آن‌ها را به روش‌های مختلف پیکربندی می‌کنند تا نیازهای موردنظر کاربران برآورده شود.

| نام ویژگی (Attribute Name) | عناصر (Elements) | توضیحات (Description) |
| --- | --- | --- |
| [`accept`](/en-US/docs/Web/HTML/Reference/Attributes/accept) | `<form>`، `<input>` | لیست نوع‌هایی که سرور می‌پذیرد، معمولاً یک نوع فایل. |
| [`accept-charset`](/en-US/docs/Web/HTML/Reference/Elements/form#accept-charset) | `<form>` | مجموعه کاراکترهایی که اگر مشخص شود، باید `"UTF-8"` باشد. |
| [`accesskey`](/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | میانبر صفحه‌کلید برای فعال کردن یا اضافه کردن focus به عنصر. |
| [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) | `<form>` | URI برنامه‌ای که اطلاعات ارسال‌شده از طریق فرم را پردازش می‌کند. |
| `align` {{deprecated_inline}} | `<caption>`، `<col>`، `<colgroup>`، `<hr>`، `<iframe>`، `<img>`، `<table>`، `<tbody>`، `<td>`، `<tfoot>`، `<th>`، `<thead>`، `<tr>` | تراز افقی عنصر را مشخص می‌کند. |
| [`allow`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allow) | `<iframe>` | یک feature-policy برای iframe مشخص می‌کند. |
| [`alpha`](/en-US/docs/Web/HTML/Reference/Elements/input/color#alpha) | `<input>` | به کاربر اجازه می‌دهد opacity رنگ را در ورودی `type="color"` انتخاب کند. |
| [`alt`](/en-US/docs/Web/HTML/Reference/Attributes/alt) | `<area>`، `<img>`، `<input>` | متن جایگزین در صورت عدم نمایش تصویر. |
| [`aria-*`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes) | همه عناصر | وضعیت یا ویژگی‌های عنصر را در درخت دسترسی‌پذیری تغییر می‌دهد. کاربرد به ویژگی ARIA خاص بستگی دارد. |
| [`as`](/en-US/docs/Web/HTML/Reference/Elements/link#as) | `<link>` | نوع محتوایی که توسط لینک بارگذاری می‌شود را مشخص می‌کند. |
| [`async`](/en-US/docs/Web/HTML/Reference/Elements/script#async) | `<script>` | اسکریپت را به‌صورت ناهمزمان اجرا می‌کند. |
| [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | مشخص می‌کند که آیا ورودی هنگام تایپ کاربر به‌طور خودکار با حرف بزرگ نوشته شود. |
| [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) | `<form>`، `<input>`، `<select>`، `<textarea>` | نشان می‌دهد که آیا کنترل‌های این فرم می‌توانند به‌طور پیش‌فرض توسط مرورگر به‌طور خودکار تکمیل شوند. |
| [`autoplay`](/en-US/docs/Web/HTML/Reference/Attributes/autoplay) | `<audio>`، `<video>` | صدا یا ویدیو باید در اسرع وقت پخش شود. |
| `background` | `<body>`، `<table>`، `<td>`، `<th>` | URL یک فایل تصویر را مشخص می‌کند. **توجه:** اگرچه مرورگرها و کلاینت‌های ایمیل ممکن است همچنان از این ویژگی پشتیبانی کنند، اما منسوخ شده است. به جای آن از ویژگی CSS `background-image` استفاده کنید. |
| `bgcolor` | `<body>`، `<col>`، `<colgroup>`، `<marquee>`، `<table>`، `<tbody>`، `<tfoot>`، `<td>`، `<th>`، `<tr>` | رنگ پس‌زمینه عنصر. **توجه:** این یک ویژگی قدیمی است. لطفاً از ویژگی CSS `background-color` استفاده کنید. |
| `border` | `<img>`، `<object>`، `<table>` | عرض حاشیه. **توجه:** این یک ویژگی قدیمی است. لطفاً از ویژگی CSS `border` استفاده کنید. |
| [`capture`](/en-US/docs/Web/HTML/Reference/Attributes/capture) | `<input>` | از [مشخصات Media Capture](https://w3c.github.io/html-media-capture/#the-capture-attribute)، مشخص می‌کند که یک فایل جدید می‌تواند ضبط شود. |
| [`charset`](/en-US/docs/Web/HTML/Reference/Elements/meta#charset) | `<meta>` | رمزگذاری کاراکتر صفحه یا اسکریپت را اعلام می‌کند. |
| [`checked`](/en-US/docs/Web/HTML/Reference/Elements/input#checked) | `<input>` | نشان می‌دهد که آیا عنصر باید در بارگذاری صفحه انتخاب شده باشد. |
| [`cite`](/en-US/docs/Web/HTML/Reference/Attributes/cite) | `<blockquote>`، `<del>`، `<ins>`، `<q>` | شامل یک URI است که به منبع نقل‌قول یا تغییر اشاره می‌کند. |
| [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | اغلب با CSS برای استایل‌دهی به عناصر با ویژگی‌های مشترک استفاده می‌شود. |
| `color` | `<font>`، `<hr>` | این ویژگی رنگ متن را با استفاده از یک رنگ نام‌گذاری شده یا رنگی که در قالب هگزادسیمال #RRGGBB مشخص شده است، تنظیم می‌کند. **توجه:** این یک ویژگی قدیمی است. لطفاً از ویژگی CSS `color` استفاده کنید. |
| [`colorspace`](/en-US/docs/Web/HTML/Reference/Elements/input/color#colorspace) | `<input>` | [فضای رنگی](/en-US/docs/Glossary/Color_space) که توسط ورودی `type="color"` استفاده می‌شود را تعریف می‌کند. |
| [`cols`](/en-US/docs/Web/HTML/Reference/Elements/textarea#cols) | `<textarea>` | تعداد ستون‌ها در یک textarea را تعریف می‌کند. |
| [`colspan`](/en-US/docs/Web/HTML/Reference/Attributes/colspan) | `<td>`، `<th>` | ویژگی colspan تعداد ستون‌هایی که یک سلول باید گسترش یابد را تعریف می‌کند. |
| [`content`](/en-US/docs/Web/HTML/Reference/Attributes/content) | `<meta>` | مقداری مرتبط با `http-equiv` یا `name` بسته به زمینه. |
| [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | نشان می‌دهد که آیا محتوای عنصر قابل ویرایش است. |
| [`controls`](/en-US/docs/Web/HTML/Reference/Attributes/controls) | `<audio>`، `<video>` | نشان می‌دهد که آیا مرورگر باید کنترل‌های پخش را به کاربر نشان دهد. |
| [`coords`](/en-US/docs/Web/HTML/Reference/Elements/area#coords) | `<area>` | مجموعه‌ای از مقادیر که مختصات ناحیه فعال را مشخص می‌کند. |
| [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) | `<audio>`، `<img>`، `<link>`، `<script>`، `<video>` | نحوه مدیریت درخواست‌های cross-origin توسط عنصر. |
| [`csp`](/en-US/docs/Web/API/HTMLIFrameElement/csp) {{experimental_inline}} | `<iframe>` | خط مشی امنیت محتوا (Content Security Policy) را مشخص می‌کند که یک سند جاسازی‌شده باید آن را بر روی خود اعمال کند. |
| [`data`](/en-US/docs/Web/HTML/Reference/Elements/object#data) | `<object>` | URL منبع را مشخص می‌کند. |
| [`data-*`](/en-US/docs/Web/HTML/Reference/Global_attributes/data-*) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | به شما امکان می‌دهد ویژگی‌های سفارشی به یک عنصر HTML متصل کنید. |
| [`datetime`](/en-US/docs/Web/HTML/Reference/Attributes/datetime) | `<del>`، `<ins>`، `<time>` | تاریخ و زمان مرتبط با عنصر را نشان می‌دهد. |
| [`decoding`](/en-US/docs/Web/HTML/Reference/Elements/img#decoding) | `<img>` | روش ترجیحی برای رمزگشایی تصویر را نشان می‌دهد. |
| [`default`](/en-US/docs/Web/HTML/Reference/Elements/track#default) | `<track>` | نشان می‌دهد که track باید فعال شود مگر اینکه ترجیحات کاربر خلاف آن را نشان دهد. |
| [`defer`](/en-US/docs/Web/HTML/Reference/Elements/script#defer) | `<script>` | نشان می‌دهد که اسکریپت باید پس از تجزیه صفحه اجرا شود. |
| [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | جهت متن را تعریف می‌کند. مقادیر مجاز: ltr (چپ به راست) یا rtl (راست به چپ). |
| [`dirname`](/en-US/docs/Web/HTML/Reference/Attributes/dirname) | `<input>`، `<textarea>` | — |
| [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled) | `<button>`، `<fieldset>`، `<input>`، `<optgroup>`، `<option>`، `<select>`، `<textarea>` | نشان می‌دهد که آیا کاربر می‌تواند با عنصر تعامل داشته باشد. |
| [`download`](/en-US/docs/Web/HTML/Reference/Attributes/download) | `<a>`، `<area>` | نشان می‌دهد که هایپرلینک برای دانلود یک منبع استفاده می‌شود. |
| [`draggable`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | تعریف می‌کند که آیا عنصر قابل کشیدن است. |
| [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) | `<form>` | نوع محتوای داده‌های فرم را زمانی که `method` برابر POST است تعریف می‌کند. |
| [`enterkeyhint`](/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint) | `<textarea>`، [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) | [`enterkeyhint`](https://html.spec.whatwg.org/multipage/interaction.html#input-modalities:-the-enterkeyhint-attribute) مشخص می‌کند که چه برچسب عملی (یا آیکونی) برای کلید Enter در صفحه‌کلیدهای مجازی نمایش داده شود. این ویژگی می‌تواند با کنترل‌های فرم (مانند مقدار عناصر `<textarea>`) یا در عناصر میزبان ویرایش (مثلاً با استفاده از ویژگی `contenteditable`) استفاده شود. |
| [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) | `<img>`، عناصر `<image>` درون `<svg>`، تصاویر پوستر `<video>`، عناصر دارای `background-image` و عناصر حاوی گره‌های متنی مانند `<p>` | نشان می‌دهد که یک عنصر برای ردیابی توسط اشیاء `PerformanceObserver` با استفاده از نوع `"element"` علامت‌گذاری شده است. برای جزئیات بیشتر، به رابط `PerformanceElementTiming` مراجعه کنید. |
| [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority) | `<img>`، `<link>`، `<script>` | نشان می‌دهد که واکشی یک تصویر خاص در مراحل اولیه بارگذاری تأثیر بیشتری بر تجربه کاربری دارد نسبت به آنچه مرورگر به طور منطقی می‌تواند هنگام تعیین اولویت داخلی استنباط کند. |
| [`for`](/en-US/docs/Web/HTML/Reference/Attributes/for) | `<label>`، `<output>` | عناصری که به این عنصر تعلق دارند را توصیف می‌کند. |
| [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form) | `<button>`، `<fieldset>`، `<input>`، `<object>`، `<output>`، `<select>`، `<textarea>` | فرمی که مالک عنصر است را نشان می‌دهد. |
| [`formaction`](/en-US/docs/Web/HTML/Reference/Attributes/formaction) | `<input>`، `<button>` | عمل عنصر را مشخص می‌کند و عمل تعریف‌شده در `<form>` را نادیده می‌گیرد. |
| [`formenctype`](/en-US/docs/Web/HTML/Reference/Attributes/formenctype) | `<button>`، `<input>` | اگر دکمه/ورودی یک [دکمه ارسال (submit button)](/en-US/docs/Glossary/Submit_button) باشد (مثلاً `type="submit"`)، این ویژگی نوع رمزگذاری را برای استفاده در هنگام ارسال فرم تنظیم می‌کند. اگر این ویژگی مشخص شود، ویژگی `enctype` فرم مالک دکمه را نادیده می‌گیرد. |
| [`formmethod`](/en-US/docs/Web/HTML/Reference/Attributes/formmethod) | `<button>`، `<input>` | اگر دکمه/ورودی یک دکمه ارسال باشد (مثلاً `type="submit"`)، این ویژگی روش ارسال را برای استفاده در هنگام ارسال فرم تنظیم می‌کند (`GET`، `POST` و غیره). اگر این ویژگی مشخص شود، ویژگی `method` فرم مالک دکمه را نادیده می‌گیرد. |
| [`formnovalidate`](/en-US/docs/Web/HTML/Reference/Attributes/formnovalidate) | `<button>`، `<input>` | اگر دکمه/ورودی یک دکمه ارسال باشد (مثلاً `type="submit"`)، این ویژگی بولی مشخص می‌کند که فرم در هنگام ارسال اعتبارسنجی نشود. اگر این ویژگی مشخص شود، ویژگی `novalidate` فرم مالک دکمه را نادیده می‌گیرد. |
| [`formtarget`](/en-US/docs/Web/HTML/Reference/Attributes/formtarget) | `<button>`، `<input>` | اگر دکمه/ورودی یک دکمه ارسال باشد (مثلاً `type="submit"`)، این ویژگی زمینه مرور (مثلاً تب، پنجره یا فریم درون‌خطی) را مشخص می‌کند که در آن پاسخی که پس از ارسال فرم دریافت می‌شود نمایش داده شود. اگر این ویژگی مشخص شود، ویژگی `target` فرم مالک دکمه را نادیده می‌گیرد. |
| [`headers`](/en-US/docs/Web/HTML/Reference/Attributes/headers) | `<td>`، `<th>` | شناسه‌های عناصر `<th>` که برای این عنصر اعمال می‌شوند. |
| `height` | `<canvas>`، `<embed>`، `<iframe>`، `<img>`، `<input>`، `<object>`، `<video>` | ارتفاع عناصر ذکر شده را مشخص می‌کند. برای سایر عناصر، از ویژگی CSS `height` استفاده کنید. **توجه:** در برخی موارد مانند `<div>`، این یک ویژگی قدیمی است و باید از ویژگی CSS `height` استفاده شود. |
| [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | از رندر شدن عنصر جلوگیری می‌کند، در حالی که عناصر فرزند (مانند عناصر script) فعال باقی می‌مانند. |
| [`high`](/en-US/docs/Web/HTML/Reference/Elements/meter#high) | `<meter>` | کران پایین محدوده بالایی را نشان می‌دهد. |
| [`href`](/en-US/docs/Web/HTML/Reference/Attributes/href) | `<a>`، `<area>`، `<base>`، `<link>` | URL یک منبع لینک‌شده. |
| [`hreflang`](/en-US/docs/Web/HTML/Reference/Attributes/hreflang) | `<a>`، `<link>` | زبان منبع لینک‌شده را مشخص می‌کند. |
| [`http-equiv`](/en-US/docs/Web/HTML/Reference/Elements/meta/http-equiv) | `<meta>` | یک دستور pragma را تعریف می‌کند. |
| [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | اغلب با CSS برای استایل‌دهی به یک عنصر خاص استفاده می‌شود. مقدار این ویژگی باید یکتا باشد. |
| [`integrity`](/en-US/docs/Web/HTML/Reference/Attributes/integrity) | `<link>`، `<script>` | این ویژگی شامل یک یا چند [هش](/en-US/docs/Glossary/Hash_function) از منبع است و برای اطمینان از اینکه محتوای منبع همان چیزی است که توسعه‌دهنده انتظار دارد و با یک کپی مخرب در یک [حمله زنجیره تأمین](/en-US/docs/Web/Security/Attacks/Supply_chain_attacks) جایگزین نشده است، استفاده می‌شود. به [یکپارچگی زیرمنبع (Subresource Integrity)](/en-US/docs/Web/Security/Defenses/Subresource_Integrity) مراجعه کنید. |
| [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode) | `<textarea>`، [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) | یک راهنمایی در مورد نوع داده‌ای که ممکن است توسط کاربر در حین ویرایش عنصر یا محتوای آن وارد شود، ارائه می‌دهد. این ویژگی می‌تواند با کنترل‌های فرم (مانند مقدار عناصر `<textarea>`) یا در عناصر میزبان ویرایش (مثلاً با استفاده از ویژگی `contenteditable`) استفاده شود. |
| [`ismap`](/en-US/docs/Web/HTML/Reference/Elements/img#ismap) | `<img>` | نشان می‌دهد که تصویر بخشی از یک نقشه تصویری سمت سرور است. |
| [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | — |
| [`kind`](/en-US/docs/Web/HTML/Reference/Elements/track#kind) | `<track>` | نوع track متنی را مشخص می‌کند. |
| [`label`](/en-US/docs/Web/HTML/Reference/Attributes/label) | `<optgroup>`، `<option>`، `<track>` | عنوان قابل خواندن برای کاربر از عنصر را مشخص می‌کند. |
| [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | زبان استفاده‌شده در عنصر را تعریف می‌کند. |
| `language` {{deprecated_inline}} | `<script>` | زبان اسکریپت استفاده‌شده در عنصر را تعریف می‌کند. |
| `loading` | `<img>`، `<iframe>` | نشان می‌دهد که عنصر باید به صورت تنبل (lazy) بارگذاری شود (`loading="lazy"`) یا بلافاصله (`loading="eager"`). |
| [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list) | `<input>` | لیستی از گزینه‌های از پیش تعریف‌شده برای پیشنهاد به کاربر را مشخص می‌کند. |
| [`loop`](/en-US/docs/Web/HTML/Reference/Attributes/loop) | `<audio>`، `<marquee>`، `<video>` | نشان می‌دهد که آیا رسانه باید پس از اتمام از ابتدا پخش شود. |
| [`low`](/en-US/docs/Web/HTML/Reference/Elements/meter#low) | `<meter>` | کران بالای محدوده پایینی را نشان می‌دهد. |
| [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max) | `<input>`، `<meter>`، `<progress>` | حداکثر مقدار مجاز را نشان می‌دهد. |
| [`maxlength`](/en-US/docs/Web/HTML/Reference/Attributes/maxlength) | `<input>`، `<textarea>` | حداکثر تعداد کاراکترهای مجاز در عنصر را تعریف می‌کند. |
| [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength) | `<input>`، `<textarea>` | حداقل تعداد کاراکترهای مجاز در عنصر را تعریف می‌کند. |
| [`media`](/en-US/docs/Web/HTML/Reference/Attributes/media) | `<a>`، `<area>`، `<link>`، `<source>`، `<style>` | یک راهنمایی از رسانه‌ای که منبع لینک‌شده برای آن طراحی شده است را مشخص می‌کند. |
| [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) | `<form>` | تعریف می‌کند که از کدام روش [HTTP](/en-US/docs/Web/HTTP) برای ارسال فرم استفاده شود. می‌تواند `GET` (پیش‌فرض) یا `POST` باشد. |
| [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) | `<input>`، `<meter>` | حداقل مقدار مجاز را نشان می‌دهد. |
| [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple) | `<input>`، `<select>` | نشان می‌دهد که آیا می‌توان مقادیر متعددی را در یک ورودی از نوع `email` یا `file` وارد کرد. |
| [`muted`](/en-US/docs/Web/HTML/Reference/Attributes/muted) | `<audio>`، `<video>` | نشان می‌دهد که آیا صدا در بارگذاری صفحه ابتدا بی‌صدا می‌شود. |
| [`name`](/en-US/docs/Web/HTML/Reference/Attributes/name) | `<button>`، `<form>`، `<fieldset>`، `<iframe>`، `<input>`، `<object>`، `<output>`، `<select>`، `<textarea>`، `<map>`، `<meta>`، `<param>` | نام عنصر. به عنوان مثال توسط سرور برای شناسایی فیلدها در ارسال‌های فرم استفاده می‌شود. |
| [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) | `<form>` | این ویژگی نشان می‌دهد که فرم در هنگام ارسال نباید اعتبارسنجی شود. |
| [`open`](/en-US/docs/Web/HTML/Reference/Attributes/open) | `<details>`، `<dialog>` | نشان می‌دهد که آیا محتوا در حال حاضر قابل مشاهده است (در مورد عنصر `<details>`) یا اینکه دیالوگ فعال است و می‌توان با آن تعامل کرد (در مورد عنصر `<dialog>`). |
| [`optimum`](/en-US/docs/Web/HTML/Reference/Elements/meter#optimum) | `<meter>` | مقدار عددی بهینه را نشان می‌دهد. |
| [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern) | `<input>` | یک عبارت منظم را تعریف می‌کند که مقدار عنصر در برابر آن اعتبارسنجی می‌شود. |
| [`ping`](/en-US/docs/Web/HTML/Reference/Elements/a#ping) | `<a>`، `<area>` | ویژگی `ping` یک لیست جدا شده با فاصله از URLهایی را مشخص می‌کند که در صورت دنبال کردن هایپرلینک توسط کاربر مطلع شوند. |
| [`placeholder`](/en-US/docs/Web/HTML/Reference/Attributes/placeholder) | `<input>`، `<textarea>` | یک راهنما به کاربر در مورد آنچه می‌تواند در فیلد وارد کند ارائه می‌دهد. |
| [`playsinline`](/en-US/docs/Web/HTML/Reference/Elements/video#playsinline) | `<video>` | یک ویژگی بولی که نشان می‌دهد ویدیو باید به صورت "درون‌خطی" پخش شود؛ یعنی در ناحیه پخش عنصر. توجه داشته باشید که عدم وجود این ویژگی به این معنی نیست که ویدیو همیشه به صورت تمام‌صفحه پخش می‌شود. |
| [`poster`](/en-US/docs/Web/HTML/Reference/Elements/video#poster) | `<video>` | یک URL که یک فریم پوستر را نشان می‌دهد تا زمانی که کاربر پخش کند یا جستجو کند. |
| [`preload`](/en-US/docs/Web/HTML/Reference/Attributes/preload) | `<audio>`، `<video>` | نشان می‌دهد که آیا کل منبع، بخشی از آن یا هیچ چیز باید از پیش بارگذاری شود. |
| [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly) | `<input>`، `<textarea>` | نشان می‌دهد که آیا عنصر قابل ویرایش است. |
| [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Attributes/referralpolicy) | `<a>`، `<area>`، `<iframe>`، `<img>`، `<link>`، `<script>` | مشخص می‌کند که کدام مرجع (referrer) هنگام واکشی منبع ارسال می‌شود. |
| [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) | `<a>`، `<area>`، `<link>` | رابطه شیء هدف با شیء لینک را مشخص می‌کند. |
| [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) | `<input>`، `<select>`، `<textarea>` | نشان می‌دهد که آیا این عنصر باید پر شود یا خیر. |
| [`reversed`](/en-US/docs/Web/HTML/Reference/Elements/ol#reversed) | `<ol>` | نشان می‌دهد که آیا لیست باید به جای ترتیب صعودی به ترتیب نزولی نمایش داده شود. |
| [`role`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | یک نقش صریح برای یک عنصر برای استفاده توسط فناوری‌های کمکی تعریف می‌کند. |
| [`rows`](/en-US/docs/Web/HTML/Reference/Elements/textarea#rows) | `<textarea>` | تعداد ردیف‌ها در یک ناحیه متنی را تعریف می‌کند. |
| [`rowspan`](/en-US/docs/Web/HTML/Reference/Attributes/rowspan) | `<td>`، `<th>` | تعداد ردیف‌هایی که یک سلول جدول باید گسترش یابد را تعریف می‌کند. |
| [`sandbox`](/en-US/docs/Web/HTML/Reference/Elements/iframe#sandbox) | `<iframe>` | از استفاده یک سند بارگذاری‌شده در iframe از برخی ویژگی‌ها (مانند ارسال فرم یا باز کردن پنجره‌های جدید) جلوگیری می‌کند. |
| [`scope`](/en-US/docs/Web/HTML/Reference/Elements/th#scope) | `<th>` | سلول‌هایی که هدر تست (تعریف‌شده در عنصر `th`) به آنها مربوط می‌شود را تعریف می‌کند. |
| [`selected`](/en-US/docs/Web/HTML/Reference/Elements/option#selected) | `<option>` | مقداری را تعریف می‌کند که در بارگذاری صفحه انتخاب می‌شود. |
| [`shape`](/en-US/docs/Web/HTML/Reference/Attributes/shape) | `<a>`، `<area>` | — |
| [`size`](/en-US/docs/Web/HTML/Reference/Attributes/size) | `<input>`، `<select>` | عرض عنصر (بر حسب پیکسل) را تعریف می‌کند. اگر ویژگی `type` عنصر برابر `text` یا `password` باشد، تعداد کاراکترها است. |
| [`sizes`](/en-US/docs/Web/HTML/Reference/Attributes/sizes) | `<link>`، `<img>`، `<source>` | — |
| [`slot`](/en-US/docs/Web/HTML/Reference/Global_attributes/slot) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | یک slot را در درخت سایه DOM shadow به یک عنصر اختصاص می‌دهد. |
| [`span`](/en-US/docs/Web/HTML/Reference/Attributes/span) | `<col>`، `<colgroup>` | — |
| [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | نشان می‌دهد که آیا بررسی املا برای عنصر مجاز است. |
| [`src`](/en-US/docs/Web/HTML/Reference/Attributes/src) | `<audio>`، `<embed>`، `<iframe>`، `<img>`، `<input>`، `<script>`، `<source>`، `<track>`، `<video>` | URL محتوای قابل جاسازی. |
| [`srcdoc`](/en-US/docs/Web/HTML/Reference/Elements/iframe#srcdoc) | `<iframe>` | — |
| [`srclang`](/en-US/docs/Web/HTML/Reference/Elements/track#srclang) | `<track>` | — |
| [`srcset`](/en-US/docs/Web/HTML/Reference/Attributes/srcset) | `<img>`، `<source>` | یک یا چند نامزد تصویر واکنش‌گرا. |
| [`start`](/en-US/docs/Web/HTML/Reference/Elements/ol#start) | `<ol>` | اولین عدد را اگر غیر از 1 باشد تعریف می‌کند. |
| [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) | `<input>` | — |
| [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | استایل‌های CSS را تعریف می‌کند که استایل‌های قبلی را نادیده می‌گیرند. |
| `summary` {{deprecated_inline}} | `<table>` | — |
| [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | ترتیب تب پیش‌فرض مرورگر را نادیده می‌گیرد و به جای آن از ترتیب مشخص شده پیروی می‌کند. |
| [`target`](/en-US/docs/Web/HTML/Reference/Attributes/target) | `<a>`، `<area>`، `<base>`، `<form>` | مشخص می‌کند که سند لینک‌شده کجا باز شود (در مورد عنصر `<a>`) یا پاسخ دریافت‌شده کجا نمایش داده شود (در مورد عنصر `<form>`). |
| [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | متنی که هنگام قرار گرفتن ماوس روی عنصر در یک tooltip نمایش داده می‌شود. |
| [`translate`](/en-US/docs/Web/HTML/Reference/Global_attributes/translate) | [ویژگی عمومی](/en-US/docs/Web/HTML/Reference/Global_attributes) | مشخص می‌کند که آیا مقادیر ویژگی‌های عنصر و مقادیر گره‌های `Text` فرزند آن هنگام بومی‌سازی صفحه ترجمه شوند یا بدون تغییر باقی بمانند. |
| [`type`](/en-US/docs/Web/HTML/Reference/Attributes/type) | `<button>`، `<input>`، `<embed>`، `<object>`، `<ol>`، `<script>`، `<source>`، `<style>`، `<menu>`، `<link>` | نوع عنصر را تعریف می‌کند. |
| [`usemap`](/en-US/docs/Web/HTML/Reference/Attributes/usemap) | `<img>`، `<input>`، `<object>` | — |
| [`value`](/en-US/docs/Web/HTML/Reference/Attributes/value) | `<button>`، `<data>`، `<input>`، `<li>`، `<meter>`، `<option>`، `<progress>`، `<param>` | یک مقدار پیش‌فرض را تعریف می‌کند که در بارگذاری صفحه در عنصر نمایش داده می‌شود. |
| [`width`](/en-US/docs/Web/HTML/Reference/Attributes/width) | `<canvas>`، `<embed>`، `<iframe>`، `<img>`، `<input>`، `<object>`، `<video>` | برای عناصر ذکر شده، عرض عنصر را تعیین می‌کند. **توجه:** برای سایر موارد مانند `<div>`، این یک ویژگی قدیمی است و باید از ویژگی CSS `width` استفاده شود. |
| [`wrap`](/en-US/docs/Web/HTML/Reference/Elements/textarea#wrap) | `<textarea>` | نشان می‌دهد که آیا متن باید پیچیده شود. |

## ویژگی‌های محتوا (Content) در مقابل ویژگی‌های IDL

در HTML، بیشتر ویژگی‌ها (attributes) دو چهره دارند: **ویژگی محتوا (content attribute)** و **ویژگی IDL (ویژگی تعریف رابط — IDL attribute)**.

ویژگی محتوا همان ویژگی‌ای است که در کد HTML (محتوا) تنظیم می‌کنید و می‌توانید آن را با `element.setAttribute()` یا `element.getAttribute()` بخوانید یا بنویسید. ویژگی محتوا همیشه یک رشته (string) است، حتی اگر مقدار مورد انتظار یک عدد صحیح باشد. مثلاً برای تنظیم `maxlength` یک عنصر `<input>` روی ۴۲ با استفاده از ویژگی محتوا، باید روی آن عنصر `setAttribute("maxlength", "42")` را فراخوانی کنید.

ویژگی IDL را به عنوان یک property جاوااسکریپت نیز می‌شناسند. این ویژگی‌ها همان‌هایی هستند که با property‌های جاوااسکریپتی مانند `element.foo` می‌توانید بخوانید یا بنویسید. ویژگی IDL همیشه از ویژگی محتوای زیرین استفاده می‌کند (ولی ممکن است آن را تغییر شکل دهد) تا هنگام خواندن یک مقدار برگرداند و هنگام نوشتن، چیزی را در ویژگی محتوا ذخیره کند. به عبارت دیگر، ویژگی‌های IDL در اصل بازتابی از ویژگی‌های محتوا هستند.

بیشتر اوقات، ویژگی‌های IDL مقادیر را دقیقاً همان‌طور که در عمل استفاده می‌شوند برمی‌گردانند. مثلاً `type` پیش‌فرض عناصر `<input>` برابر "text" است. بنابراین اگر `input.type = "foobar"` را تنظیم کنید، عنصر `<input>` از نظر ظاهر و رفتار از نوع text خواهد بود، اما مقدار ویژگی محتوای "type" برابر "foobar" می‌ماند. در حالی که ویژگی IDL نوع `type` رشته "text" را برمی‌گرداند.

ویژگی‌های IDL همیشه رشته نیستند؛ مثلاً `input.maxlength` یک عدد (long با علامت) است. هنگام استفاده از ویژگی‌های IDL، مقادیر را با نوع مورد نظر می‌خوانید یا می‌نویسید، بنابراین `input.maxlength` همیشه یک عدد برمی‌گرداند و وقتی `input.maxlength` را تنظیم می‌کنید، به عدد نیاز دارد. اگر نوع دیگری ارسال کنید، طبق قوانین استاندارد تبدیل نوع جاوااسکریپت خودکاراً به عدد تبدیل می‌شود.

ویژگی‌های IDL می‌توانند [انواع دیگر](https://html.spec.whatwg.org/multipage/urls-and-fetching.html) مانند unsigned long، URLها، booleanها و غیره را بازتاب دهند. متأسفانه قوانین مشخصی وجود ندارد و رفتار ویژگی‌های IDL در ارتباط با ویژگی‌های محتوای متناظرشان به خود ویژگی بستگی دارد. بیشتر اوقات از [قوانین تعیین‌شده در مشخصات](https://html.spec.whatwg.org/multipage/urls-and-fetching.html) پیروی می‌کند، اما گاهی هم نمی‌کند. مشخصات HTML سعی می‌کند تا جای ممکن برای توسعه‌دهنده‌ها دوستانه باشد، اما به دلایل مختلف (اغلب تاریخی) برخی ویژگی‌ها رفتار عجیبی دارند (مثلاً `select.size`) و برای فهم دقیق رفتارشان باید مشخصات را مطالعه کنید.

## ویژگی‌های بولی (Boolean Attributes)

برخی از ویژگی‌های محتوا (مانند `required`، `readonly`، `disabled`) «[ویژگی‌های بولی (boolean attributes)](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#boolean-attributes)» نامیده می‌شوند. اگر یک ویژگی بولی وجود داشته باشد، مقدار آن **true** است و اگر نباشد، مقدار آن **false** است.

HTML برای مقادیر مجاز ویژگی‌های بولی محدودیت‌هایی تعریف کرده است: اگر ویژگی وجود داشته باشد، مقدار آن باید یا رشتهٔ خالی باشد (به‌عبارتی ویژگی می‌تواند مقدار تعیین‌نشده داشته باشد)، یا مقداری که با صرف‌نظر از بزرگی/کوچکی حروف (ASCII case-insensitive) با نام متعارف ویژگی همخوانی داشته باشد و فاصلهٔ ابتدا و انتها نداشته باشد. مثال‌های زیر روش‌های معتبر برای نشان‌دادن یک ویژگی بولی هستند:

```html-nolint
<div itemscope>This is valid HTML but invalid XML.</div>
<div itemscope=itemscope>This is also valid HTML but invalid XML.</div>
<div itemscope="">This is valid HTML and also valid XML.</div>
<div itemscope="itemscope">
  This is also valid HTML and XML, but perhaps a bit verbose.
</div>
```

برای روشن‌تر شدن موضوع: مقادیر `"true"` و `"false"` برای ویژگی‌های بولی مجاز نیستند. برای نمایش مقدار false، باید ویژگی را به‌کلی حذف کرد. این محدودیت برخی سوءتفاهم‌های رایج را برطرف می‌کند: مثلاً با `checked="false"`، ویژگی `checked` عنصر به‌دلیل وجود داشتن، **true** تفسیر می‌شود.

## ویژگی‌های event handler

> [!WARNING]
> استفاده از content attribute های event handler توصیه نمی‌شود. ترکیب HTML و JavaScript اغلب کدی تولید می‌کند که نگهداری آن دشوار است؛ همچنین اجرای ویژگی‌های event handler ممکن است توسط سیاست‌های امنیت محتوا مسدود شود.

> [!WARNING]
> هرچند با فراخوانی `Function.prototype.toString()` روی handler قابل مشاهده نیست، ویژگی‌های event handler به‌صورت ضمنی کد را در دو عبارت `with` می‌پیچند و ممکن است نتایج غیرمنتظره‌ای ایجاد کنند. برای مثال:
>
> ```html
> <div onclick="console.log(new URL(location))">Bad Example</div>
> ```
>
> در اصل به این شکل تبدیل می‌شود:
>
> ```js example-bad
> function onclick(event) {
>   with (this.ownerDocument) {
>     with (this) {
>       console.log(new URL(location)); // 'URL' now resolves to document.URL instead of window.URL
>       // TypeError: URL is not a constructor
>     }
>   }
> }
> ```

علاوه بر ویژگی‌های ذکرشده در جدول بالا، [event handler](/en-US/docs/Web/API/Document_Object_Model/Events#using_onevent_properties) های سراسری — مانند [`onclick`](/en-US/docs/Web/API/Element/click_event) — را می‌توان روی همهٔ عناصر به‌صورت [content attribute](#content_versus_idl_attributes) نیز مشخص کرد.

همهٔ ویژگی‌های event handler یک رشته دریافت می‌کنند. از این رشته برای ساخت یک [تابع جاوااسکریپت](/en-US/docs/Web/JavaScript/Reference/Functions) به شکل `function name(/*args*/) {body}` استفاده می‌شود که در آن `name` نام ویژگی و `body` مقدار ویژگی است. handler همان پارامترهای همتای جاوااسکریپتی خود را دریافت می‌کند — بیشتر handlerها فقط یک پارامتر `event` می‌گیرند، در حالی‌که `onerror` پنج پارامتر دریافت می‌کند: `event`, `source`, `lineno`, `colno`, `error`. بنابراین به‌طور کلی می‌توانید درون ویژگی از متغیر `event` استفاده کنید.

```html
<div onclick="console.log(event)">Click me!</div>
<!-- The synthesized handler has a name; you can reference itself -->
<div onclick="console.log(onclick)">Click me!</div>
```

## همچنین ببینید

- [HTML elements](/en-US/docs/Web/HTML/Reference/Elements)