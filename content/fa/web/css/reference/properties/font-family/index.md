---
title: "font-family CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/font-family"
translated_by: "n8n + AI"
---

ویژگی `font-family` در CSS یک لیست اولویت‌بندی‌شده از یک یا چند نام خانوادهٔ فونت (font family) و/یا نام‌های خانوادهٔ عمومی (generic family) را برای عنصر انتخاب‌شده مشخص می‌کند.

مقادیر با کاما از هم جدا می‌شوند تا نشان دهند گزینه‌های جایگزین هستند. مرورگر اولین فونتی را در این لیست انتخاب می‌کند که روی سیستم نصب باشد یا با استفاده از قاعدهٔ `@font-face` قابل دانلود باشد.

معمولاً استفاده از ویژگی خلاصهٔ `font` برای تنظیم هم‌زمان `font-size` و دیگر ویژگی‌های مربوط به فونت راحت‌تر است.

همیشه باید حداقل یک نام خانوادهٔ عمومی در لیست `font-family` قرار دهید، چون هیچ تضمینی نیست که یک فونت مشخص در دسترس باشد. این کار به مرورگر اجازه می‌دهد در صورت نیاز یک فونت جایگزین (fallback) قابل‌قبول انتخاب کند.

ویژگی `font-family` یک لیست از فونت‌ها را، از بالاترین اولویت تا پایین‌ترین، مشخص می‌کند. انتخاب فونت با رسیدن به اولین فونت موجود در سیستم کاربر متوقف *نمی‌شود*. بلکه انتخاب فونت *کاراکتر به کاراکتر* انجام می‌شود؛ یعنی اگر فونت در دسترس، گلیف (glyph) لازم برای یک کاراکتر را نداشته باشد، فونت‌های بعدی در لیست امتحان می‌شوند. وقتی یک فونت فقط در برخی [استایل‌ها](/en-US/docs/Web/CSS/Reference/Properties/font-style)، [حالت‌ها](/en-US/docs/Web/CSS/Reference/Properties/font-variant)، یا [اندازه‌ها](/en-US/docs/Web/CSS/Reference/Properties/font-size) در دسترس باشد، این ویژگی‌ها هم ممکن است بر انتخاب خانوادهٔ فونت تأثیر بگذارند.

## نحوهٔ نگارش

```css
/* یک نام خانوادهٔ فونت و یک نام خانوادهٔ عمومی */
font-family: "Gill Sans Extrabold", sans-serif;
font-family: "Goudy Bookletter 1911", sans-serif;

/* فقط یک نام خانوادهٔ عمومی */
font-family: serif;
font-family: sans-serif;
font-family: monospace;
font-family: cursive;
font-family: fantasy;
font-family: system-ui;
font-family: ui-serif;
font-family: ui-sans-serif;
font-family: ui-monospace;
font-family: ui-rounded;
font-family: math;
font-family: fangsong;

/* مقادیر سراسری */
font-family: inherit;
font-family: initial;
font-family: revert;
font-family: revert-layer;
font-family: unset;
```

ویژگی `font-family` یک یا چند خانوادهٔ فونت را که با کاما از هم جدا شده‌اند فهرست می‌کند. هر خانوادهٔ فونت به‌صورت یک `<family-name>` یا یک `<generic-name>` مشخص می‌شود.

مثال زیر دو خانوادهٔ فونت را فهرست می‌کند، اولی با یک `<family-name>` و دومی با یک `<generic-name>`:

```css
font-family: "Gill Sans Extrabold", sans-serif;
```

### مقادیر

