---
title: 'HTML: HyperText Markup Language'
source: https://developer.mozilla.org/en-US/docs/Web/HTML
translated_by: n8n + AI
cover: >-
  .gitbook/assets/FromKlickpin.com-54184001763550470-pin-id-54184001763550470-ezgif.com-video-to-gif-converter.gif
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
    mask: none
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# HTML  HyperText Markup Language

**HTML** (HyperText Markup Language) پایه‌ای‌ترین بلوک ساختمانی وب است. این زبان معنی و ساختار محتوای وب را مشخص می‌کند. معمولاً از فناوری‌های دیگری مثل [CSS](../../../../en-US/docs/Web/CSS/) برای ظاهر/نمایش صفحه و [JavaScript](../../../../en-US/docs/Web/JavaScript/) برای عملکرد/رفتار آن استفاده می‌شود.

«Hypertext» اشاره به لینک‌هایی دارد که صفحات وب را به هم متصل می‌کنند – چه در یک وب‌سایت و چه بین وب‌سایت‌های مختلف. لینک‌ها یک جنبهٔ اساسی وب هستند. با آپلود محتوا در اینترنت و پیوند دادن آن به صفحه‌هایی که دیگران ساخته‌اند، شما به یک شرکت‌کنندهٔ فعال در وب جهانی تبدیل می‌شوید.

HTML از «markup» (نشانه‌گذاری) برای حاشیه‌نویسی متن، تصاویر و سایر محتواها جهت نمایش در مرورگر استفاده می‌کند. این نشانه‌گذاری شامل «عناصر» (elements) خاصی مانند `<head>`، `<title>`، `<body>`، `<header>`، `<footer>`، `<article>`، `<section>`، `<p>`، `<div>`، `<span>`، `<img>`، `<aside>`، `<audio>`، `<canvas>`، `<datalist>`، `<details>`، `<embed>`، `<nav>`، `<search>`، `<output>`، `<progress>`، `<video>`، `<ul>`، `<ol>`، `<li>` و بسیاری دیگر است.

یک عنصر HTML با «تگ» (tag) از بقیهٔ متن یک سند جدا می‌شود. تگ از نام عنصر که بین `<` و `>` قرار می‌گیرد تشکیل شده است. نام عنصر داخل تگ به بزرگی یا کوچکی حروف حساس نیست؛ یعنی می‌توان آن را با حروف بزرگ، کوچک یا ترکیبی نوشت. مثلاً تگ `<title>` را می‌توان به صورت `<Title>`، `<TITLE>` یا هر شکل دیگری نوشت. با این حال، قرارداد و روش توصیه‌شده این است که تگ‌ها را با حروف کوچک بنویسید.

مقاله‌های زیر می‌توانند به شما در یادگیری بیشتر HTML کمک کنند.

### آموزش‌های مقدماتی

ماژول‌های اصلی [یادگیری توسعه وب](../../../../en-US/docs/Learn_web_development/Core/) شامل آموزش‌های مدرن و به‌روز دربارهٔ مبانی HTML هستند.

* [اولین وب‌سایت شما: ایجاد محتوا](../../../../en-US/docs/Learn_web_development/Getting_started/Your_first_website/Creating_the_content/)
  * : این مقاله یک مرور مختصر از چیستی HTML و نحوه استفاده از آن ارائه می‌دهد و برای افرادی که کاملاً تازه‌کار هستند مناسب است.
* [ساختاربندی محتوا با HTML](../../../../en-US/docs/Learn_web_development/Core/Structuring_content/)
  * : این ماژول مبانی زبان HTML را پوشش می‌دهد و سپس به موضوعات کلیدی مانند ساختار سند، لینک‌ها، لیست‌ها، تصاویر، فرم‌ها و موارد دیگر می‌پردازد.
* [فرم‌های HTML](../../../../en-US/docs/Learn_web_development/Extensions/Forms/)
  * : فرم‌ها بخش بسیار مهمی از وب هستند – آنها بسیاری از قابلیت‌های مورد نیاز برای تعامل با وب‌سایت‌ها را فراهم می‌کنند؛ مانند ثبت‌نام و ورود، ارسال بازخورد، خرید محصولات و موارد دیگر. این ماژول شما را با ساخت بخش‌های سمت کاربر (front-end) فرم‌ها آشنا می‌کند.

### راهنماها

[راهنماهای HTML](../../../../en-US/docs/Web/HTML/Guides/) به شما کمک می‌کنند تا با HTML در وب کار کنید. این راهنماها موضوعاتی مانند فرم‌ها، CORS، بارگذاری پیش‌فرض محتوا و تصاویر واکنش‌گرا را پوشش می‌دهند.

