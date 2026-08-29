ماژول حالت‌های نوشتاری CSS پشتیبانی از حالت‌های نوشتاری بین‌المللی مختلف و ترکیب‌های آن‌ها، از جمله ترتیب چپ‌به‌راست و راست‌به‌چپ و همچنین جهت‌های افقی و عمودی را فراهم می‌کند.

یک حالت نوشتاری در CSS توسط ویژگی‌های {{cssxref("writing-mode")}}، {{cssxref("direction")}} و {{cssxref("text-orientation")}} که در این ماژول تعریف شده‌اند، مشخص می‌شود. این حالت عمدتاً بر اساس جهت پایهٔ درون‌خطی و جهت جریان بلوکی تعریف می‌شود.

برخی از زبان‌های افقی چپ‌به‌راست هستند، از جمله خطوط لاتین و هندی. برخی دیگر از زبان‌های افقی راست‌به‌چپ نوشته می‌شوند، از جمله خطوط عبری و عربی. گاهی متن نیاز به دوطرفه بودن دارد، مثلاً وقتی خطوط چپ‌به‌راست و راست‌به‌چپ با هم ترکیب می‌شوند. برخی از زبان‌ها را می‌توان با جهت عمودی نوشت، برای مثال خطوط چینی، ژاپنی و کرهای (CJK).

ماژول حالت‌های نوشتاری CSS به جهت‌گیری همهٔ حالت‌های نوشتاری می‌پردازد. ماژول‌های دیگر، مانند ماژول چیدمان روبی CSS، مدل‌های رندرینگ و کنترل‌های قالب‌بندی مربوط به نمایش حاشیه‌نویسی متن را ارائه می‌دهند.

مرجع
ویژگی‌ها
{{cssxref("direction")}}

{{cssxref("glyph-orientation-vertical")}}

{{cssxref("text-combine-upright")}}

{{cssxref("text-orientation")}}

{{cssxref("unicode-bidi")}}

{{cssxref("writing-mode")}}

واژه‌نامه و اصطلاحات
{{glossary("Baseline/Typography", "خط مبنا")}}

{{Glossary("Internationalization", "بین‌المللی‌سازی")}}

{{glossary("Localization", "بومی‌سازی")}}

{{glossary("Leading", "فاصلهٔ بین خطوط")}}

راهنماها
ایجاد کنترل‌های عمودی فرم

: این مقاله نحوهٔ استفاده از ویژگی‌های CSS {{cssxref("writing-mode")}} و {{cssxref("direction")}} را برای ایجاد و پیکربندی کنترل‌های عمودی فرم توضیح می‌دهد.

آشنایی با سیستم‌های حالت نوشتاری

: مروری کوتاه بر سیستم‌های حالت نوشتاری و جهت‌مندی آن‌ها.

مفاهیم مرتبط
ماژول متن CSS

{{cssxref("hanging-punctuation")}}

{{cssxref("hyphens")}}

{{cssxref("letter-spacing")}}

{{cssxref("line-break")}}

{{cssxref("overflow-wrap")}}

{{cssxref("text-align")}}

{{cssxref("text-align-last")}}

{{cssxref("text-indent")}}

{{cssxref("text-justify")}}

{{cssxref("word-break")}}

{{cssxref("word-spacing")}}

ماژول چیدمان درون‌خطی CSS

{{cssxref("alignment-baseline")}}

{{cssxref("dominant-baseline")}}

{{cssxref("line-height")}}

{{cssxref("text-box-edge")}}

{{cssxref("text-box-trim")}}

{{cssxref("text-box")}} (نوشتار فشرده)

{{cssxref("text-edge")}}

ماژول ویژگی‌ها و مقادیر منطقی CSS

{{glossary("Flow relative values", "مقادیر نسبی به جریان")}}

{{glossary("Inset properties", "ویژگی‌های فاصله‌گذاری داخلی")}}

{{glossary("Logical properties", "ویژگی‌های منطقی")}}

{{glossary("Physical properties", "ویژگی‌های فیزیکی")}}

ماژول نمایش CSS

{{cssxref("display")}}

{{CSSxRef("<display-internal>")}}

مدل قالب‌بندی بصری

محتویات تولیدشدهٔ CSS

{{CSSxRef("quotes")}}

SVG

{{SVGAttr("glyph-orientation-horizontal")}} {{deprecated_inline}}

{{SVGAttr("glyph-orientation-vertical")}} {{deprecated_inline}}

{{SVGAttr("writing-mode")}}

HTML

{{htmlelement("bdo")}}

{{htmlelement("blockquote")}}

{{htmlelement("q")}}

{{htmlelement("ruby")}}

{{htmlelement("sub")}}

{{htmlelement("sup")}}

ویژگی dir

ویژگی lang

JavaScript

راهنمای بین‌المللی‌سازی

شیء Intl

مشخصات
{{Specifications}}

همچنین ببینید
ماژول قلم‌های CSS

ماژول چیدمان روبی CSS

ماژول تزئین متن CSS

ماژول سبک‌های شمارندهٔ CSS

ماژول فهرست‌های CSS

ماژول محدوده‌بندی CSS: {{CSSxRef("contain-intrinsic-block-size")}} و {{CSSxRef("contain-intrinsic-inline-size")}}

ماژول سرریز CSS: {{CSSxRef("overflow-block")}} و {{CSSxRef("overflow-inline")}}

ماژول رفتار سرریز پیمایشی CSS: {{CSSxRef("overscroll-behavior-block")}} و {{CSSxRef("overscroll-behavior-inline")}}
