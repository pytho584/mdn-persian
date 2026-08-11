---
title: "<meta name=\"text-scale\">"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name/text-scale"
translated_by: "n8n + AI"
---

# مقدار `text-scale`

مقدار **`text-scale`** برای ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/meta/name) در عنصر {{htmlelement("meta")}} باعث می‌شود صفحهٔ شما در مقیاس‌بندی `font-size` اولیهٔ عنصر ریشه {{htmlelement("html")}} متناسب با تنظیمات مقیاس متن در سطح سیستم‌عامل و مرورگر مشارکت کند.

> [!WARNING]
> اگر برای فعال‌کردن این رفتار از `<meta name="text-scale" content="scale" />` در سایت خود استفاده می‌کنید، حتماً تست کنید که سایت شما مقیاس‌های متنی تا حداکثر ضریب مقیاس‌بندیِ پلتفرم‌های هدف را پشتیبانی می‌کند. این ضریب معمولاً در پلتفرم‌های موبایل از ۲۰۰٪ تا بیش از ۳۰۰٪ متغیر است و برخی ویژگی‌های دسترس‌پذیری مقیاس‌های بزرگ‌تری را هم فعال می‌کنند. مطمئن شوید که ظاهر سایت شما برای کاربرانی که اندازهٔ فونت سیستم‌عامل را بزرگ‌تر یا کوچک‌تر تنظیم می‌کنند، خراب نمی‌شود.

## نکات استفاده

یک عنصر `<meta name="text-scale">` ویژگی‌های اضافی زیر را دارد:

