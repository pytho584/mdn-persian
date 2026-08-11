---
title: "Fallback options and conditional hiding for overflow"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding"
translated_by: "n8n + AI"
---

هنگام استفاده از [موقعیت‌یابی لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning)، یک نکته مهم این است که اطمینان حاصل کنید عناصر موقعیت‌یابی‌شده با لنگر، در صورت امکان، همیشه در جایی مناسب برای تعامل کاربر قرار بگیرند، صرف‌نظر از اینکه خود لنگر کجاست. مثلاً وقتی صفحه را اسکرول می‌کنید، لنگرها و عناصر موقعیت‌یابی‌شدهٔ مرتبط با آن‌ها به سمت لبهٔ viewport حرکت می‌کنند. وقتی یک عنصر موقعیت‌یابی‌شده شروع به سرریز شدن (overflow) از viewport می‌کند، باید موقعیت آن را تغییر دهید تا دوباره روی صفحه قرار گیرد، مثلاً در سمت مخالف لنگر.

در برخی موارد، ممکن است ترجیح دهید عناصر موقعیت‌یابی‌شده‌ای که سرریز می‌کنند را پنهان کنید — مثلاً اگر لنگرهای آن‌ها خارج از صفحه باشد، محتوایشان ممکن است نامفهوم شود.

این راهنما نحوه استفاده از مکانیزم‌های موقعیت‌یابی لنگر CSS برای مدیریت این مسائل را توضیح می‌دهد: **گزینه‌های fallback موقعیت‌یابی (position-try fallback options)** و **پنهان‌سازی شرطی (conditional hiding)**. گزینه‌های fallback موقعیت‌یابی، موقعیت‌های جایگزینی را در اختیار مرورگر قرار می‌دهند تا وقتی عناصر موقعیت‌یابی‌شده شروع به سرریز شدن می‌کنند، آن موقعیت‌ها را امتحان کند و عنصر را درون صفحه نگه دارد. پنهان‌سازی شرطی به شما امکان می‌دهد شرایطی را مشخص کنید که تحت آن لنگر یا یک عنصر موقعیت‌یابی‌شده پنهان شود.

> [!NOTE]
> برای اطلاعات در مورد اصول پایهٔ موقعیت‌یابی لنگر CSS، به [استفاده از موقعیت‌یابی لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using) مراجعه کنید.

## خلاصهٔ ویژگی

اگر یک tooltip به گوشهٔ بالا-راست یک عنصر UI چسبیده باشد، وقتی کاربر محتوا را اسکرول می‌کند تا آن عنصر UI در گوشهٔ بالا-راست viewport قرار گیرد، tooltip آن عنصر از صفحه خارج می‌شود. موقعیت‌یابی لنگر CSS چنین مشکلاتی را حل می‌کند. ویژگی {{cssxref("position-try-fallbacks")}} ماژول، یک یا چند گزینهٔ fallback موقعیت‌یابی جایگزین را مشخص می‌کند تا مرورگر برای جلوگیری از سرریز شدن عنصر موقعیت‌یابی‌شده آن‌ها را امتحان کند.

گزینه‌های fallback موقعیت‌یابی را می‌توان به روش‌های زیر مشخص کرد:

