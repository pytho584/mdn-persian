---
title: "Using anchored container queries"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Anchor_positioning/Anchored_container_queries"
translated_by: "n8n + AI"
---

[CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) شامل مکانیزم‌هایی برای ارائه‌ی گزینه‌های جایگزین (fallback options) است. این گزینه‌ها موقعیت‌های جایگزینی هستند که مرورگر می‌تواند برای قرار دادن یک عنصر موقعیت‌یافته نسبت به anchor خود امتحان کند تا اگر عنصر از viewport خارج شد، دوباره درون صفحه نمایش داده شود.

**Anchored container queries** کاربرد گزینه‌های جایگزین anchor positioning را با امکان اعمال استایل‌های متفاوت روی عنصر موقعیت‌یافته، بسته به اینکه کدام گزینه‌ی جایگزین اعمال شده، افزایش می‌دهد. این راهنما نحوه استفاده از anchored container queries را به همراه چند مثال نشان می‌دهد.

> [!NOTE]
> برای اطلاعات پایه‌ای درباره‌ی anchor positioning، به [Using CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using) مراجعه کنید.

## خلاصه‌ی ویژگی

هنگام قرار دادن یک tooltip نسبت به یک عنصر UI با استفاده از anchor positioning، مفید است که گزینه‌های جایگزین `position-try` را از طریق ویژگی {{cssxref("position-try-fallbacks")}} فراهم کنید. این گزینه‌ها تضمین می‌کنند که tooltip تا جای ممکن درون صفحه باقی بماند.

برای مثال، اگر tooltip به طور پیش‌فرض بالای عنصر UI که به آن anchor شده قرار گرفته باشد، و کاربر به سمت بالا اسکرول کند، می‌توانید با استفاده از fallbackها، tooltip را درست قبل از خارج شدن از صفحه، به زیر عنصر منتقل کنید.

اما یک مشکل باقی می‌ماند: به‌روزرسانی استایل element موقعیت‌یافته متناسب با گزینه‌های جایگزین مختلف. برای مثال، معمول است که یک فلش کوچک روی tooltip قرار داده شود که به عنصر anchor اشاره کند و ارتباط بصری را واضح‌تر کند. وقتی tooltip به موقعیت دیگری منتقل می‌شود، موقعیت و جهت فلش نیز باید تغییر کند، در غیر این صورت ظاهر نادرستی خواهد داشت.

برای حل این مشکل، می‌توانید از anchored container queries استفاده کنید. این ویژگی قابلیت‌های [CSS container queries](/en-US/docs/Web/CSS/Guides/Containment/Container_queries) را گسترش می‌دهد تا بتوانید تشخیص دهید که چه زمانی یک گزینه‌ی جایگزین خاص روی element موقعیت‌یافته اعمال شده است و بر اساس آن، استایل‌های فرزندان آن را تغییر دهید. به طور خاص، anchored container queries به دو ویژگی وابسته است:

- مقدار `anchored` در ویژگی {{cssxref("container-type")}}: این مقدار را روی element موقعیت‌یافته اعمال کنید تا شروع به تشخیص اعمال گزینه‌های جایگزین مختلف کند.
- تابع `anchored()` در at-rule {{cssxref("@container")}}: این تابع یک [descriptor به نام `fallback`](/en-US/docs/Web/CSS/Reference/At-rules/@container#fallback) به عنوان آرگومان دریافت می‌کند. مقدار این descriptor یک مقدار از `position-try-fallbacks` است.

برای مثال، فرض کنید یک tooltip داریم که به طور پیش‌فرض با استفاده از مقدار `top` در ویژگی {{cssxref("position-area")}} بالای anchor خود قرار گرفته است، اما یک مقدار `flip-block` برای {{cssxref("position-try-fallbacks")}} مشخص شده است. این باعث می‌شود که tooltip در جهت بلاک به پایین anchor خود بچرخد (flip) وقتی از بالای viewport خارج می‌شود. اگر بخواهیم تشخیص دهیم که چه زمانی fallback روی tooltip اعمال شده است، ابتدا باید `container-type: anchored` را روی آن تنظیم کنیم تا به یک container query anchored تبدیل شود.

```css
.tooltip {
  position: absolute;
  position-anchor: --my-anchor;
  position-area: top;
  position-try-fallbacks: flip-block;
  container-type: anchored;
}
```

با این کار، می‌توانیم یک container query به صورت زیر بنویسیم:

```css
@container anchored(fallback: flip-block) {
  /* استایل‌های فرزندان */
}
```

تست query — `anchored(fallback: flip-block)` — وقتی `true` برمی‌گرداند که گزینهٔ fallback با نام `flip-block` روی tooltip اعمال شده باشد؛ در این حالت استایل‌هایی که داخل بلوک `@container` نوشته شده‌اند، اعمال می‌شوند. برای مثال ممکن است بخواهید موقعیت و جهت یک فلش را تغییر دهید تا به جای رو به پایین، رو به بالا باشد، یا جهت یک گرادیان را عوض کنید.

> [!NOTE]
> به خاطر داشته باشید که مانند همهٔ container query ها، استایل‌های اعمال‌شده فقط می‌توانند روی فرزندان (descendants) کانتینر اثر بگذارند، نه روی خود کانتینر. بنابراین ممکن است لازم باشد برخی از استایل‌های عنصر موقعیت‌یافته را روی یک عنصر wrapper داخل آن اعمال کنید، نه روی خود عنصر؛ همان‌طور که در [مثال چندین fallback](#multiple_fallbacks_example) نشان داده شده است.

## مثال کاربرد پایه

در این مثال یک عنصر anchor داریم که یک infobox نسبت به آن موقعیت‌دهی شده است.
در ابتدا، infobox بالای anchor قرار می‌گیرد و یک فلش دارد که به سمت پایین و به سمت anchor نشانه گرفته است. ما یک position try fallback اضافه کرده‌ایم تا وقتی محتوا به اندازهٔ کافی به بالا اسکرول شود و infobox شروع به خارج شدن از بالای viewport کند، infobox به پایین anchor منتقل شود. علاوه بر این، از یک anchored container query استفاده می‌کنیم تا وقتی fallback فعال شد، استایل‌ها تغییر کنند و جهت فلش به سمت بالا عوض شود.

anchor و infobox با دو عنصر `<div>` نمایش داده می‌شوند که در زیر می‌بینید. در نمایش نهایی، این دو با محتوای متنی احاطه شده‌اند تا صفحه اسکرول شود، اما برای خلاصه‌بودن مطلب آن‌ها را مخفی کرده‌ایم:

```html
<div class="anchor">⚓︎</div>

<div class="infobox">Infobox</div>
```

```html hidden live-sample___basic-example
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<div class="anchor">⚓︎</div>

<div class="infobox">Infobox</div>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
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

در CSS، ابتدا عنصر `<div>` با کلاس `anchor` را با دادن یک `anchor-name` به مقدار `--my-anchor` به عنوان عنصر anchor مشخص می‌کنیم.

```css hidden live-sample___basic-example
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  width: 80%;
  max-width: 600px;
  margin: 0 auto;
}

p {
  font-size: 1.4em;
  line-height: 1.5;
}
```

```css
.anchor {
  font-size: 2em;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: blue;
  width: fit-content;
  padding: 5px 10px;
}

.infobox {
  color: white;
  background-color: black;
  font-size: 1.4em;
  padding: 10px;
  margin: 1rem;
  border-radius: 10px;
}

.infobox::before {
  color: black;
  font-size: 1rem;
  margin: 0;
  line-height: 0.5;
  left: 0;
  width: 100%;
  text-align: center;
}

@supports not (container-type: anchored) {
  body::before {
    content: "Your browser does not support anchored container queries.";
    background-color: wheat;
    display: block;
    text-align: center;
    padding: 1rem 0;
  }
}
```

```css live-sample___basic-example
.anchor {
  anchor-name: --my-anchor;
}
```

در مرحله بعد، به `infobox` که یک `<div>` است یک `position: fixed` و یک `position-anchor: --my-anchor` می‌دهیم تا آن را به عنصر anchor متصل کنیم. سپس به infobox یک `position-area: top` می‌دهیم تا بالای عنصر anchor قرار بگیرد و یک `position-try-fallbacks: bottom` مشخص می‌کنیم تا وقتی محتوا به سمت بالا اسکرول می‌شود و infobox از بالای viewport خارج می‌شود، به پایین anchor منتقل شود.

در نهایت، روی infobox مقدار `container-type: anchored` را تنظیم می‌کنیم تا به عنوان یک anchored query container شناخته شود. یعنی می‌توانیم با استفاده از at-ruleهای `@container` تشخیص دهیم که کدام `position-try-fallbacks` روی infobox فعال است و بر اساس آن استایل فرزندان آن را تغییر دهیم.

```css live-sample___basic-example
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  position-area: top;
  position-try-fallbacks: bottom;
  container-type: anchored;
}
```

حالا با استفاده از محتوای تولید شده روی pseudo-element `::before` یک فلش به infobox اضافه می‌کنیم. `content` را به یک آیکون فلش رو به پایین (▼) تنظیم می‌کنیم، آن را به صورت absolute position می‌کنیم و `top: 105%` قرار می‌دهیم تا در پایین infobox ظاهر شود (مقدار بیشتر از 100% باعث می‌شود از نظر بصری با فلش رو به بالای متناظر هماهنگ شود).

```css live-sample___basic-example
.infobox::before {
  content: "▼";
  position: absolute;
  top: 105%;
}
```

سپس anchored container query را اضافه می‌کنیم. یک at-rule `@container` با شرط `anchored(fallback: bottom)` تعریف می‌کنیم. یعنی وقتی fallback با موقعیت `bottom` روی infobox اعمال می‌شود، CSS داخل at-rule روی سند اعمال می‌شود. در داخل آن، استایل جایگزین برای pseudo-element `::before` تعریف می‌کنیم که آیکون فلش رو به پایین را با یک فلش رو به بالا (▲) عوض می‌کند و آن را در بالای infobox قرار می‌دهد.

```css live-sample___basic-example
@container anchored(fallback: bottom) {
  .infobox::before {
    content: "▲";
    bottom: 100%;
    top: auto;
  }
}
```

> [!NOTE]
> در این مثال CSS بیشتری برای استایل‌دهی پایه‌ای همه عناصر وجود دارد، اما فقط بخش‌های مربوط به anchored container queries را نشان داده‌ایم. برای دیدن کد کامل، دکمه «Play» را روی یکی از بلاک‌های کد یا نمایش زنده بزنید تا مثال در MDN Playground باز شود.

خروجی این مثال به صورت زیر است:

_نمایش زنده در اینجا قرار می‌گرفت (حذف شده)_

مثال را اسکرول کنید تا anchor به نزدیک بالای viewport برسد. توجه کنید که نه تنها infobox به پایین anchor منتقل می‌شود تا روی صفحه بماند، بلکه استایل آن نیز به‌روز می‌شود تا آیکون فلش برای موقعیت جدید infobox همچنان درست کار کند.

اگر anchor را دوباره به سمت پایین viewport اسکرول کنید، infobox دوباره به بالای آن برمی‌گردد. نیازی به تعیین مقدار اضافی `position-try-fallbacks: top` نیست، زیرا `position-area: top` موقعیت پیش‌فرض infobox است. اگر fallbackهای تعریف شده مانع از سرریز شدن عنصر positioned از viewport نشوند، مرورگر به موقعیت پیش‌فرض برمی‌گردد.

## مثال چندین fallback

این مثال چندین fallback از نوع `position-try` و همچنین anchored container queries را در عمل نشان می‌دهد. به‌علاوه، به این مسئله می‌پردازد که اگر بخواهید از anchored container queries برای اعمال استایل روی خودِ عنصرِ دارای موقعیت anchor استفاده کنید، نه روی فرزندان آن، چه باید کرد؛ با کمک یک عنصر wrapper اضافی. این مثال شامل کمی JavaScript هم هست که به شما اجازه می‌دهد عنصر anchor را با ماوس یا صفحه‌کلید روی صفحه جابه‌جا کنید و fallbackهای مختلف را ببینید.

HTML این مثال شامل دو عنصر `<div>` است که anchor و infobox را نشان می‌دهند. `<div>` با کلاس `anchor` یک attribute به نام [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) دارد تا بتوان با صفحه‌کلید آن را فوکوس کرد؛ و `<div>` با کلاس `infobox` یک `<div>` wrapper اضافی دارد که استایل‌های infobox روی آن اعمال می‌شود تا بتوانیم آن را با at-ruleهای `@container` استایل‌دهی کنیم.

```html live-sample___multiple-fallbacks
<div class="anchor" tabindex="0">⚓︎</div>