- [`content`](/en-US/docs/Web/HTML/Reference/Elements/meta#content)
  - : رفتار فعال‌سازی مقیاس `font-size` را مشخص می‌کند.
    مقدار آن یک کلیدواژه است که می‌تواند یکی از موارد زیر باشد:
    - `scale`
      - : صفحه را در مقیاس‌بندی `font-size` اولیهٔ عنصر ریشه {{htmlelement("html")}} متناسب با تنظیمات مقیاس متن در سطح سیستم‌عامل و مرورگر مشارکت می‌دهد. همچنین باعث می‌شود مرورگر مکانیزم‌ها و الگوریتم‌های موجود مبتنی‌بر مرورگر (مثلاً تنظیم خودکار اندازهٔ متن در موبایل) را غیرفعال کند.
    - `legacy`
      - : مقدار پیش‌فرض. صفحه در مقیاس‌بندی `font-size` عنصر ریشه متناسب با تنظیمات مقیاس متن سیستم‌عامل و مرورگر مشارکت نمی‌کند. این مقدار همان اثرِ نبودنِ عنصر `<meta>` را دارد (تنظیمات اندازهٔ فونت سیستم‌عامل نادیده گرفته می‌شود).

## توضیحات

عنصر `<meta name="text-scale" content="scale" />` را می‌توان در بخش {{htmlelement("head")}} سند قرار داد تا به مرورگر اعلام کند که اندازه‌بندی صفحه به‌گونه‌ای است که در تنظیمات مختلف اندازهٔ فونت کاربر به‌خوبی مقیاس‌پذیر خواهد بود؛ همچنین مکانیزم‌ها و الگوریتم‌های موجود مرورگر را غیرفعال می‌کند.

به‌طور مشخص، این عنصر مقدار `font-size` اولیهٔ عنصر ریشه {{htmlelement("html")}} را متناسب با تنظیمات اندازهٔ فونت تعریف‌شده توسط کاربر در سطح سیستم‌عامل و مرورگر تنظیم می‌کند. مقدار `initial` برای `font-size` ریشه `medium` است که مقدار واحد [`rem`](/en-US/docs/Web/CSS/Reference/Values/length#rem) را مشخص می‌کند. اگر `font-size` ریشه را روی یک واحد [طول نسبی به فونتِ محلی یا ریشه](/en-US/docs/Web/CSS/Guides/Values_and_units/Numeric_data_types#local_font-relative_lengths) تنظیم کنید یا اجازه دهید پیش‌فرض بماند، هر کلیدواژهٔ بعدی (مثل `medium`) یا طول نسبی به فونت (مثل `em` و `rem`) متناسب با تنظیمات اندازهٔ فونت سیستم‌عامل یا مرورگر مقیاس می‌شود.

برای مثال، با وجود `<meta name="text-scale" content="scale">` در صفحه، قانون زیر:

```css
p {
  font-size: medium;
}
```

باعث می‌شود همهٔ عناصر {{htmlelement("p")}} اندازهٔ فونت مقیاس‌شده دریافت کنند. همچنین می‌توانید `font-size` را برابر `initial` قرار دهید تا همان اثر را بگیرید.

در پلتفرم‌های موبایل، این رفتار به‌صورت پیش‌فرض وجود ندارد و `<meta name="text-scale" content="scale" />` این مقیاس‌بندی را فعال می‌کند. در پلتفرم‌های دسکتاپ، اثر آن این است که متغیر محیطی [`env(preferred-text-scale)`](/en-US/docs/Web/CSS/Reference/Values/env#preferred-text-scale) ضریبی را که با تنظیمات اندازهٔ فونت مرورگر متناظر است بازتاب می‌دهد، اما جدا از این، مزیت قابل‌توجه دیگری ندارد.

### خلاصهٔ استفاده

به‌طور خلاصه، فقط زمانی از `scale` استفاده کنید که برنامهٔ شما برای پشتیبانی از مقیاس‌بندی فونت طراحی شده باشد. استفادهٔ پیشنهادی این است که:

1. `<meta name="text-scale" content="scale" />` را در `<head>` صفحهٔ خود قرار دهید.
2. مقدار `font-size` اولیهٔ `:root` را با یک مقدار [طول مطلق](/en-US/docs/Web/CSS/Reference/Values/length#absolute_length_units) (مثل `16px`) بازنویسی نکنید.
3. برای اندازه‌گذاری محتوا فقط از [واحدهای نسبتبه‌فونت](/en-US/docs/Web/CSS/Reference/Values/length#relative_length_units_based_on_font) مانند `em`/`rem` یا کلیدواژه‌هایی مثل `small`، `x-large` و غیره استفاده کنید.

### `<meta name="text-scale">` در مقایسه با `env(preferred-text-scale)`

استفاده از `<meta name="text-scale" />` برای اندازه‌گذاری ابعاد نسبت به تنظیمات مقیاس متن سیستم‌عامل، به‌جای متغیر محیطی [`env(preferred-text-scale)`](/en-US/docs/Web/CSS/Reference/Values/env#preferred-text-scale) توصیه می‌شود. این دو روی موبایل اثر مشابهی دارند، اما `<meta>` بهبودهایی نیز برای مرورگرهای دسکتاپ فراهم می‌کند (و استفاده از آن آسان‌تر است).

از استفاده همزمان هر دو ویژگی خودداری کنید، زیرا ممکن است مقیاس متن دو بار اعمال شود و ابعاد کوچک مبتنی‌برفونت کوچک‌تر و ابعاد بزرگ مبتنی‌برفونت بزرگ‌تر شوند.

## مثال‌ها

### نمایش اثر متای text-scale

این مثال اثر `<meta name="text-scale" content="scale">` را نشان می‌دهد.

#### HTML

ما المان `<meta name="text-scale" content="scale">` را در `<head>` سند قرار داده‌ایم، به‌علاوهٔ یک المان [`<meta name="viewport">`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/viewport) تا نمایش صحیح در دستگاه‌های موبایل تضمین شود. همچنین چند محتوای متنی داخل المان‌های `<p>` با `class`های متفاوت اضافه کرده‌ایم تا بتوانیم آن‌ها را با استایل‌های مختلف هدف قرار دهیم.

```html live-sample___text-scale
<!doctype html>
<html lang="en-US">
  <head>
    <meta name="text-scale" content="scale" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
  </head>
  <body>
    <p class="text-scale">
      This font size obeys the user's font preferences, whether those
      preferences are specified at the operating system level or the user agent
      level.
    </p>
    <p class="fixed">
      This font size does NOT respect the user's font preferences, even with
      text-scale set.
      <span class="text-scale">But this font size does!</span>
    </p>
  </body>
</html>
```

```html hidden live-sample___no-text-scale
<!doctype html>
<html lang="en-US">
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
  </head>
  <body>
    <p class="text-scale">
      This font size does not obey the user's font preferences, whether those
      preferences are specified at the operating system level or the user agent
      level.
    </p>
    <p class="fixed">
      This font size does NOT respect the user's font preferences.
      <span class="text-scale">Neither does this!</span>
    </p>
  </body>
</html>
```

#### CSS

به کانتینرهای متنی که `class` آن‌ها `text-scale` است، یک `font-size` برابر با `1rem` داده می‌شود. یعنی در مرورگرهایی که از `<meta name="text-scale" content="scale">` پشتیبانی می‌کنند، این متن با تغییر تنظیمات فونت سیستم‌عامل/مرورگر مقیاس خواهد شد. به کانتینرهای متنی با `class` برابر با `fixed` نیز `font-size` برابر با `20px` داده می‌شود؛ یعنی این متن با تغییر تنظیمات فونت سیستم‌عامل/مرورگر در اندازهٔ ثابت باقی می‌ماند.

```css live-sample___text-scale live-sample___no-text-scale
.text-scale {
  font-size: 1rem;
}

.fixed {
  font-size: 20px;
}
```

#### نتیجه

این نسخه شامل المان `<meta name="text-scale">` است:

این نسخه المان `<meta name="text-scale">` را شامل نمی‌شود:

### آزمایش در مرورگر موبایل

برای آزمایش این مثال‌ها، در مرورگر موبایل خود اندازهٔ فونت ترجیحی را از تنظیمات نمایش یا دسترس‌پذیری دستگاه تغییر دهید. در مثال اول، هنگامی که `<meta name="text-scale">` در صفحه وجود دارد، خطوط بالا و پایین متن متناسب با تنظیمات سیستم‌عامل مقیاس می‌شوند. اما خط وسط که `font-size` آن با واحدهای absolute (مطلق) تنظیم شده، تغییری نمی‌کند. در غیاب عنصر `<meta name="text-scale">`، متن متناسب با تنظیمات سیستم‌عامل مقیاس نمی‌شود.

برای سهولت آزمایش، می‌توانید هر دو نسخه را در یک تب جداگانه به‌صورت تمام‌صفحه باز کنید:

- [مثال با `<meta name="text-scale">`](https://mdn.github.io/dom-examples/...)
- [مثال بدون `<meta name="text-scale">`](https://mdn.github.io/dom-examples/...)

### یک چیدمان واکنش‌گرا به مقیاس متن

این مثال نشان می‌دهد که با اعمال `<meta name="text-scale">` به صفحه، می‌توان از اندازه‌های نسبی به فونت درون کوئری‌های `@media` استفاده کرد تا مرورگر موبایل به‌طور خودکار نقاط شکست را با تغییر اندازهٔ متن سیستم‌عامل تنظیم کند.

#### HTML

مانند مثال قبلی، نشانه‌گذاری ما شامل عناصر `<meta name="text-scale">` و `<meta name="viewport">` درون `<head>` است. در این نسخه، محتوای بدنه شامل دو عنصر `<main>` و `<aside>` است که یک ستون محتوای اصلی و یک نوار کناری را نمایش می‌دهند.

```html live-sample___text-scale-layout
<!doctype html>
<html lang="en-US">
  <head>
    <meta name="text-scale" content="scale" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
  </head>
  <body>
    <main>Main content</main>
    <aside>Aside content</aside>
  </body>
</html>
```

#### CSS

به‌طور پیش‌فرض، محتوای اصلی و نوار کناری به‌صورت عمودی (یکی زیر دیگری) چیده می‌شوند. ما یک کوئری `@media` اضافه کرده‌ایم که وقتی viewport از `35rem` عریض‌تر می‌شود، عناصر را با استفاده از [CSS Grid](/en-US/docs/Web/CSS/Guides/Grid_layout) در کنار هم قرار می‌دهد.

```css hidden live-sample___text-scale-layout
body {
  margin: 0;
}

main,
aside {
  background-color: silver;
  padding: 24px;
  font-size: 1.5rem;
}
```

```css live-sample___text-scale-layout
@media (width > 35rem) {
  body {
    display: grid;
    gap: 24px;
    grid-template-columns: 1fr 18.75rem;
  }
}
```

#### نتیجه

این مثال را در یک مرورگر موبایل آزمایش کنید. خواهید دید که با افزایش اندازهٔ فونت سیستم‌عامل، اندازهٔ نقطه شکست نیز متناسب با آن افزایش می‌یابد. در اندازه‌های بزرگ‌تر فونت سیستم‌عامل، `<main>` و `<aside>` به‌جای کنار هم، دوباره یکی زیر دیگری قرار می‌گیرند. برای مشاهدهٔ این اثر ممکن است لازم باشد صفحه را به حالت افقی بچرخانید.

برای سهولت آزمایش، می‌توانید دمو را در یک تب جداگانه با استفاده از لینک زیر باز کنید:

- [مثال چیدمان واکنش‌گرا](https://mdn.github.io/dom-examples/...)

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [`env(preferred-text-scale)`](/en-US/docs/Web/CSS/Reference/Values/env#preferred-text-scale)
- [پشتیبانی از `<meta text-scale>` در WebView](https://chromium.googlesource.com/chromium/src/+/b29d63222d10f4c7e620d057578d737969eb7ae3) در chromium.googlesource.com (2026)