- [گزینه‌های fallback از پیش‌تعریف‌شده](#گزینه‌های-fallback-از-پیش‌تعریف‌شده)
- [مقادیر `position-area`](#استفاده-از-گزینه‌های-fallback-position-area)
- [گزینه‌های سفارشی](#گزینه‌های-سفارشی-fallback) که با استفاده از at-rule {{cssxref("@position-try")}} تعریف می‌شوند.

علاوه بر این، ویژگی {{cssxref("position-try-order")}} به شما امکان می‌دهد گزینه‌های مختلفی را مشخص کنید که نتیجهٔ آن تنظیم یک گزینهٔ موقعیت‌یابی در دسترس به جای موقعیت‌یابی اولیهٔ عنصر است. مثلاً ممکن است بخواهید عنصر را ابتدا در فضایی نمایش دهید که ارتفاع یا عرض بیشتری در دسترس دارد.

ویژگی کوتاه‌نویس {{cssxref("position-try")}} می‌تواند مقادیر `position-try-order` و `position-try-fallbacks` را در یک اعلامیه واحد مشخص کند.

در برخی شرایط، محتوای موقعیت‌یابی‌شده با لنگر اگر خود لنگر خارج از صفحه باشد معنی ندارد، یا برعکس. مثلاً ممکن است یک لنگر حاوی سؤال مسابقه داشته باشید و پاسخ‌ها در عناصر موقعیت‌یابی‌شدهٔ مرتبط قرار داشته باشند و بخواهید هر دو را با هم یا هیچ‌کدام را نشان دهید. این کار با پنهان‌سازی شرطی انجام می‌شود که توسط ویژگی {{cssxref("position-visibility")}} مدیریت می‌شود. این ویژگی مقادیر مختلفی را می‌پذیرد که شرایطی را تعریف می‌کنند که تحت آن عناصر سرریز شده پنهان می‌شوند.

## گزینه‌های fallback از پیش‌تعریف‌شده

مقادیر گزینه‌های fallback از پیش‌تعریف‌شدهٔ ویژگی `position-try-fallbacks` (که در spec به عنوان [`<try-tactic>`](/en-US/docs/Web/CSS/Reference/Properties/position-try-fallbacks#try-tactic) تعریف شده‌اند) موقعیت عنصر موقعیت‌یابی‌شده با لنگر را در یک یا هر دو محور «برعکس» می‌کنند (flip) اگر عنصر در غیر این صورت سرریز می‌کرد.

عنصر را می‌توان طوری تنظیم کرد که در امتداد محور بلوکی (block axis) با مقدار `flip-block`، در امتداد محور درون‌خطی (inline axis) با مقدار `flip-inline`، یا به‌صورت مورب روی خطی فرضی که از گوشه‌ای از anchor به مرکز آن و سپس به گوشهٔ مقابل کشیده می‌شود با مقدار `flip-start` قرینه شود. این سه مقدار عنصر را قرینه می‌کنند؛ دو مقدار اول موقعیت آن را به سمت مقابل منعکس می‌کنند و `flip-start` آن را به سمت مجاور. برای مثال، اگر عنصری که `10px` بالای anchor قرار گرفته شروع به سرریز شدن از بالای anchor کند، مقدار `flip-block` عنصر را طوری قرینه می‌کند که `10px` زیر anchor قرار گیرد.

در این مثال، دو عنصر `<div>` قرار داده‌ایم. عنصر اول به‌عنوان anchor عمل می‌کند و عنصر دوم نسبت به anchor موقعیت‌گذاری می‌شود:

```html
<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>
```

ما عنصر `<body>` را طوری استایل می‌دهیم که از viewport بزرگ‌تر باشد تا بتوانیم anchor و عنصر موقعیت‌گذاری‌شده را در viewport هم به‌صورت افقی و هم عمودی اسکرول کنیم:

```css
body {
  width: 1500px;
  height: 500px;
}
```

برای نمایش بهتر، anchor را به‌صورت absolute موقعیت‌گذاری می‌کنیم تا نزدیک مرکز نمایش اولیهٔ `<body>` قرار گیرد:

```css hidden
.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
  position: absolute;
  top: 100px;
  left: 45%;
}
```

به عنصر موقعیت‌گذاری‌شده نسبت به anchor، موقعیت‌گیری fixed داده می‌شود و با استفاده از `position-area` به گوشهٔ بالا-چپ anchor متصل می‌شود. به این عنصر `position-try-fallbacks: flip-block, flip-inline;` داده می‌شود تا گزینه‌های fallback برای جابه‌جایی آن فراهم شود و وقتی anchor به لبهٔ viewport نزدیک می‌شود، از سرریز شدن عنصر جلوگیری شود.

```css hidden
.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  position-area: top left;
  position-try-fallbacks: flip-block, flip-inline;
}
```

> [!NOTE]
> وقتی چند گزینهٔ position try fallback مشخص شده باشد، با کاما از هم جدا می‌شوند و به‌ترتیب ذکرشده امتحان می‌شوند.

دمو را اسکرول کنید تا anchor به لبه‌ها نزدیک شود:

- anchor را به بالای viewport ببرید. عنصر موقعیت‌گذاری‌شده برای جلوگیری از سرریز، به پایین-چپ anchor قرینه می‌شود.
- anchor را به سمت چپ viewport ببرید. عنصر موقعیت‌گذاری‌شده برای جلوگیری از سرریز، به بالا-راست anchor قرینه می‌شود.

اگر anchor را به سمت گوشهٔ بالا-چپ viewport ببرید، متوجه یک مشکل می‌شوید: وقتی عنصر موقعیت‌گذاری‌شده در جهت بلوکی و درون‌خطی شروع به سرریز می‌کند، به حالت پیش‌فرض بالا-چپ برمی‌گردد و در هر دو جهت سرریز می‌کند، که مطلوب ما نیست.

این اتفاق به این دلیل رخ می‌دهد که ما فقط گزینه‌های `flip-block` _یا_ `flip-inline` را در اختیار مرورگر قرار داده‌ایم و گزینهٔ امتحان کردن هر دو را هم‌زمان به آن نداده‌ایم. مرورگر گزینه‌های fallback را امتحان می‌کند و به دنبال گزینه‌ای می‌گردد که عنصر موقعیت‌گذاری‌شده را کاملاً داخل viewport یا containing block رندر کند. اگر چنین گزینه‌ای پیدا نکند، عنصر را در همان موقعیت رندر اولیه‌اش بدون اعمال هیچ گزینهٔ fallback رندر می‌کند.

بخش بعدی نحوهٔ رفع این مشکل را نشان می‌دهد.

می‌توان چندین [گزینه fallback از پیش‌تعریف‌شده](#predefined_fallback_options) یا [گزینه fallback دلخواه](#custom_fallback_options) را به‌صورت یک مقدار حاوی space-separated در لیست کاما-جدا `position-try-fallbacks` قرار داد. وقتی مرورگر این گزینه‌های fallback را امتحان می‌کند، اثر هرکدام را با هم ترکیب می‌کند و یک گزینه fallback واحد می‌سازد.

برای رفع مشکلی که در دموی قبلی داشتیم، از یک گزینه fallback ترکیبی استفاده می‌کنیم. HTML و CSS این دمو مثل قبل است، فقط به‌جز استایل‌های موقعیت‌دهی infobox. در اینجا یک گزینه fallback سوم به نام `flip-block flip-inline` اضافه شده است:

```html hidden
<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>
```

```css hidden
body {
  width: 1500px;
  height: 500px;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
  position: absolute;
  top: 100px;
  left: 45%;
}

.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css-nolint
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  position-area: top left;
  position-try-fallbacks:
    flip-block,
    flip-inline,
    flip-block flip-inline;
}
```

یعنی مرورگر اول `flip-block` و سپس `flip-inline` را امتحان می‌کند تا از سرریز جلوگیری کند. اگر هر دو fallback شکست خوردند، ترکیب آن‌ها را امتحان می‌کند: یعنی هم‌زمان موقعیت عنصر را در جهت block _و_ inline برعکس می‌کند. حالا وقتی anchor را به سمت لبه‌های بالا و چپ viewport ببرید، عنصر موقعیت‌یافته به سمت پایین-راست برمی‌گردد.

## استفاده از گزینه‌های fallback `position-area`

گزینه‌های fallback از پیش‌تعریف‌شده `<try-tactic>` مفیدند اما محدود هستند، چون فقط می‌توانند جای عنصر موقعیت‌یافته را در محورها برعکس کنند. اگر بخواهید عنصری که در بالا-چپ anchor قرار گرفته، وقتی شروع به سرریز کرد به زیر anchor منتقل شود، چه؟

برای این کار می‌توانید یک مقدار `position-area` را به‌عنوان گزینه fallback در لیست `position-try-fallbacks` قرار دهید. این کار به‌طور خودکار یک گزینه fallback بر اساس آن position area می‌سازد. در واقع این یک میانبر برای ایجاد یک [گزینه موقعیت دلخواه](#custom_fallback_options) است که فقط همان مقدار `position-area` را دارد.

مثال زیر استفاده از گزینه‌های fallback `position-area` را نشان می‌دهد. HTML و CSS مثل قبل است، فقط به‌جز موقعیت‌دهی infobox. در اینجا گزینه‌های fallback ما مقادیر `position-area` هستند: `top`, `top-right`, `right`, `bottom-right`, `bottom`, `bottom-left` و `left`. عنصر موقعیت‌یافته فارغ از اینکه anchor به کدام لبه viewport نزدیک شود، به‌خوبی جای‌گیری می‌کند. این روش جزئی‌تر و انعطاف‌پذیرتر از مقادیر از پیش‌تعریف‌شده است.

```html hidden
<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>
```

```css hidden
body {
  width: 1500px;
  height: 500px;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
  position: absolute;
  top: 100px;
  left: 45%;
}

.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css-nolint
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  position-area: top left;
  position-try-fallbacks:
    top, top right, right,
    bottom right, bottom,
    bottom left, left;
}
```

> [!NOTE]
> امکان اضافه کردن گزینه‌های `position-area` برای try fallback در قالب یک گزینه position ترکیبی که با فاصله جدا شده‌اند در فهرست position-try fallback وجود ندارد.

صفحه را اسکرول کنید و اثر این گزینه‌های position-try fallback را وقتی anchor به لبه viewport نزدیک می‌شود مشاهده کنید.

## گزینه‌های fallback سفارشی

برای استفاده از گزینه‌های position fallback سفارشی که از طریق سازوکارهای بالا در دسترس نیستند، می‌توانید با at-rule@position-try گزینه‌های خودتان را بسازید. سینتکس آن به این شکل است:

```plain
@position-try --try-fallback-name {
  descriptor-list
}
```

`--try-fallback-name` یک نام تعریف‌شده توسط توسعه‌دهنده برای گزینه position try fallback است. این نام را می‌توانید در فهرست جداشده با کاما از گزینه‌های try fallback، درون مقدار ویژگی `position-try-fallbacks` مشخص کنید. اگر چند قاعده `@position-try` نام یکسانی داشته باشند، قاعده‌ای که در ترتیب سند آخر باشد بقیه را لغو می‌کند. از به‌کار بردن نام یکسان برای گزینه‌های try fallback و همچنین نام‌های anchor یا propertyهای سفارشی خودداری کنید؛ این کار at-rule را بی‌اعتبار نمی‌کند، اما درک CSS را بسیار دشوار می‌کند.

`descriptor-list` مقادیر propertyهای آن گزینه try fallback سفارشی را تعریف می‌کند؛ از جمله نحوه قرارگیری و اندازه‌گیری عنصر positioned و هر حاشیه‌ای. فهرست محدود descriptorهای مجاز شامل موارد زیر است:

- `position-area`
- [Inset properties](/en-US/docs/Glossary/Inset_properties)
- ویژگی‌های margin (مثل `margin-left`، `margin-block-start`)
- ویژگی‌های [self-alignment](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using#centering_on_the_anchor_using_anchor-center)
- ویژگی‌های اندازه (مثل `width`، `block-size` و ...)
- `position-anchor`

مقادیری که در at-rule قرار می‌دهید، در صورتی که گزینه custom-try fallback نام‌برده اعمال شود، روی عنصر positioned اعمال می‌شوند. اگر قبلاً هر یک از این propertyها روی عنصر positioned تنظیم شده باشند، مقادیرشان با مقادیر descriptor جایگزین می‌شوند. اگر کاربر صفحه را اسکرول کند و در نتیجه گزینه try fallback دیگری یا هیچ‌کدام اعمال نشود، مقادیر مربوط به گزینه try fallback قبلی از بین می‌روند.

در این مثال، چند گزینه try fallback سفارشی را تعریف و استفاده می‌کنیم. از همان HTML و CSS پایه که در مثال‌های قبلی استفاده کردیم بهره می‌بریم.

ابتدا چهار گزینه try fallback سفارشی را با استفاده از `@position-try` تعریف می‌کنیم:

```html hidden
<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>
```

```css hidden
body {
  width: 1500px;
  height: 500px;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
  position: absolute;
  top: 100px;
  left: 45%;
}

.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
@position-try --custom-left {
  position-area: left;
  width: 100px;
  margin-right: 10px;
}

@position-try --custom-bottom {
  position-area: bottom;
  margin-top: 10px;
}

@position-try --custom-right {
  position-area: right;
  width: 100px;
  margin-left: 10px;
}

@position-try --custom-bottom-right {
  position-area: bottom right;
  margin: 10px 0 0 10px;
}
```

پس از ایجاد گزینه‌های try fallback سفارشی، می‌توانیم با ارجاع به نامشان آن‌ها را در فهرست position قرار دهیم:

```css
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  position-area: top;
  width: 200px;
  margin-bottom: 10px;
  position-try-fallbacks:
    --custom-left, --custom-bottom, --custom-right, --custom-bottom-right;
}
```

توجه داشته باشید که موقعیت پیش‌فرض ما با `position-area: top` تعریف شده است. وقتی infobox در هیچ جهتی از صفحه سرریز نمی‌کند، در بالای anchor قرار می‌گیرد و گزینه‌های fallback موقعیت که در ویژگی `position-try-fallbacks` تنظیم شده‌اند نادیده گرفته می‌شوند. همچنین به خاطر داشته باشید که infobox دارای عرض ثابت و margin پایین است. این مقادیر با اعمال هر یک از گزینه‌های position-try fallback تغییر می‌کنند.

اگر infobox شروع به سرریز شدن کند، مرورگر گزینه‌های موقعیت ذکر شده در ویژگی `position-try-fallbacks` را امتحان می‌کند:

- مرورگر ابتدا گزینه fallback `--custom-left` را امتحان می‌کند. این کار infobox را به سمت چپ anchor می‌برد، margin را متناسب با آن تنظیم می‌کند و همچنین عرض متفاوتی به infobox می‌دهد.
- سپس مرورگر موقعیت `--custom-bottom` را امتحان می‌کند. این موقعیت infobox را به پایین anchor می‌برد و یک margin مناسب تنظیم می‌کند. از آنجا که این گزینه شامل توصیف‌گر (descriptor) `width` نیست، infobox به عرض پیش‌فرض خود یعنی `200px` که توسط ویژگی `width` تنظیم شده بازمی‌گردد.
- مرورگر بعد از آن موقعیت `--custom-right` را امتحان می‌کند. این گزینه تقریباً مشابه `--custom-left` عمل می‌کند، با همین مقدار توصیف‌گر `width`، اما مقادیر `position-area` و `margin` به صورت آینه‌ای تنظیم می‌شوند تا infobox به‌درستی در سمت راست قرار گیرد.
- اگر هیچ‌کدام از fallbackهای قبلی نتوانند جلوی سرریز شدن عنصر موقعیت‌یافته را بگیرند، مرورگر به عنوان آخرین راه‌حل موقعیت `--custom-bottom-right` را امتحان می‌کند. این گزینه تقریباً مانند سایر گزینه‌های fallback عمل می‌کند، اما عنصر را در پایین-راست anchor قرار می‌دهد.

اگر هیچ‌کدام از fallbackها نتوانند جلوی سرریز شدن عنصر موقعیت‌یافته را بگیرند، موقعیت به مقدار اولیه `position-area: top;` بازمی‌گردد.

> [!NOTE]
> وقتی یک گزینه position-try fallback اعمال می‌شود، مقادیر آن، مقادیر پیش‌فرض تنظیم‌شده روی عنصر موقعیت‌یافته را بازنویسی (override) می‌کند. به عنوان مثال، عرض پیش‌فرض تنظیم‌شده روی عنصر `200px` است، اما وقتی گزینه fallback `--custom-right` اعمال می‌شود، عرض آن به `100px` تنظیم می‌شود.

برای دیدن تأثیر این گزینه‌های position-try fallback وقتی anchor به لبه viewport نزدیک می‌شود، صفحه را اسکرول کنید.

## استایل‌دهی به عناصر anchor-positioned بر اساس fallback فعال

مشکلی که قابلیت بالا حل نمی‌کند، به‌روزرسانی استایل یک عنصر anchor-positioned متناسب با گزینه‌های مختلف fallback است. برای مثال، معمول است که یک فلش کوچک روی tooltip قرار می‌گیرد که به عنصر anchor مرتبط با آن اشاره می‌کند و با واضح‌تر کردن ارتباط بصری، تجربه کاربری (UX) را بهبود می‌بخشد. وقتی tooltip به موقعیت دیگری منتقل می‌شود، باید موقعیت و جهت فلش را تغییر دهید، وگرنه ظاهر آن درست نخواهد بود.

برای حل این مشکل می‌توانید از anchored container queries استفاده کنید. این قابلیت، عملکرد [CSS container queries](/en-US/docs/Web/CSS/Guides/Containment/Container_queries) را گسترش می‌دهد تا بتوانید تشخیص دهید چه زمانی یک گزینه fallback خاص روی یک عنصر anchor-positioned اعمال شده است و در نتیجه CSS را روی فرزندان آن اعمال کنید. به طور مشخص، anchored container queries به دو ویژگی زیر تکیه دارند:

- مقدار `anchored` در ویژگی `container-type`: این مقدار را روی عنصر anchor-positioned اعمال کنید تا تشخیص اینکه چه زمانی گزینه‌های fallback مختلف روی آن اعمال می‌شوند، شروع شود.
- کلیدواژه `anchored` در at-rule `@container`: این کلیدواژه با یک جفت پرانتز دنبال می‌شود که داخل آن توصیف‌گر `fallback` قرار می‌گیرد. مقدار این توصیف‌گر یک مقدار `position-try-fallbacks` است.

برای مثال، فرض کنید یک المنت tooltip داریم که با استفاده از Anchor Positioning جایگذاری شده و به‌طور پیش‌فرض با مقدار `top` برای ویژگی `position-area` بالای anchor خود قرار می‌گیرد، اما برای `position-try-fallbacks` مقدار `flip-block` تنظیم شده است. این باعث می‌شود وقتی tooltip از بالای viewport سرریز کند، در جهت block به سمت پایین anchor بچرخد. اگر بخواهیم تشخیص دهیم که این fallback روی tooltip اعمال شده است، ابتدا باید `container-type: anchored` را روی آن تنظیم کنیم تا به یک anchored query container تبدیل شود.

```css
.tooltip {
  position: absolute;
  position-anchor: --myAnchor;
  position-area: top;
  position-try-fallbacks: flip-block;
  container-type: anchored;
}
```

با این کار، حالا می‌توانیم یک container query به این شکل بنویسیم:

```css
@container anchored(fallback: flip-block) {
  /* Descendant styles here */
}
```

آزمون query یعنی `anchored(fallback: flip-block)` زمانی `true` برمی‌گرداند که گزینه‌ی fallback با نام `flip-block` روی tooltip اعمال شده باشد؛ در این حالت، استایل‌های داخل بلوک `@container` اعمال می‌شوند. برای مثال، ممکن است بخواهید موقعیت و جهت آیکون فلش را طوری تغییر دهید که همچنان به سمت anchor اشاره کند، جهت گرادیان را عوض کنید، و غیره.

برای اطلاعات بیشتر درباره‌ی anchored container queries و چند مثال، به [Using anchored container queries](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Anchored_container_queries) مراجعه کنید.

## استفاده از `position-try-order`

ویژگی `position-try-order` تمرکز کمی متفاوت از بقیه‌ی قابلیت position try دارد، چرا که از گزینه‌های position try fallback در اولین نمایش المنت جایگذاری‌شده استفاده می‌کند، نه زمانی که در حال سرریز شدن است.

این ویژگی به شما اجازه می‌دهد مشخص کنید که المنت جایگذاری‌شده در ابتدا با استفاده از گزینه‌ی position try fallback نمایش داده شود که بیشترین عرض یا بیشترین ارتفاع را به containing block آن می‌دهد. این کار با تنظیم مقادیر `most-height`، `most-width`، `most-block-size` یا `most-inline-size` انجام می‌شود. همچنین می‌توانید با استفاده از مقدار `normal` اثر مقادیر قبلی `position-try-order` را حذف کنید.

اگر هیچ گزینه‌ی position-try fallback در دسترس نباشد که عرض/ارتفاع بیشتری نسبت به جایگذاری اولیه‌ی المنت فراهم کند، `position-try-order` هیچ اثری نخواهد داشت.

بیایید یک دمو ببینیم که اثر این ویژگی را نشان می‌دهد. HTML مانند مثال‌های قبلی است، با این تفاوت که یک `<form>` حاوی دکمه‌های رادیویی اضافه کرده‌ایم تا بتوانید مقادیر مختلف `position-try-order` را انتخاب کنید و اثر آن‌ها را ببینید.

```html hidden
<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>

<form>
  <fieldset>
    <legend>Choose a try order</legend>
    <div>
      <label for="radio-normal">normal</label>
      <input
        type="radio"
        id="radio-normal"
        name="position-try-order"
        value="normal"
        checked />
    </div>
    <div>
      <label for="radio-most-height">most-height</label>
      <input
        type="radio"
        id="radio-most-height"
        name="position-try-order"
        value="most-height" />
    </div>
  </fieldset>
</form>
```

ما یک گزینه‌ی try fallback سفارشی به نام `--custom-bottom` اضافه کرده‌ایم که المنت را زیر anchor قرار می‌دهد و یک margin اضافه می‌کند:

```css hidden
.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
  position: absolute;
  top: 100px;
  left: 45%;
}

.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
  text-align: center;
}

form {
  position: fixed;
  bottom: 2px;
  right: 2px;
}
```

```css
@position-try --custom-bottom {
  top: anchor(bottom);
  bottom: unset;
  margin-top: 10px;
}
```

ابتدا اینفو باکس را در بالای anchor قرار می‌دهیم و سپس گزینه‌ی تلاش مجدد سفارشی (try fallback) را به آن می‌دهیم:

```css
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  bottom: anchor(top);
  margin-bottom: 10px;
  justify-self: anchor-center;
  position-try-fallbacks: --custom-bottom;
}
```

در نهایت، جاوااسکریپتی اضافه می‌کنیم که یک event handler برای رویداد [`change`](/en-US/docs/Web/API/HTMLElement/change_event) روی دکمه‌های رادیویی تنظیم می‌کند. وقتی یک دکمه‌ی رادیویی انتخاب شود، مقدار آن روی پراپرتی `position-try-order` اینفو باکس اعمال می‌شود.

```js
const infobox = document.querySelector(".infobox");
const radios = document.querySelectorAll('[name="position-try-order"]');

for (const radio of radios) {
  radio.addEventListener("change", setTryOrder);
}

function setTryOrder(e) {
  const tryOrder = e.target.value;
  infobox.style.positionTryOrder = tryOrder;
}
```

گزینه‌ی ترتیب `most-height` را انتخاب کنید. این کار باعث اعمال گزینه‌ی position try fallback یعنی `--custom-bottom` می‌شود که عنصر را زیر anchor قرار می‌دهد. این اتفاق به این دلیل رخ می‌دهد که فضای بیشتری زیر anchor نسبت به بالای آن وجود دارد.

## پنهان‌سازی شرطی عناصر دارای موقعیت anchor

در برخی موقعیت‌ها ممکن است بخواهید یک عنصر دارای موقعیت anchor را پنهان کنید. برای مثال، اگر عنصر anchor به دلیل نزدیکی بیش از حد به لبه‌ی viewport بریده شود، شاید بخواهید عنصر مرتبط با آن را به‌طور کامل پنهان کنید. پراپرتی `position-visibility` به شما امکان می‌دهد شرایط مخفی شدن عناصر دارای موقعیت را مشخص کنید.

به‌طور پیش‌فرض، عنصر دارای موقعیت با مقدار `always` نمایش داده می‌شود. مقدار `no-overflow` اگر عنصر دارای موقعیت شروع به سرریز شدن از عنصر والد یا viewport کند، آن را **strongly hide** (مخفی‌سازی قوی) خواهد کرد.

از طرف دیگر، مقدار `anchors-visible` عنصر دارای موقعیت را strongly hide می‌کند اگر anchor(های) مرتبط با آن _کاملاً_ پنهان باشند؛ چه به دلیل سرریز شدن از عنصر والد (یا viewport) و چه در صورت پوشیده شدن توسط عناصر دیگر. اگر هر بخشی از anchor(ها) همچنان قابل مشاهده باشد، عنصر دارای موقعیت قابل مشاهده خواهد بود.

یک عنصر strongly hidden طوری رفتار می‌کند که گویی روی خود و عناصر فرزندش مقدار `visibility: hidden` تنظیم شده است، صرف‌نظر از اینکه مقدار واقعی `visibility` آن‌ها چه باشد.

بیایید این پراپرتی را در عمل ببینیم.

این مثال از همان HTML و CSS مثال‌های قبلی استفاده می‌کند، با این تفاوت که اینفو باکس به لبه‌ی پایینی anchor متصل شده است. به اینفو باکس مقدار `position-visibility: no-overflow;` داده شده است تا وقتی به سمت بالا اسکرول می‌شود و شروع به سرریز شدن از viewport می‌کند، به‌طور کامل پنهان شود.

```html hidden
<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique.
</p>

<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

```css hidden
.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
}
```

```css
body {
  width: 50%;
  margin: 0 auto;
}
```

```css hidden
.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  margin-bottom: 5px;
  position-area: top span-all;
  position-visibility: no-overflow;
}
```

صفحه را به پایین اسکرول کنید و توجه کنید که عنصر موقعیت‌یافته (positioned element) به محض رسیدن به بالای viewport پنهان می‌شود:

## جستارهای وابسته

- [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) module
- [Using CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using)
- [Learn: CSS positioning](/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning)
- [CSS logical properties and values](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values) module
- [Learn: Sizing items in CSS](/en-US/docs/Learn_web_development/Core/Styling_basics/Sizing)