- `<family-name>`
  - : نام یک خانوادهٔ فونت. این مقدار باید یا یک {{cssxref("string")}} تکی باشد یا دنباله‌ای از مقادیر {{cssxref("custom-ident")}} که با فاصله جدا شده‌اند. مقادیر رشته‌ای باید داخل گیومه قرار بگیرند اما می‌توانند هر کاراکتر یونیکدی را شامل شوند. شناسه‌های سفارشی (custom identifiers) گیومه نمی‌خورند، ولی برخی کاراکترها باید escape شوند. بهتر است نام خانوادهٔ فونت‌هایی که شامل فاصله، رقم یا نشانه‌های نقطه‌گذاری (به‌جز خط تیره) هستند را داخل گیومه بگذارید.

    همچنین ببینید [نام‌های معتبر خانواده فونت](#valid_family_names).

- `<generic-name>`
  - : خانواده‌های فونت عمومی (generic) یک سازوکار جایگزین هستند؛ روشی برای حفظ بخشی از هدف نویسندهٔ stylesheet وقتی هیچ‌یک از فونت‌های مشخص‌شده در دسترس نباشند. نام‌های خانوادهٔ عمومی کلمات کلیدی هستند و نباید داخل گیومه قرار بگیرند. خانوادهٔ فونت عمومی باید آخرین آیتم در لیست نام‌های خانوادهٔ فونت باشد. کلمات کلیدی زیر تعریف شده‌اند:
    - `serif`
      - : حروف (گلیف‌ها) دارای خطوط انتهایی کامل، انتهای پهن یا باریک، یا واقعاً دندانه‌دار (سریف) هستند.

        برای مثال: Lucida Bright, Lucida Fax, Palatino, Palatino Linotype, Palladio, URW Palladio, serif.

    - `sans-serif`
      - : حروف دارای انتهای ساده و بدون تزئین هستند.

        برای مثال: Open Sans, Fira Sans, Lucida Sans, Lucida Sans Unicode, Trebuchet MS, Liberation Sans, Nimbus Sans L, sans-serif.

    - `monospace`
      - : همهٔ حروف دارای عرض ثابت و یکسانی هستند.

        برای مثال: Fira Mono, DejaVu Sans Mono, Menlo, Consolas, Liberation Mono, Monaco, Lucida Console, monospace.

    - `cursive`
      - : حروف در فونت‌های شکسته (cursive) عموماً دارای اتصالات یا دیگر ویژگی‌های شکسته فراتر از نوع ایتالیک هستند. گلیف‌ها به‌طور جزئی یا کامل به هم متصل می‌شوند و نتیجه بیشتر شبیه دست‌خط با قلم یا قلم‌مو به نظر می‌رسد تا حروف چاپی.

        برای مثال: Brush Script MT, Brush Script Std, Lucida Calligraphy, Lucida Handwriting, Apple Chancery, cursive.

    - `fantasy`
      - : فونت‌های فانتزی (fantasy) عمدتاً فونت‌های تزئینی هستند که نمایش‌های فانتزی و بازی‌گوشانه‌ای از کاراکترها دارند.

        برای مثال: Papyrus, Herculanum, Party LET, Curlz MT, Harrington, fantasy.

    - `system-ui`
      - : گلیف‌ها از فونت رابط کاربری پیش‌فرض در یک پلتفرم مشخص گرفته می‌شوند. از آنجا که سنت‌های تایپوگرافی در سراسر جهان بسیار متفاوت است، این خانوادهٔ عمومی برای فونت‌هایی ارائه شده که به‌خوبی در دسته‌های عمومی دیگر جای نمی‌گیرند.
        > [!NOTE]
        > همان‌طور که از نامش پیداست، `system-ui` برای آن است که عناصر رابط کاربری شبیه برنامه‌های بومی (native) به نظر برسند و برای حروفچینی پاراگراف‌های بلند متن مناسب نیست. ممکن است باعث شود فونت نمایش‌داده‌شده برای برخی کاربران مطلوب نباشد – برای مثال، فونت پیش‌فرض CJK در ویندوز ممکن است خط لاتین را ضعیف نمایش دهد و ویژگی `lang` هم روی فونت نمایشی تأثیر نگذارد. برخی سیستم‌عامل‌ها امکان شخصی‌سازی `system-ui` را نمی‌دهند، درحالی‌که مرورگرها عموماً اجازهٔ شخصی‌سازی خانواده فونت `sans-serif` را می‌دهند. برای پاراگراف‌های بلند، به‌جای آن از `sans-serif` یا یک خانواده فونت غیر از رابط کاربری استفاده کنید.
    - `ui-serif`
      - : فونت سریف (serif) پیش‌فرض رابط کاربری.
    - `ui-sans-serif`
      - : فونت بدون‌سریف (sans-serif) پیش‌فرض رابط کاربری.
    - `ui-monospace`
      - : فونت تک‌فاصله (monospace) پیش‌فرض رابط کاربری.
    - `ui-rounded`
      - : فونت پیش‌فرض رابط کاربری که دارای ویژگی‌های گردشده است.
    - `math`
      - : فونتی که به نگرانی‌های سبکی خاص نمایش ریاضیات می‌پردازد: بالانویس و پایین‌نویس، کروشه‌هایی که چند خط را می‌پیمایند، عبارت‌های تودرتو و حروف دوبل با معانی متمایز.
        شیوه‌نامه‌های عامل کاربر (UA) ممکن است `math { font-family: math }` را تنظیم کنند تا عنصر `<math>` به‌طور پیش‌فرض از فونت‌های مناسب استفاده کند.
    - `fangsong`
      - : سبکی خاص از کاراکترهای چینی که بین فرم Song سریف‌دار و Kai شکسته‌نگار قرار می‌گیرد. این سبک اغلب برای اسناد دولتی استفاده می‌شود.

## مثال‌ها

### چند خانواده فونت متداول

```css
.serif {
  font-family: "Times", "Times New Roman", "Georgia", serif;
}

.sansserif {
  font-family: "Verdana", "Helvetica", "Arial", sans-serif;
}

.monospace {
  font-family: "Lucida Console", "Courier New", monospace;
}

.cursive {
  font-family: cursive;
}

.fantasy {
  font-family: fantasy;
}

.math {
  font-family: math;
}

.fangsong {
  font-family: fangsong;
}
```

```css hidden
div {
  margin: 0.5rem;
}
```

```html hidden
<div class="serif">This is an example of a serif font.</div>
```

```html
<div class="sansserif">این یک نمونه از فونت sans-serif است.</div>

<div class="monospace">این یک نمونه از فونت monospace است.</div>

<div class="cursive">این یک نمونه از فونت cursive است.</div>

<div class="fantasy">این یک نمونه از فونت fantasy است.</div>

<div class="fangsong">این یک نمونه از فونت fangsong است.</div>

<div class="math">این یک نمونه از فونت math است: ℝ, ∫, ∑…</div>
```

### نام‌های معتبر خانواده فونت

اعلان‌های زیر معتبر هستند:

```css example-good
font-family: "Goudy Bookletter 1911", sans-serif;
```

اعلان‌های زیر نامعتبر هستند:

```css-nolint example-bad
font-family: Goudy Bookletter 1911, sans-serif;
font-family: Red/Black, sans-serif;
font-family: "Lucida" Grande, sans-serif;
font-family: Ahem!, sans-serif;
font-family: test@foo, sans-serif;
font-family: #POUND, sans-serif;
font-family: Hawaii 5-0, sans-serif;
```

مثال زیر از نظر فنی معتبر است اما توصیه نمی‌شود:

```css
font-family:
  Gill Sans Extrabold,
  sans-serif;
```

## همچنین ببینید

- `font-style`
- `font-weight`
- `font-variant-emoji`
- SVG `font-family` attribute
- [آموزش: اصول استایل‌دهی متن و فونت](/en-US/docs/Learn_web_development/Core/Text_styling/Fundamentals)