<div class="infobox">
  <div>Infobox</div>
</div>
```

استایل‌ها را با مشخص کردن `<div>` کلاس `anchor` به‌عنوان عنصر anchor شروع می‌کنیم؛ برای این کار دوباره یک `anchor-name` با مقدار `--my-anchor` به آن می‌دهیم. همچنین موقعیت آن را `position: absolute` می‌کنیم تا بتوانیم با تنظیم مقادیر مختلف ویژگی‌های `inset` از طریق JavaScript آن را جابه‌جا کنیم.

```css hidden live-sample___multiple-fallbacks
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
  height: 100%;
}

body {
  height: inherit;
}

p {
  font-size: 1.4em;
  line-height: 1.5;
}

.anchor {
  font-size: 2em;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: blue;
  width: fit-content;
  padding: 5px 10px;
}

@supports not (container-type: anchored) {
  body::before {
    content: "Your browser does not support anchored container queries.";
    background-color: wheat;
    display: block;
    text-align: center;
    padding: 1rem 0;
  }
}
```

```css live-sample___multiple-fallbacks
.anchor {
  anchor-name: --my-anchor;
  position: absolute;
}
```

سپس infobox را نسبت به anchor موقعیت‌دهی می‌کنیم؛ برای این کار آن را `position: absolute` می‌کنیم و `position-anchor` را برابر `--my-anchor` قرار می‌دهیم. این بار آن را در گوشهٔ بالا-چپ anchor با `position-area: top left` می‌گذاریم. سپس سه `position-try-fallbacks` تنظیم می‌کنیم: `flip-block`، `flip-inline` و `flip-block flip-inline`. این کار باعث می‌شود infobox در امتداد محور block، محور inline یا هر دو بچرخد تا وقتی anchor به لبه‌های مختلف viewport نزدیک می‌شود، همچنان روی صفحه بماند.

در نهایت، با تنظیم `container-type: anchored`، infobox را به یک anchored query container تبدیل می‌کنیم.

```css live-sample___multiple-fallbacks
.infobox {
  position: absolute;
  position-anchor: --my-anchor;
  position-area: top left;
  position-try-fallbacks:
    flip-block,
    flip-inline,
    flip-block flip-inline;
  container-type: anchored;
}
```

در این مرحله، استایل‌های بصری اصلی را که روی infobox اعمال می‌شود نشان می‌دهیم تا این نکته را روشن کنیم که در این مورد، این استایل‌ها را روی `<div>` wrapper داخل infobox تنظیم می‌کنیم، نه روی خود infobox. همان‌طور که اشاره شد، این کار را انجام می‌دهیم تا بتوانیم این استایل‌ها را از طریق anchored container queries تغییر دهیم. اگر این استایل‌ها مستقیماً روی infobox تنظیم می‌شدند، این امکان وجود نداشت؛ چون خود infobox همان anchored query container است.

قابل ذکرترین نکته این است که در اینجا یک مقدار `border-radius` تنظیم کرده‌ایم که تمام گوشه‌های infobox به‌جز گوشهٔ پایین-راست را گرد می‌کند. از آنجایی که infobox در گوشهٔ بالا-چپ anchor قرار گرفته است، این گوشه مانند یک پیکان عمل می‌کند و به سمت anchor اشاره می‌کند.

```css live-sample___multiple-fallbacks
.infobox div {
  color: white;
  background-color: black;
  font-size: 1.4em;
  padding: 10px;
  margin: 1px;

  border-radius: 10px 10px 0 10px;
}
```

در پایان، برای هر fallback از position-try که ممکن است روی infobox اعمال شود، یک container query لنگر‌اندازی‌شده با استفاده از قواعد @container تعریف می‌کنیم. در هر مورد، گوشه‌های گرد اعمال‌شده روی `<div>` پوشانندهٔ infobox را تغییر می‌دهیم تا نزدیک‌ترین گوشه به anchor همیشه گرد نباشد.

```css live-sample___multiple-fallbacks
@container anchored(fallback: flip-block) {
  .infobox div {
    border-radius: 10px 0 10px 10px;
  }
}

