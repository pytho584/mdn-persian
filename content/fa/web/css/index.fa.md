---
title: "CSS: برگه‌های سبک آبشاری"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS"
translated_by: "n8n + AI"
---

**برگه‌های سبک آبشاری** (**CSS**) زبانی برای توصیف نمایش یک سند نوشته‌شده با [HTML](/en-US/docs/Web/HTML) یا [XML](/en-US/docs/Web/XML/Guides/XML_introduction) (و گویش‌های XML مانند [SVG](/en-US/docs/Web/SVG)، [MathML](/en-US/docs/Web/MathML) یا {{Glossary("XHTML")}}) است. CSS مشخص می‌کند که عناصر چگونه روی صفحه، کاغذ، در گفتار یا سایر رسانه‌ها رندر شوند.

CSS یکی از زبان‌های اصلی **وب باز** است و طبق [مشخصات W3C](https://www.w3.org/Style/CSS/#specs) در مرورگرهای وب استاندارد شده است. پیشتر بخش‌های مختلف مشخصات CSS به‌صورت هم‌زمان توسعه پیدا می‌کردند و همین موضوع نسخه‌بندی آخرین توصیه‌ها را ممکن می‌کرد. شاید نام CSS1، CSS2.1 یا حتی CSS3 را شنیده باشید. اما هرگز CSS3 یا CSS4 وجود نخواهد داشت؛ در واقع همه‌چیز حالا فقط «CSS» است و هر ماژول CSS شماره نسخهٔ خودش را دارد.

پس از CSS 2.1، دامنهٔ مشخصات به‌طور قابل توجهی گسترده شد و پیشرفت ماژول‌های مختلف CSS آن‌قدر از هم فاصله گرفت که [توسعه و انتشار توصیه‌ها به صورت جداگانه برای هر ماژول](https://www.w3.org/Style/CSS/current-work) مؤثرتر شد. به‌جای نسخه‌بندی کل مشخصات CSS، W3C حالا به‌صورت دوره‌ای [آخرین وضعیت پایدار مشخصات CSS](https://www.w3.org/TR/css/) را به‌عنوان snapshot ثبت می‌کند و ماژول‌های جداگانه پیشرفت می‌کنند. ماژول‌های CSS حالا شماره نسخه یا سطح دارند؛ مثلاً [CSS Color Module Level 5](https://drafts.csswg.org/css-color-5/).

## آموزش‌های مقدماتی

ماژول‌های اصلی [یادگیری توسعه وب](/en-US/docs/Learn_web_development/Core) شامل آموزش‌های مدرن و به‌روز در مورد مبانی CSS هستند.

- [اولین وب‌سایت شما: استایل‌دهی به محتوا](/en-US/docs/Learn_web_development/Getting_started/Your_first_website/Styling_the_content)
  - : این مقاله یک مرور کوتاه از چیستی CSS و نحوه استفاده از آن ارائه می‌دهد و برای افرادی نوشته شده که تازه توسعه وب را شروع کرده‌اند.
- [مبانی استایل‌دهی با CSS](/en-US/docs/Learn_web_development/Core/Styling_basics)
  - : این ماژول تمام مفاهیم پایه‌ای CSS را که برای یادگیری مؤثر این فناوری لازم دارید پوشش می‌دهد؛ از جمله syntax، ویژگی‌ها و تکنیک‌ها.
- [استایل‌دهی متن](/en-US/docs/Learn_web_development/Core/Text_styling)
  - : در این ماژول به مبانی استایل‌دهی متن با CSS می‌پردازیم؛ از جمله تنظیم فونت، ضخامت، ایتالیک، فاصله خطوط و حروف و سایه متن. در پایان هم به اعمال فونت‌های سفارشی، استایل‌دهی لیست‌ها و لینک‌ها می‌پردازیم.
- [چیدمان با CSS](/en-US/docs/Learn_web_development/Core/CSS_layout)
  - : این ماژول به floats، positioning و سایر ابزارهای مدرن چیدمان و همچنین ساخت طراحی‌های واکنش‌گرا که با دستگاه‌ها، اندازه‌های صفحه و رزولوشن‌های مختلف سازگار می‌شوند، می‌پردازد.

## راهنماها

راهنماهای CSS بر اساس ماژول‌ها سازماندهی شده‌اند و به شما کمک می‌کنند یاد بگیرید با CSS چه کارهایی می‌توانید انجام دهید. فهرست کامل را در [راهنماهای CSS](/en-US/docs/Web/CSS/Guides) ببینید؛ از جمله موضوعاتی مانند:

- [سینتکس CSS](/en-US/docs/Web/CSS/Guides/Syntax/Introduction) شامل declarations و rulesets
- [خصیصه‌مندی (Specificity)](/en-US/docs/Web/CSS/Guides/Cascade/Specificity)، [وراثت (inheritance)](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance) و [آبشاری (cascade)](/en-US/docs/Web/CSS/Guides/Cascade/Introduction)
- [تودرتو (Nesting)](/en-US/docs/Web/CSS/Guides/Nesting)، [دامنه (scoping)](/en-US/docs/Web/CSS/Guides/Scoping) و [بخش‌های سایه (shadow parts)](/en-US/docs/Web/CSS/Guides/Shadow_parts)
- [پرس‌وجوهای رسانه (Media)](/en-US/docs/Web/CSS/Guides/Media_queries) و [ظرف (container)](/en-US/docs/Web/CSS/Guides/Containment) queries
- [انواع داده عددی](/en-US/docs/Web/CSS/Guides/Values_and_units/Numeric_data_types) و [متنی](/en-US/docs/Web/CSS/Guides/Values_and_units/Textual_data_types)
- [مدل جعبه (Box model)](/en-US/docs/Web/CSS/Guides/Box_model/Introduction) و [فروریختن حاشیه (margin collapse)](/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing)
- [بلوک محتوی (Containing block)](/en-US/docs/Web/CSS/Guides/Display/Containing_block)
- [زمینه‌های انباشت (Stacking)](/en-US/docs/Web/CSS/Guides/Positioned_layout/Stacking_context) و [قالب‌بندی بلوک (block-formatting)](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) contexts
- [پردازش مقدار property](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing)
- [ویژگی‌های کوتاه‌نویس (Shorthand properties)](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties)
- [چیدمان جعبه انعطاف‌پذیر (Flexible box)](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)، [چندستونه (multi-column)](/en-US/docs/Web/CSS/Guides/Multicol_layout) و [شبکه‌ای (grid)](/en-US/docs/Web/CSS/Guides/Grid_layout) layouts
- [انیمیشن‌ها (Animations)](/en-US/docs/Web/CSS/Guides/Animations/Using)، [انتقال‌ها (transitions)](/en-US/docs/Web/CSS/Guides/Transitions/Using) و [تبدیل‌ها (transforms)](/en-US/docs/Web/CSS/Guides/Transforms/Using)

## راهنما (How-to)

- [کتابخانه چیدمان CSS](/en-US/docs/Web/CSS/How_to/Layout_cookbook)
  - : دستورالعمل‌هایی برای الگوهای چیدمان رایج که ممکن است در سایت‌های خود نیاز به پیاده‌سازی داشته باشید. این دستورالعمل‌ها کدی را ارائه می‌دهند که می‌توانید به عنوان نقطه شروع در پروژه‌های خود استفاده کنید. همچنین روش‌های مختلف استفاده از مشخصات چیدمان و انتخاب‌هایی که به عنوان توسعه‌دهنده دارید را برجسته می‌کنند.

## ابزارها

- [تولیدکننده border-image](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Border-image_generator)
  - : مقادیر CSS {{cssxref("border-image")}} را تولید کنید.
- [تولیدکننده border-radius](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Border-radius_generator)
  - : افکت‌های CSS {{cssxref("border-radius")}} را تولید کنید.
- [تولیدکننده box-shadow](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Box-shadow_generator)
  - : افکت‌های {{cssxref("box-shadow")}} را به اشیاء CSS خود اضافه کنید.
- [مبدل فرمت رنگ](/en-US/docs/Web/CSS/Guides/Colors/Color_format_converter)
  - : یک رنگ را وارد یا انتخاب کنید و مقدار متناظر آن را در هر [فرمت رنگ](/en-US/docs/Web/CSS/Reference/Values/color_value) CSS کپی کنید.
- [ترکیب‌کننده رنگ](/en-US/docs/Web/CSS/Guides/Colors/Color_mixer)
  - : دو رنگ را در هر فضای رنگی با استفاده از تابع {{cssxref("color_value/color-mix", "color-mix()")}} ترکیب کنید و رنگ حاصل را در هر فرمت رنگ CSS کپی کنید.
- [تولیدکننده shape](/en-US/docs/Web/CSS/Guides/Shapes/Shape_generator)
  - : مختصات و سینتکس ویژگی‌های {{cssxref("basic-shape")}} را تعریف کنید.

همچنین می‌توانید از منابع زیر استفاده کنید:

- [سرویس اعتبارسنجی CSS W3C](https://jigsaw.w3.org/css-validator/): برای بررسی معتبر بودن CSS شما. این یک ابزار بسیار مفید برای رفع اشکال است.
- [ابزارهای توسعه‌دهنده Firefox](https://firefox-source-docs.mozilla.org/devtools-user/index.html): برای مشاهده و ویرایش زنده CSS یک صفحه از طریق ابزارهای [Inspector](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/index.html) و [Style Editor](https://firefox-source-docs.mozilla.org/devtools-user/style_editor/index.html).
- [افزونه Web Developer](https://addons.mozilla.org/en-US/firefox/addon/web-developer/): برای ردیابی و ویرایش زنده CSS در وب‌سایت‌ها در Firefox.

## مرجع

مستندات کامل [مرجع CSS](/en-US/docs/Web/CSS/Reference) را مرور کنید.

- [ویژگی‌های (property) CSS](/en-US/docs/Web/CSS/Reference/Properties)
  - : مرجعی برای همهٔ CSS propertyها.
- [انتخاب‌گرهای (selector) CSS](/en-US/docs/Web/CSS/Reference/Selectors)
  - : مرجعی برای CSS selectorها، [ترکیب‌کننده‌ها (combinatorها)](/en-US/docs/Web/CSS/Reference/Selectors/Combinators)، [شبه‌کلاس‌ها (pseudo-classes)](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-classes) و [شبه‌عناصر (pseudo-elements)](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements).
- [قوانین at-rule CSS](/en-US/docs/Web/CSS/Reference/At-rules)
  - : مرجعی برای CSS at-ruleها، از جمله media queryها.
- [مقادیر (value) CSS](/en-US/docs/Web/CSS/Reference/Values)
  - : مرجعی برای CSS keywordها، [انواع داده‌ها](/en-US/docs/Web/CSS/Reference/Values/Data_types) و [تابع‌ها](/en-US/docs/Web/CSS/Reference/Values/Functions).

## همچنین ببینید

- زبان‌های وبی که CSS اغلب روی آن‌ها اعمال می‌شود: [HTML](/en-US/docs/Web/HTML)، [SVG](/en-US/docs/Web/SVG)، [MathML](/en-US/docs/Web/MathML)، XHTML و [XML](/en-US/docs/Web/XML/Guides/XML_introduction).
- [سؤال‌های Stack Overflow دربارهٔ CSS](https://stackoverflow.com/questions/tagged/css)