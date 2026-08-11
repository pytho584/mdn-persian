---
title: "CSS: Cascading Style Sheets"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS"
translated_by: "n8n + AI"
---

**Cascading Style Sheets** (**CSS**) یک زبان [stylesheet](/en-US/docs/Web/API/StyleSheet) است که برای توصیف نمایش یک سند نوشته‌شده با [HTML](/en-US/docs/Web/HTML) یا [XML](/en-US/docs/Web/XML/Guides/XML_introduction) (شامل گویش‌های XML مانند [SVG](/en-US/docs/Web/SVG)، [MathML](/en-US/docs/Web/MathML) یا XHTML) استفاده می‌شود. CSS نحوهٔ رندر شدن elements را روی صفحه، کاغذ، گفتار یا سایر رسانه‌ها توصیف می‌کند.

CSS یکی از زبان‌های اصلی **وب باز** است و طبق [مشخصات W3C](https://www.w3.org/Style/CSS/#specs) در مرورگرهای وب استاندارد شده است. پیش‌تر، توسعهٔ بخش‌های مختلف مشخصات CSS به‌صورت هم‌زمان انجام می‌شد که امکان نسخه‌گذاری آخرین توصیه‌ها را فراهم می‌کرد. شاید نام CSS1، CSS2.1 یا حتی CSS3 را شنیده باشید. هیچ‌وقت CSS3 یا CSS4 وجود نخواهد داشت؛ بلکه همه‌چیز اکنون فقط «CSS» است و ماژول‌های جداگانهٔ CSS شمارهٔ نسخهٔ خود را دارند.

پس از CSS 2.1، دامنهٔ مشخصات به‌طور قابل توجهی افزایش یافت و پیشرفت ماژول‌های مختلف CSS آن‌قدر از هم فاصله گرفت که [توسعه و انتشار توصیه‌ها به‌صورت جداگانه برای هر ماژول](https://www.w3.org/Style/CSS/current-work) مؤثرتر شد. اکنون W3C به‌جای نسخه‌گذاری کل مشخصات CSS، به‌صورت دوره‌ای از [آخرین وضعیت پایدار مشخصات CSS](https://www.w3.org/TR/css/) و پیشرفت ماژول‌های جداگانهٔ آن یک snapshot (عکس‌برداری) می‌گیرد. ماژول‌های CSS اکنون شمارهٔ نسخه یا level دارند؛ مانند [CSS Color Module Level 5](https://drafts.csswg.org/css-color-5/).

## آموزش‌های مبتدی

ماژول‌های اصلی [آموزش توسعهٔ وب](/en-US/docs/Learn_web_development/Core) شامل آموزش‌های مدرن و به‌روز دربارهٔ مبانی CSS هستند.

- [Your first website: Styling the content](/en-US/docs/Learn_web_development/Getting_started/Your_first_website/Styling_the_content)
  - : این مقاله مروری کوتاه بر اینکه CSS چیست و چگونه از آن استفاده می‌شود ارائه می‌دهد و برای افرادی است که کاملاً با توسعهٔ وب تازه‌کار هستند.
- [CSS styling basics](/en-US/docs/Learn_web_development/Core/Styling_basics)
  - : این ماژول تمام مبانی CSS را که برای شروع مؤثر یادگیری این فناوری نیاز دارید، شامل syntax، امکانات و تکنیک‌ها، در اختیار شما قرار می‌دهد.
- [CSS text styling](/en-US/docs/Learn_web_development/Core/Text_styling)
  - : در اینجا به مبانی قالب‌بندی متن با CSS می‌پردازیم، از جمله تنظیم فونت، ضخامت، ایتالیک، فاصلهٔ خطوط و حروف و سایهٔ متن. در پایان ماژول، به استفاده از فونت‌های سفارشی در صفحه و استایل‌دهی به فهرست‌ها و لینک‌ها می‌پردازیم.
- [CSS layout](/en-US/docs/Learn_web_development/Core/CSS_layout)
  - : این ماژول به floats، موقعیت‌دهی، سایر ابزارهای مدرن چیدمان و ساخت طراحی‌های واکنش‌گرا (responsive) که با دستگاه‌ها، اندازه‌های صفحه و وضوح‌های مختلف سازگار می‌شوند، می‌پردازد.

## راهنماها

راهنماهای CSS بر اساس ماژول‌ها سازماندهی شده‌اند تا به شما کمک کنند یاد بگیرید با CSS چه کارهایی می‌توانید انجام دهید. فهرست کامل را در [CSS guides](/en-US/docs/Web/CSS/Guides) ببینید؛ این فهرست شامل موضوعاتی مانند:

- [CSS syntax](/en-US/docs/Web/CSS/Guides/Syntax/Introduction) شامل declarations و rulesets
- [Specificity](/en-US/docs/Web/CSS/Guides/Cascade/Specificity)، [inheritance](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance) و [cascade](/en-US/docs/Web/CSS/Guides/Cascade/Introduction)
- [Nesting](/en-US/docs/Web/CSS/Guides/Nesting)، [scoping](/en-US/docs/Web/CSS/Guides/Scoping) و [shadow parts](/en-US/docs/Web/CSS/Guides/Shadow_parts)
- [Media](/en-US/docs/Web/CSS/Guides/Media_queries) و [container](/en-US/docs/Web/CSS/Guides/Containment) queries
- انواع داده‌ی [عددی](/en-US/docs/Web/CSS/Guides/Values_and_units/Numeric_data_types) و [متنی](/en-US/docs/Web/CSS/Guides/Values_and_units/Textual_data_types)
- [Box model](/en-US/docs/Web/CSS/Guides/Box_model/Introduction) و [margin collapse](/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing)
- [Containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block)
- [Stacking](/en-US/docs/Web/CSS/Guides/Positioned_layout/Stacking_context) و [block-formatting](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) contexts
- [Property value processing](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing)
- [Shorthand properties](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties)
- چیدمان‌های [Flexible box](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)، [multi-column](/en-US/docs/Web/CSS/Guides/Multicol_layout) و [grid](/en-US/docs/Web/CSS/Guides/Grid_layout)
- [Animations](/en-US/docs/Web/CSS/Guides/Animations/Using)، [transitions](/en-US/docs/Web/CSS/Guides/Transitions/Using) و [transforms](/en-US/docs/Web/CSS/Guides/Transforms/Using)

## راهنماها

- [CSS layout cookbook](/en-US/docs/Web/CSS/How_to/Layout_cookbook)
  - : دستور العمل‌هایی برای الگوهای چیدمان رایج که ممکن است در سایت‌هایتان نیاز داشته باشید. این دستور العمل‌ها کدی را ارائه می‌دهند که می‌توانید به عنوان نقطه شروع در پروژه‌های خود استفاده کنید. همچنین نحوه‌ی استفاده‌های مختلف از مشخصات چیدمان و انتخاب‌های ممکن به عنوان یک توسعه‌دهنده را برجسته می‌کنند.

## ابزارها

- [Border-image generator](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Border-image_generator)
  - : مقادیر CSS border-image را تولید کنید.
- [Border-radius generator](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Border-radius_generator)
  - : افکت‌های CSS border-radius را ایجاد کنید.
- [Box-shadow generator](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders/Box-shadow_generator)
  - : افکت‌های box-shadow را به اشیاء CSS خود اضافه کنید.
- [Color format converter](/en-US/docs/Web/CSS/Guides/Colors/Color_format_converter)
  - : یک رنگ را وارد یا انتخاب کنید و مقدار متناظر آن را در هر [فرمت رنگی](/en-US/docs/Web/CSS/Reference/Values/color_value) CSS کپی کنید.
- [Color mixer](/en-US/docs/Web/CSS/Guides/Colors/Color_mixer)
  - : دو رنگ را در هر فضای رنگی با استفاده از تابع color-mix() ترکیب کنید و رنگ حاصل را در هر فرمت رنگی CSS کپی کنید.
- [Shape generator](/en-US/docs/Web/CSS/Guides/Shapes/Shape_generator)
  - : مختصات و نحو ویژگی‌های basic-shape را تعریف کنید.

همچنین می‌توانید از منابع زیر استفاده کنید:

- [W3C CSS Validation Service](https://jigsaw.w3.org/css-validator/): برای بررسی معتبر بودن CSS خود. این یک ابزار رفع اشکال ارزشمند است.
- [Firefox Developer Tools](https://firefox-source-docs.mozilla.org/devtools-user/index.html): برای مشاهده و ویرایش CSS زنده‌ی یک صفحه از طریق ابزارهای [Inspector](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/index.html) و [Style Editor](https://firefox-source-docs.mozilla.org/devtools-user/style_editor/index.html).
- [Web Developer extension](https://addons.mozilla.org/en-US/firefox/addon/web-developer/): برای ردیابی و ویرایش CSS زنده در وب‌سایت‌ها در فایرفاکس.

## مرجع

مستندات کامل [CSS reference](/en-US/docs/Web/CSS/Reference) را مرور کنید.

- [CSS properties](/en-US/docs/Web/CSS/Reference/Properties)
  - : مرجعی برای تمام CSS properties.

- [CSS selectors](/en-US/docs/Web/CSS/Reference/Selectors)
  - : مرجعی برای CSS selectors، [combinators](/en-US/docs/Web/CSS/Reference/Selectors/Combinators)، [pseudo-classes](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-classes)، و [pseudo-elements](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements).

- [CSS at-rules](/en-US/docs/Web/CSS/Reference/At-rules)
  - : مرجعی برای CSS at-rules، از جمله media queries.

- [CSS values](/en-US/docs/Web/CSS/Reference/Values)
  - : مرجعی برای CSS keywords، [data types](/en-US/docs/Web/CSS/Reference/Values/Data_types)، و [functions](/en-US/docs/Web/CSS/Reference/Values/Functions).

## همچنین ببینید

- زبان‌های وبی که CSS اغلب روی آن‌ها استفاده می‌شود: [HTML](/en-US/docs/Web/HTML)، [SVG](/en-US/docs/Web/SVG)، [MathML](/en-US/docs/Web/MathML)، XHTML، و [XML](/en-US/docs/Web/XML/Guides/XML_introduction).
- [پرسش‌های Stack Overflow درباره CSS](https://stackoverflow.com/questions/tagged/css)