@container anchored(fallback: flip-inline) {
  .infobox div {
    border-radius: 10px 10px 10px 0;
  }
}

@container anchored(fallback: flip-block flip-inline) {
  .infobox div {
    border-radius: 0 10px 10px 10px;
  }
}
```

> [!NOTE]
> باز هم برای اختصار، بخش عمده‌ای از استایل‌دهی پایه و همچنین جاوااسکریپتی که کنترل‌های حرکت را فراهم می‌کند پنهان کرده‌ایم (این‌ها به آنچه می‌خواهیم در اینجا نشان دهیم مرتبط نیستند). برای مشاهدهٔ کد کامل، مثال را با فشردن دکمهٔ «Play» روی یکی از بلوک‌های کد یا در نمایش زنده در MDN Playground باز کنید.

```js hidden live-sample___multiple-fallbacks
const anchorDiv = document.querySelector(".anchor");

let xPos = 250;
let yPos = 120;

function setPos() {
  const maxX = document.body.clientWidth - anchorDiv.clientWidth - 25;
  const maxY = document.body.clientHeight - anchorDiv.clientHeight - 25;

  if (xPos < 25) {
    xPos = 25;
  }

  if (xPos > maxX) {
    xPos = maxX;
  }

  if (yPos < 25) {
    yPos = 25;
  }

  if (yPos > maxY) {
    yPos = maxY;
  }

  anchorDiv.style.left = `${xPos}px`;
  anchorDiv.style.top = `${yPos}px`;
}

