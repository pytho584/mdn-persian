---
title: "grid-template-columns CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid-template-columns"
translated_by: "n8n + AI"
---

# ویژگی `grid-template-columns` در CSS

ویژگی **`grid-template-columns`** در [CSS](/en-US/docs/Web/CSS) نام خطوط و توابع اندازه‌دهی مسیرها (track sizing functions) را برای ستون‌های گرید (grid columns) تعیین می‌کند.

## سینتکس

```css
/* مقدار کلیدی */
grid-template-columns: none;

/* مقادیر <track-list> */
grid-template-columns: 100px 1fr;
grid-template-columns: [line-name] 100px;
grid-template-columns: [line-name1] 100px [line-name2 line-name3];
grid-template-columns: minmax(100px, 1fr);
grid-template-columns: fit-content(40%);
grid-template-columns: repeat(3, 200px);
grid-template-columns: subgrid;
grid-template-columns: masonry;

/* مقادیر <auto-track-list> */
grid-template-columns: 200px repeat(auto-fill, 100px) 300px;
grid-template-columns:
  minmax(100px, max-content)
  repeat(auto-fill, 200px) 20%;
grid-template-columns:
  [line-name1] 100px [line-name2]
  repeat(auto-fit, [line-name3 line-name4] 300px)
  100px;
grid-template-columns:
  [line-name1 line-name2] 100px
  repeat(auto-fit, [line-name1] 300px) [line-name3];

/* مقادیر سراسری */
grid-template-columns: inherit;
grid-template-columns: initial;
grid-template-columns: revert;
grid-template-columns: revert-layer;
grid-template-columns: unset;
```

### مقادیر

- `none`
  - : نشان می‌دهد که هیچ گرید صریحی (explicit grid) وجود ندارد. ستون‌ها به‌صورت ضمنی تولید می‌شوند و اندازهٔ آن‌ها توسط ویژگی {{cssxref("grid-auto-columns")}} تعیین می‌گردد.
- `[line-name]`
  - : یک شناسهٔ سفارشی (custom-ident) که نامی برای خط در آن موقعیت مشخص می‌کند. شناسه می‌تواند هر رشتهٔ معتبری باشد، غیر از کلمات رزروشدهٔ `span` و `auto`. خط‌ها می‌توانند چندین نام داشته باشند که با فاصله درون براکت‌ها جدا می‌شوند، برای مثال `[line-name-a line-name-b]`.
- {{cssxref("&lt;length&gt;")}}‏
  - : یک طول غیرمنفی که عرض ستون را تعیین می‌کند.
- {{cssxref("&lt;percentage&gt;")}}‏
  - : مقداری درصدی و غیرمنفی نسبت به اندازهٔ درون‌خطی (inline size) محفظهٔ گرید. اگر اندازهٔ محفظهٔ گرید به اندازهٔ مسیرهای آن وابسته باشد، مرورگر درصد را به‌عنوان `auto` در نظر می‌گیرد. مرورگر ممکن است اندازهٔ ذاتی مسیر را متناسب با محفظه تنظیم کند و اندازهٔ نهایی مسیر را به کمترین مقدار لازم برای رعایت درصد افزایش دهد.
- {{cssxref("&lt;flex&gt;")}}‏
  - : یک مقدار غیرمنفی با واحد `fr` که ضریب انعطاف‌پذیری (flex factor) مسیر را مشخص می‌کند. هر مسیری که با `<flex>` اندازه‌گیری شده باشد، نسبتی از فضای باقی‌مانده را به‌تناسب ضریب خود دریافت می‌کند.

    وقتی این مقدار خارج از تابع `minmax()` ظاهر می‌شود، به‌صورت خودکار یک حداقل خودکار (یعنی `minmax(auto, <flex>)`) برای آن در نظر گرفته می‌شود.

- `max-content`
  - : یک کلیدواژه است که نمایانگر بزرگترین [بیشینهٔ مشارکت محتوا](https://drafts.csswg.org/css-sizing-3/#max-content) (maximal content contribution) در بین آیتم‌های grid قرارگرفته در track است. برای مثال، اگر اولین عنصر track شامل جملهٔ _"Repetitio est mater studiorum"_ و دومین عنصر شامل _"Dum spiro, spero"_ باشد، بیشینهٔ مشارکت محتوا با اندازهٔ بزرگترین جمله در میان همهٔ عناصر grid تعیین می‌شود: _"Repetitio est mater studiorum"_.
- `min-content`
  - : یک کلیدواژه است که نمایانگر بزرگترین [کمینهٔ مشارکت محتوا](https://drafts.csswg.org/css-sizing-3/#min-content) (minimal content contribution) در بین آیتم‌های grid قرارگرفته در track است. برای مثال، اگر اولین عنصر track شامل جملهٔ _"Repetitio est mater studiorum"_ و دومین عنصر شامل _"Dum spiro, spero"_ باشد، کمینهٔ مشارکت محتوا با اندازهٔ بزرگترین کلمه در میان همهٔ جمله‌ها تعیین می‌شود: _"studiorum"_.
- `minmax(min, max)`
  - : یک نماد تابعی است که یک بازهٔ اندازه تعریف می‌کند: بزرگتر یا مساوی با _min_ و کوچکتر یا مساوی با _max_. اگر _max_ از _min_ کوچکتر باشد، _max_ نادیده گرفته می‌شود و تابع معادل _min_ رفتار می‌کند. به‌عنوان بیشینه، مقدار `<flex>` ضریب انعطاف‌پذیری track را مشخص می‌کند. این مقدار به‌عنوان کمینه معتبر نیست.
- `auto`
  - : به‌عنوان مقدار بیشینه، نمایانگر بزرگترین اندازهٔ `max-content` آیتم‌های موجود در آن track است.

    به‌عنوان مقدار کمینه، نمایانگر بزرگترین اندازهٔ کمینهٔ آیتم‌ها در آن track است (که با ویژگی‌های `min-width`/`min-height` آیتم‌ها مشخص می‌شود). این معمولاً با اندازهٔ `min-content` برابر است، اما همیشه این‌طور نیست.

    اگر خارج از نماد `minmax()` استفاده شود، `auto` بازهٔ بین مقادیر کمینه و بیشینهٔ توصیف‌شده در بالا را نشان می‌دهد. در بیشتر موارد، این مشابه `minmax(min-content,max-content)` رفتار می‌کند.

    > [!NOTE]
    > اندازه‌های track با مقدار `auto` (و فقط این اندازه‌ها) می‌توانند با ویژگی‌های `align-content` و `justify-content` کشیده شوند. بنابراین، به‌طور پیش‌فرض، یک track با اندازهٔ `auto` هر فضای باقی‌مانده در grid container را اشغال خواهد کرد.

- `fit-content( [ <length> | <percentage> ] )`
  - : نمایش‌دهندهٔ فرمول `max(minimum, min(limit, max-content))` است، که در آن _minimum_ یک کمینهٔ `auto` را نشان می‌دهد (که اغلب، اما نه همیشه، برابر با کمینهٔ `min-content` است) و _limit_ همان تابع اندازه‌دهی track است که به‌عنوان آرگومان به `fit-content()` داده می‌شود. در اصل، این مقدار به‌عنوان کوچک‌ترین مقدار بین `minmax(auto, max-content)` و `minmax(auto, limit)` محاسبه می‌شود.
- `repeat( [ <positive-integer> | auto-fill | auto-fit ] , <track-list> )`
  - : نمایانگر یک قطعهٔ تکراری از لیست track است و اجازه می‌دهد تعداد زیادی ستون با الگوی تکرارشونده به‌صورت فشرده‌تر نوشته شود.
- [`masonry`](/en-US/docs/Web/CSS/Guides/Grid_layout/Masonry_layout)
  - : مقدار `masonry` نشان می‌دهد که این محور باید بر اساس الگوریتم masonry چیده شود.
- [`subgrid`](/en-US/docs/Web/CSS/Guides/Grid_layout/Subgrid)
  - : مقدار `subgrid` نشان می‌دهد که grid بخش پوشش‌داده‌شده از grid والد خود را در آن محور به ارث می‌برد. به‌جای مشخص‌سازی صریح، اندازه‌های سطرها/ستون‌های grid از تعریف grid والد گرفته می‌شود.

## مثال‌ها

### تعیین اندازه ستون‌های گرید

#### HTML

```html
<div id="grid">
  <div id="areaA">A</div>
  <div id="areaB">B</div>
</div>
```

#### CSS

```css
#grid {
  display: grid;
  width: 100%;
  grid-template-columns: 50px 1fr;
}

#areaA {
  background-color: lime;
}

#areaB {
  background-color: yellow;
}
```

## سازگاری با مرورگرها

## همچنین ببینید

- [`grid-template-rows`](/en-US/docs/Web/CSS/grid-template-rows)
- [`grid-template-areas`](/en-US/docs/Web/CSS/grid-template-areas)
- [`grid-template`](/en-US/docs/Web/CSS/grid-template)
- [مفاهیم پایه‌ای طرح‌بندی گرید: grid tracks](/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts#grid_tracks)
- ویدئو: [Defining a grid](https://gridbyexample.com/video/series-define-a-grid/)
- [Subgrid](/en-US/docs/Web/CSS/Guides/Grid_layout/Subgrid)