* [HTML cheatsheet for syntax and common tasks](../../../../en-US/docs/Web/HTML/Guides/Cheatsheet/)
  * : مرجعی سریع برای سینتکس و کارهای رایج HTML.
* [Using HTML comments `<!-- … -->`](../../../../en-US/docs/Web/HTML/Guides/Comments/)
  * : کامنت‌های HTML برای افزودن توضیحات به نشانه‌گذاری یا جلوگیری از تفسیر بخش‌های خاصی از سند توسط مرورگر استفاده می‌شوند.
* [Using HTML form validation and the Constraint Validation API](../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/)
  * : HTML5 اعتبارسنجی محدودیتی (constraint validation) را برای ساده‌سازی اعتبارسنجی فرم در سمت کلاینت معرفی کرد. با تنظیم attribute روی عناصر فرم می‌توان محدودیت‌های پایه را بدون JavaScript بررسی کرد.
* [Content categories](../../../../en-US/docs/Web/HTML/Guides/Content_categories/)
  * : HTML از چندین نوع محتوا تشکیل شده که هرکدام در برخی زمینه‌ها مجاز و در برخی دیگر ممنوع هستند. به‌طور مشابه، هر زمینه مجموعه‌ای از دسته‌های محتوایی دیگر را می‌پذیرد و عناصر خاصی را می‌توان یا نمی‌توان در آن استفاده کرد. این راهنما به این دسته‌بندی‌ها می‌پردازد.
* [Using date and time formats in HTML](../../../../en-US/docs/Web/HTML/Guides/Date_and_time_formats/)
  * : برخی عناصر HTML از مقادیر تاریخ و/یا زمان استفاده می‌کنند. این راهنما فرمت‌های رشته‌هایی را که این مقادیر را مشخص می‌کنند، توضیح می‌دهد.
* [Using microdata in HTML](../../../../en-US/docs/Web/HTML/Guides/Microdata/)
  * : Microdata برای تودرتوسازی فراداده (metadata) درون محتوای موجود در صفحات وب استفاده می‌شود. موتورهای جستجو و خزنده‌های وب می‌توانند microdata را استخراج و پردازش کنند تا تجربه مرور غنی‌تری ارائه دهند.
* [Using microformats in HTML](../../../../en-US/docs/Web/HTML/Guides/Microformats/)
  * : Microformats استانداردهایی هستند برای جاسازی معناشناسی و داده‌های ساختاریافته در HTML که توسط برنامه‌های وب اجتماعی، موتورهای جستجو، جمع‌آوری‌کننده‌ها و سایر ابزارها استفاده می‌شوند.
* [Understanding quirks and standards modes](../../../../en-US/docs/Web/HTML/Guides/Quirks_mode_and_standards_mode/)
  * : اطلاعات تاریخی درباره حالت quirks mode و standards mode.
* [Using responsive images in HTML](../../../../en-US/docs/Web/HTML/Guides/Responsive_images/)
  * : درباره تصاویر واکنش‌گرا (responsive) بیاموزید که در دستگاه‌هایی با اندازه صفحه، وضوح و ویژگی‌های بسیار متفاوت به خوبی کار می‌کنند و عملکرد را در دستگاه‌های مختلف بهبود می‌بخشند.
* [Media types and formats on the web](../../../../en-US/docs/Web/Media/Guides/Formats/)
  * : عناصر `<audio>` و `<video>` به شما امکان می‌دهند محتوای صوتی و تصویری را به صورت بومی درون محتوای خود پخش کنید بدون نیاز به نرم‌افزار خارجی.

### How to

* [تعریف اصطلاحات با HTML](../../../../en-US/docs/Web/HTML/How_to/Define_terms_with_HTML/)
  * : HTML روش‌های متعددی برای انتقال معنای توصیف (description semantics) ارائه می‌دهد؛ چه به‌صورت درون‌خطی (inline) و چه به‌صورت واژه‌نامه‌های ساختاریافته. این مقاله نشان می‌دهد که هنگام تعریف کلمه‌های کلیدی، چگونه آن‌ها را به‌درستی نشانه‌گذاری کنید.
* [استفاده از data attributeها](../../../../en-US/docs/Web/HTML/How_to/Use_data_attributes/)
  * : HTML5 با در نظر گرفتن قابلیت توسعه‌پذیری (extensibility) طراحی شده است؛ برای داده‌هایی که باید به یک element خاص مرتبط شوند اما لزومی ندارد معنای از پیش تعریف‌شده‌ای داشته باشند. attributeهای `data-*` به ما اجازه می‌دهند اطلاعات اضافی را روی elementهای استاندارد و معنایی HTML ذخیره کنیم.