setPos();

document.body.addEventListener("keydown", (e) => {
  if (e.key === "w") {
    yPos -= 25;
  } else if (e.key === "d") {
    xPos += 25;
  } else if (e.key === "s") {
    yPos += 25;
  } else if (e.key === "a") {
    xPos -= 25;
  }

  setPos();
});

document.body.addEventListener("click", (e) => {
  xPos = e.clientX;
  yPos = e.clientY;

  setPos();
});
```

این مثال به این شکل نمایش داده می‌شود:

سعی کنید عنصر anchor را در viewport جابه‌جا کنید با:

- کلیک کردن با ماوس (یا لمس صفحه اگر دستگاه شما لمسی است) در موقعیتی که می‌خواهید anchor به آنجا منتقل شود.
- استفاده از کلیدهای <kbd>W</kbd>، <kbd>A</kbd>، <kbd>S</kbd> و <kbd>D</kbd> برای حرکت anchor به ترتیب به بالا، چپ، پایین و راست.

وقتی عنصر anchor را به لبه‌های صفحه نزدیک می‌کنید، توجه کنید که infobox برای ماندن در صفحه به موقعیت‌های مختلفی دور آن منتقل می‌شود؛ همچنین `border-radius` اعمال‌شده روی infobox تغییر می‌کند به‌طوری که گوشهٔ غیرگرد همیشه به سمت anchor باشد. جابه‌جا کردن anchor در گوشه‌های مختلف، قطعاً جلوه‌های متفاوت را به شما نشان می‌دهد.

## See also

- [پرس‌وجوهای ظرف (Container Queries)](/en-US/docs/Web/CSS/Guides/Containment/Container_queries)
- [استفاده از پرس‌وجوهای اندازه و استایل ظرف](/en-US/docs/Web/CSS/Guides/Containment/Container_size_and_style_queries)
- [استفاده از پرس‌وجوهای وضعیت اسکرول ظرف](/en-US/docs/Web/CSS/Guides/Conditional_rules/Container_scroll-state_queries)
- ماژول [مکان‌دهی لنگر CSS](/en-US/docs/Web/CSS/Guides/Anchor_positioning)
- [یادگیری: مکان‌دهی CSS](/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning)