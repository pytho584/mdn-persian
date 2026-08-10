---
title: "font-weight CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/font-weight"
translated_by: "n8n + AI"
---

ویژگی **`font-weight`** در [CSS](/en-US/docs/Web/CSS) میزان ضخامت (یا bold بودن) فونت را تعیین می‌کند. ضخامت‌های در دسترس به فونت خانواده‌ای که در حال حاضر با {{cssxref("font-family")}} تنظیم شده بستگی دارد.

## نحوه نگارش

```css
/* مقادیر کلیدی <font-weight-absolute> */
font-weight: normal;
font-weight: bold;

/* مقادیر عددی <font-weight-absolute> [1,1000] */
font-weight: 100;
font-weight: 200;
font-weight: 300;
font-weight: 400; /* normal */
font-weight: 500;
font-weight: 600;
font-weight: 700; /* bold */
font-weight: 800;
font-weight: 900;

/* مقادیر کلیدی نسبی به عنصر والد */
font-weight: lighter;
font-weight: bolder;

/* مقادیر سراسری */
font-weight: inherit;
font-weight: initial;
font-weight: revert;
font-weight: revert-layer;
font-weight: unset;
```

ویژگی `font-weight` با استفاده از یکی از مقادیر `<font-weight-absolute>` یا یک مقدار نسبی، مطابق فهرست زیر مشخص می‌شود.

### مقادیر

- `normal`
  - : ضخامت فونت معمولی. معادل `400`.

- `bold`
  - : ضخامت فونت بولد. معادل `700`.

- `<number>`
  - : یک مقدار {{cssxref("&lt;number&gt;")}} بین ۱ و ۱۰۰۰ که هر دو مقدار شامل این بازه می‌شوند. اعداد بزرگ‌تر نشان‌دهنده ضخامت‌هایی هستند که نسبت به اعداد کوچک‌تر بولدتر (یا هم‌سطح) هستند. این امکان کنترل دقیق را برای [فونت‌های متغیر](#فونت‌های_متغیر) فراهم می‌کند. برای فونت‌های غیر متغیر، اگر ضخامت دقیق مشخص‌شده در دسترس نباشد، از یک الگوریتم [ضخامت جایگزین](#ضخامت‌های_جایگزین) استفاده می‌شود — مقادیر عددی که بر ۱۰۰ بخش‌پذیرند با نام‌های رایج ضخامت مطابقت دارند، همانطور که در بخش [نگاشت نام‌های رایج ضخامت](#نگاشت_نام‌های_رایج_ضخامت) در زیر توضیح داده شده است.

- `lighter`
  - : یک واحد ضخامت فونت نسبی، نازک‌تر از عنصر والد. توجه داشته باشید که برای محاسبه ضخامت نسبی فقط چهار ضخامت در نظر گرفته می‌شود؛ به بخش [معنای ضخامت‌های نسبی](#معنای_ضخامت‌های_نسبی) در زیر مراجعه کنید.

- `bolder`
  - : یک واحد ضخامت فونت نسبی، ضخیم‌تر از عنصر والد. توجه داشته باشید که برای محاسبه ضخامت نسبی فقط چهار ضخامت در نظر گرفته می‌شود؛ به بخش [معنای ضخامت‌های نسبی](#معنای_ضخامت‌های_نسبی) در زیر مراجعه کنید.

### ضخامت‌های جایگزین

اگر ضخامت دقیق داده شده در دسترس نباشد، آنگاه از قاعده زیر برای تعیین ضخامتی که واقعاً رندر می‌شود استفاده می‌شود:

- اگر ضخامت هدف داده شده بین `400` و `500` (شامل هر دو) باشد:
  - به دنبال ضخامت‌های در دسترس بین ضخامت هدف و `500`، به ترتیب صعودی بگرد.
  - اگر موردی پیدا نشد، به دنبال ضخامت‌های در دسترس کوچک‌تر از ضخامت هدف، به ترتیب نزولی بگرد.
  - اگر موردی پیدا نشد، به دنبال ضخامت‌های در دسترس بزرگ‌تر از `500`، به ترتیب صعودی بگرد.

- اگر ضخامتی کمتر از `400` داده شود، به دنبال ضخامت‌های در دسترس کوچک‌تر از ضخامت هدف، به ترتیب نزولی بگرد. اگر موردی پیدا نشد، به دنبال ضخامت‌های در دسترس بزرگ‌تر از ضخامت هدف، به ترتیب صعودی بگرد.

اگر وزنی بزرگ‌تر از `500` تعیین شود، ابتدا وزن‌های موجود که بزرگ‌تر از مقدار هدف هستند، به ترتیب صعودی جستجو می‌شوند. اگر موردی پیدا نشد، وزن‌های موجود که کوچک‌تر از هدف هستند، به ترتیب نزولی بررسی می‌شوند.

> [!NOTE]
> الگوریتم وزن جایگزین فقط هنگام رندرینگ به کار می‌رود. مقدار محاسبه‌شده (computed value) ویژگی همچنان همان مقدار مشخص‌شده (specified value) باقی می‌ماند.

### معنای وزن‌های نسبی

زمانی که `lighter` یا `bolder` مشخص می‌شود، نمودار زیر نشان می‌دهد که وزن مطلق قلم برای آن عنصر چگونه تعیین می‌شود.

توجه کنید که وقتی از وزن‌های نسبی استفاده می‌کنید، فقط چهار وزن قلم در نظر گرفته می‌شوند — thin (۱۰۰)، normal (۴۰۰)، bold (۷۰۰) و heavy (۹۰۰). اگر خانوادهٔ قلم وزن‌های بیشتری در دسترس داشته باشد، این وزن‌ها برای محاسبهٔ وزن نسبی نادیده گرفته می‌شوند.

<table class="standard-table">
  <thead>
    <tr>
      <th>مقدار به‌ارث‌برده</th>
      <th><code>bolder</code></th>
      <th><code>lighter</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>400</td>
      <td>100</td>
    </tr>
    <tr>
      <th>200</th>
      <td>400</td>
      <td>100</td>
    </tr>
    <tr>
      <th>300</th>
      <td>400</td>
      <td>100</td>
    </tr>
    <tr>
      <th>400</th>
      <td>700</td>
      <td>100</td>
    </tr>
    <tr>
      <th>500</th>
      <td>700</td>
      <td>100</td>
    </tr>
    <tr>
      <th>600</th>
      <td>900</td>
      <td>400</td>
    </tr>
    <tr>
      <th>700</th>
      <td>900</td>
      <td>400</td>
    </tr>
    <tr>
      <th>800</th>
      <td>900</td>
      <td>700</td>
    </tr>
    <tr>
      <th>900</th>
      <td>900</td>
      <td>700</td>
    </tr>
  </tbody>
</table>

### نگاشت نام‌های رایج وزن

مقادیر عددی `100` تا `900` تقریباً با نام‌های رایج وزن زیر مطابقت دارند (مشاهدهٔ [مشخصات OpenType](https://learn.microsoft.com/en-us/typography/opentype/spec/os2#usweightclass)):

| مقدار | نام رایج وزن                                                                                                                       |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------- |
| 100   | Thin (Hairline)                                                                                                                    |
| 200   | Extra Light (Ultra Light)                                                                                                          |
| 300   | Light                                                                                                                              |
| 400   | Normal (Regular)                                                                                                                   |
| 500   | Medium                                                                                                                             |
| 600   | Semi Bold (Demi Bold)                                                                                                              |
| 700   | Bold                                                                                                                               |
| 800   | Extra Bold (Ultra Bold)                                                                                                            |
| 900   | Black (Heavy)                                                                                                                      |
| 950   | [Extra Black (Ultra Black)](https://learn.microsoft.com/en-us/dotnet/api/system.windows.fontweights?view=netframework-4.8#remarks) |

### قلم‌های متغیر

هرچند بسیاری از قلم‌ها یک وزن مشخص متناظر با یکی از اعداد [نگاشت نام‌های رایج وزن](#common_weight_name_mapping) دارند، اغلب قلم‌های متغیر بازه‌ای از وزن‌ها را پشتیبانی می‌کنند که دانه‌بندی بسیار ظریف‌تری را فراهم می‌آورد و به طراحان و توسعه‌دهندگان کنترل بیشتری روی وزن انتخابی می‌دهد.

در قلم‌های متغیر TrueType یا OpenType، از تغییر `wght` برای پیاده‌سازی عرض‌های متغیر استفاده می‌شود.

این نسخهٔ نمایشی با `font-weight: 500;` بارگذاری می‌شود. مقدار ویژگی `font-weight` را در سلکتور `.sample` تغییر دهید تا وزن متن تغییر کند (مثلاً ۲۰۰ یا ۷۰۰). در بلوک‌های کد زیر روی «Play» کلیک کنید تا مثال را در MDN Playground ویرایش کنید:

```html live-sample___font-weight-example
<p class="sample">
  ...it would not be wonderful to meet a Megalosaurus, forty feet long or so,
  waddling like an elephantine lizard up Holborn Hill.
</p>
```

```css live-sample___font-weight-example
@font-face {
  src: url("https://mdn.github.io/shared-assets/fonts/variable-fonts/MutatorSans.ttf");
  font-family: "MutatorSans";
  font-style: normal;
  font-weight: 1 1000;
}

.sample {
  text-transform: uppercase;
  font-weight: 500;
  font-size: 1.5rem;
  font-family: "MutatorSans", sans-serif;
}
```

## دسترسی‌پذیری

افرادی که دچار کم‌بینایی هستند ممکن است در خواندن متنی که با `font-weight` مقدار `100` (Thin/Hairline) یا `200` (Extra Light) تنظیم شده است مشکل داشته باشند، به‌ویژه اگر فونت [نسبت کنتراست رنگ پایینی](/en-US/docs/Web/CSS/Reference/Properties/color#accessibility) داشته باشد.

- [توضیحات MDN دربارهٔ درک WCAG، راهنمای 1.4](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [درک معیار موفقیت 1.4.8 | W3C درک WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-visual-presentation.html)

## تعریف رسمی

## نحو رسمی

## مثال‌ها

### تنظیم وزن فونت

#### HTML

```html
<p>
  Alice was beginning to get very tired of sitting by her sister on the bank,
  and of having nothing to do: once or twice she had peeped into the book her
  sister was reading, but it had no pictures or conversations in it, "and what
  is the use of a book," thought Alice "without pictures or conversations?"
</p>

<div>
  I'm heavy<br />
  <span>I'm lighter</span>
</div>
```

#### CSS

```css
/* Set paragraph text to be bold. */
p {
  font-weight: bold;
}

/* Set div text to two steps heavier than
   normal but less than a standard bold. */
div {
  font-weight: 600;
}

/* Set span text to be one step lighter
   than its parent. */
span {
  font-weight: lighter;
}
```

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- [`font-family`](/en-US/docs/Web/CSS/font-family)
- [`font-style`](/en-US/docs/Web/CSS/font-style)
- SVG [`font-weight`](/en-US/docs/Web/SVG/Attribute/font-weight) attribute
- [یادگیری: اصول پایه استایل‌دهی متن و فونت](/en-US/docs/Learn_web_development/Core/Text_styling/Fundamentals)
- [ماژول فونت‌های CSS](/en-US/docs/Web/CSS/Guides/Fonts)