* [استفاده از تصاویر cross-origin در canvas](../../../../en-US/docs/Web/HTML/How_to/CORS_enabled_image/)
  * : برخی از elementهای HTML که از [CORS](../../../../en-US/docs/Web/HTTP/Guides/CORS/) پشتیبانی می‌کنند، مانند `<img>` یا `<video>`، دارای attribute به نام `crossorigin` (یا property به نام `crossOrigin`) هستند که به شما امکان می‌دهد درخواست‌های CORS مربوط به داده‌های بارگیری‌شدهٔ آن element را پیکربندی کنید.
* [افزودن hitmap روی یک تصویر](../../../../en-US/docs/Web/HTML/How_to/Add_a_hit_map_on_top_of_an_image/)
  * : Image mapها اجازه می‌دهند لینک‌ها به بخش‌های مختلف یک تصویر مرتبط شوند. این مقاله نحوهٔ ایجاد و پیاده‌سازی آن‌ها را نشان می‌دهد.
* [نوشتن صفحات HTML با بارگذاری سریع](../../../../en-US/docs/Web/HTML/How_to/Author_fast-loading_HTML_pages/)
  * : این نکات بر پایهٔ دانش عمومی و آزمایش‌های عملی هستند. یک صفحهٔ وب بهینه‌سازیشده نه‌تنها سایت پاسخگوتری برای بازدیدکنندگان فراهم می‌کند، بلکه بار سرورهای وب و اتصال اینترنت شما را نیز کاهش می‌دهد.
* [افزودن JavaScript به صفحهٔ وب شما](../../../../en-US/docs/Web/HTML/How_to/Add_JavaScript_to_your_web_page/)
  * : این مقاله توضیح می‌دهد که چگونه کد JavaScript را به یک فایل HTML اضافه کنید.

### مرجع

HTML از **elementها** تشکیل شده است که هر کدام ممکن است با تعدادی **attribute** تغییر کنند. صفحات HTML نیز توسط **لینک‌ها** به یکدیگر متصل می‌شوند. برای مشاهدهٔ مستندات کامل [مرجع HTML](../../../../en-US/docs/Web/HTML/Reference/) مراجعه کنید.

* [HTML elementها](../../../../en-US/docs/Web/HTML/Reference/Elements/)
  * : مرجع همهٔ elementهای HTML.
* [HTML attributeها](../../../../en-US/docs/Web/HTML/Reference/Attributes/)
  * : مرجع همهٔ attributeهای HTML. attributeها مقادیر اضافی هستند که elementها را پیکربندی می‌کنند یا رفتار آن‌ها را به روش‌های گوناگون تنظیم می‌کنند.
* [Global attributeها](../../../../en-US/docs/Web/HTML/Reference/Global_attributes/)
  * : مرجع attributeهای سراسری که می‌توان روی همهٔ elementهای HTML مشخص کرد، _حتی آن‌هایی که در استاندارد تعریف نشده‌اند_. یعنی هر element غیراستانداردی همچنان باید این attributeها را بپذیرد، حتی اگر این عناصر باعث شوند سند با HTML5 سازگار نباشد.

#### Attributeها بر اساس element

* [Input typeها](../../../../en-US/docs/Web/HTML/Reference/Elements/input/)
  * : برای ساخت کنترل‌های تعاملی در فرم‌های مبتنی بر وب استفاده می‌شود.
* [Script typeها](../../../../en-US/docs/Web/HTML/Reference/Elements/script/type/)
  * : نوع اسکریپتی را که element نشان می‌دهد مشخص می‌کند.
* [meta name](../../../../en-US/docs/Web/HTML/Reference/Elements/meta/name/)
  * : فراداده (metadata) را به‌صورت جفت‌های نام-مقدار برای کل صفحه فراهم می‌کند.

#### مقدارهای attribute

* [rel keywords](../../../../en-US/docs/Web/HTML/Reference/Attributes/rel/)
  * : رابطهٔ بین یک منبع لینک‌شده و سند فعلی را تعریف می‌کند.

### موضوعات مرتبط

* [اعمال رنگ به elementهای HTML با استفاده از CSS](../../../../en-US/docs/Web/CSS/Guides/Colors/Applying_color/)
  * : این مقاله بیشتر روش‌هایی را که با استفاده از CSS به محتوای HTML رنگ اضافه می‌کنید پوشش می‌دهد؛ بخش‌های قابل رنگ‌آمیزی در اسناد HTML را فهرست می‌کند و مشخص می‌کند از کدام propertyهای CSS برای این کار استفاده کنید.
