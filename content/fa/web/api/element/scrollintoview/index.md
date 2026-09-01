---
title: "Element: scrollIntoView() method"
short-title: scrollIntoView()
slug: Web/API/Element/scrollIntoView
page-type: web-api-instance-method
browser-compat: api.Element.scrollIntoView
---

{{APIRef("DOM")}}

متد **`scrollIntoView()`** از رابط {{domxref("Element")}}، کانتینرهای ancestor المان را طوری اسکرول می‌کند که المانی که `scrollIntoView()` روی آن فراخوانی شده، برای کاربر قابل مشاهده باشد.

## Syntax

```js-nolint
scrollIntoView()
scrollIntoView(alignToTop)
scrollIntoView(options)
```

### پارامترها

- `alignToTop` {{optional_inline}}
  - : یک مقدار بولی:
    - اگر `true` باشد، بالای المان با بالای ناحیه قابل مشاهده ancestor قابل اسکرول هم‌تراز می‌شود. معادل `scrollIntoViewOptions: {block: "start", inline: "nearest"}` است. این مقدار پیش‌فرض است.
    - اگر `false` باشد، پایین المان با پایین ناحیه قابل مشاهده ancestor قابل اسکرول هم‌تراز می‌شود. معادل `scrollIntoViewOptions: {block: "end", inline: "nearest"}` است.

- `options` {{optional_inline}}
  - : یک شی با ویژگی‌های زیر:
    - `behavior` {{optional_inline}}
      - : تعیین می‌کند که اسکرول فوری باشد یا به صورت روان متحرک شود. این گزینه یک رشته است که باید یکی از مقادیر زیر را بگیرد:
        - `smooth`: اسکرول به صورت روان متحرک می‌شود.
        - `instant`: اسکرول به صورت فوری و در یک پرش انجام می‌شود.
        - `auto`: رفتار اسکرول توسط مقدار محاسبه‌شده ویژگی CSS {{cssxref("scroll-behavior")}} روی المان تعیین می‌شود.

        اگر حذف شود، `behavior` به طور پیش‌فرض `auto` است.

    - `block` {{optional_inline}}
      - : تراز عمودی المان را درون کانتینر ancestor قابل اسکرول تعریف می‌کند. مقدار آن می‌تواند یکی از موارد زیر باشد:
        - `start`: لبه بالایی المان را با بالای کانتینر قابل اسکرول هم‌تراز می‌کند و باعث می‌شود المان در ابتدای ناحیه قابل مشاهده به صورت عمودی ظاهر شود.
        - `center`: المان را به صورت عمودی در مرکز کانتینر قابل اسکرول هم‌تراز می‌کند و آن را در وسط ناحیه قابل مشاهده قرار می‌دهد.
        - `end`: لبه پایینی المان را با پایین کانتینر قابل اسکرول هم‌تراز می‌کند و المان را در انتهای ناحیه قابل مشاهده به صورت عمودی قرار می‌دهد.
        - `nearest`: تا حد امکان کم اسکرول می‌کند تا المان قابل مشاهده شود. اگر المان به لبه بالایی کانتینر قابل اسکرول نزدیک‌تر باشد، با بالا هم‌تراز می‌شود؛ اگر به لبه پایینی نزدیک‌تر باشد، با پایین هم‌تراز می‌شود. اگر المان از قبل قابل مشاهده است، هیچ اسکرولی انجام نمی‌شود.

        پیش‌فرض `start` است.

    - `container` {{optional_inline}}
      - : کانتینر ancestor قابل اسکرول را تعریف می‌کند. مقدار آن می‌تواند یکی از موارد زیر باشد:
        - `all`: همه کانتینرهای قابل اسکرول تحت تأثیر قرار می‌گیرند (شامل viewport).
        - `nearest`: فقط نزدیک‌ترین کانتینر قابل اسکرول تحت تأثیر اسکرول قرار می‌گیرد.

        پیش‌فرض `all` است.

    - `inline` {{optional_inline}}
      - : تراز افقی المان را درون کانتینر ancestor قابل اسکرول تعریف می‌کند. مقدار آن می‌تواند یکی از موارد زیر باشد:
        - `start`: لبه چپ المان را با چپ کانتینر قابل اسکرول هم‌تراز می‌کند و باعث می‌شود المان در ابتدای ناحیه قابل مشاهده به صورت افقی ظاهر شود.
        - `center`: المان را به صورت افقی در مرکز کانتینر قابل اسکرول هم‌تراز می‌کند و آن را در وسط ناحیه قابل مشاهده قرار می‌دهد.
        - `end`: لبه راست المان را با راست کانتینر قابل اسکرول هم‌تراز می‌کند و المان را در انتهای ناحیه قابل مشاهده به صورت افقی قرار می‌دهد.
        - `nearest`: تا حد امکان کم اسکرول می‌کند تا المان قابل مشاهده شود. اگر المان به لبه چپ کانتینر قابل اسکرول نزدیک‌تر باشد، با چپ هم‌تراز می‌شود؛ اگر به لبه راست نزدیک‌تر باشد، با راست هم‌تراز می‌شود. اگر المان از قبل قابل مشاهده است، هیچ اسکرولی انجام نمی‌شود.

        پیش‌فرض `nearest` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شی حاوی ویژگی زیر fulfilled می‌شود:

- `interrupted`
  - : یک مقدار بولی که نشان می‌دهد عملیات اسکرول قطع شده است (`true`) یا خیر (`false`). چنین قطعی معمولاً زمانی اتفاق می‌افتد که یک اسکرول برنامه‌ای در حال انجام است و اسکرول برنامه‌ای دیگری روی همان المان قبل از اتمام اولین شروع می‌شود.

## مثال‌ها

### استفاده پایه

```js
const element = document.getElementById("box");

element.scrollIntoView();
element.scrollIntoView(false);
element.scrollIntoView({ block: "end" });
element.scrollIntoView({ behavior: "smooth", block: "end", inline: "nearest" });
```

### کنترل تراز بالا/پایین

به طور پیش‌فرض، المان با لبه بالا (یا پایین) ancestor قابل اسکرول هم‌تراز می‌شود. برای تعریف فاصله سفارشی، از {{cssxref("scroll-margin-top")}} یا {{cssxref("scroll-margin-bottom")}} استفاده کنید. این کار معمولاً زمانی مفید است که یک هدر ثابت در صفحه وجود دارد.

#### HTML

```html live-sample___scroll-with-padding
<body>
  <header class="navbar">Navbar</header>
  <main class="content">
    <button id="go-to-bottom">Go to bottom</button>
    <button id="go-to-top">Go to top</button>
  </main>
</body>
```

#### CSS

```css live-sample___scroll-with-padding
.navbar {
  height: 50px;
  position: sticky;
  top: 0;
  border-bottom: 1.5px solid black;
  display: flex;
  justify-content: center;
  align-items: center;
}
.content {
  height: 2000px;
  position: relative;
}
#go-to-bottom {
  position: absolute;
  top: 10px;
  /* بدون این، دکمه با بالای صفحه هم‌تراز می‌شود
  به جای پایین نوار ناوبری هنگام اسکرول */
  scroll-margin-top: 60px;
}
#go-to-top {
  position: absolute;
  bottom: 10px;
  scroll-margin-bottom: 0;
}
```

#### JavaScript

```js live-sample___scroll-with-padding
const goToTop = document.getElementById("go-to-top");
const goToBottom = document.getElementById("go-to-bottom");
goToBottom.addEventListener("click", () => {
  goToTop.scrollIntoView({ behavior: "instant", block: "end" });
});
goToTop.addEventListener("click", () => {
  goToBottom.scrollIntoView({ behavior: "instant", block: "start" });
});
```

#### نتیجه

{{EmbedLiveSample("scroll-with-padding", "700", "300")}}

### پاسخ به پایان اسکرول

[دموی متدهای المان](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) ما ([مشاهده کد منبع](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods)) نشان می‌دهد که چگونه می‌توان از مقدار بازگشتی promise مربوط به `scrollIntoView()` برای پاسخ به پایان یک عملیات اسکرول استفاده کرد. این تکنیک بیشتر در مواردی مفید است که اسکرول به صورت روان در طول زمان اتفاق می‌افتد (با تنظیم گزینه [`behavior`](#behavior) روی `smooth`، یا با تنظیم ویژگی {{cssxref("scroll-behavior")}} المان اسکرول شونده روی `smooth`).

#### HTML

HTML ما شامل یک عنصر {{htmlelement("section")}} است که حاوی چندین پاراگراف محتوا و یک نوار ابزار {{htmlelement("div")}} شامل دکمه‌های {{htmlelement("button")}} است که عملیات اسکرول مختلفی را روی `<section>` فعال می‌کنند. آخرین پاراگراف دارای `id` برابر `end` است.

```html
<div>
  <button class="scroll">scroll() to 1000</button>
  <button class="scroll-to">scrollTo() top</button>
  <button class="scroll-by">scrollBy() 200</button>
  <button class="scroll-into-view">Scroll last &lt;p&gt; into view</button>
</div>

<section>
  ...

  <p id="end">...</p>
</section>
```

#### CSS

ما به عنصر `<section>` یک {{cssxref("height")}} ثابت و یک مقدار `overflow-y` برابر `scroll` می‌دهیم تا به صورت عمودی اسکرول شود، و ویژگی {{cssxref("scroll-behavior")}} آن را روی `smooth` تنظیم می‌کنیم تا هر عملیات اسکرول به جای فوری، به صورت روان در طول زمان متحرک شود.

```css
section {
  border: 1px solid black;
  padding: 20px;
  margin-top: 60px;
  height: 500px;
  overflow-y: scroll;
  scroll-behavior: smooth;
}
```

همچنین دو انتخابگر کلاس ایجاد می‌کنیم؛ هنگامی که یک کلاس `fade-out` یا `fade-in` روی یک عنصر اعمال می‌شود، یک {{cssxref("animation")}} اعمال می‌شود تا به ترتیب به صورت روان محو یا ظاهر شود. همچنین بلوک‌های {{cssxref("@keyframes")}} را برای تعریف تغییرات {{cssxref("opacity")}} مورد نیاز برای آن انیمیشن‌ها تعریف می‌کنیم.

```css
.fade-out {
  animation: fade-out 0.3s linear both;
}

.fade-in {
  animation: fade-in 0.3s linear both;
}

@keyframes fade-out {
  from {
    opacity: 1;
  }

  to {
    opacity: 0;
  }
}

@keyframes fade-in {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
```

بقیه CSS برای اختصار نشان داده نشده است.

#### JavaScript

ما با دریافت ارجاع به دکمه‌ای که عملیات `scrollIntoView()` را اجرا می‌کند، نوار ابزار `<div>` و پاراگراف با `id` برابر `end` شروع می‌کنیم:

```js
const scrollIntoViewBtn = document.querySelector(".scroll-into-view");
const toolbar = document.querySelector("div");
const end = document.querySelector("#end");
```

سپس، تابعی به نام `isInterrupted()` تعریف می‌کنیم که برای پاسخ به پایان یک عملیات اسکرول طراحی شده است و یک مقدار بولی `interrupted` را به عنوان پارامتر می‌گیرد. این تابع یک پیام در کنسول ثبت می‌کند که پایان اسکرول را اعلام کرده و نشان می‌دهد که آیا عملیات قطع شده است (`interrupted` برابر `true`) یا خیر. علاوه بر این، اگر `interrupted` برابر `true` باشد، یک `alert()` فراخوانی می‌کند تا قطع شدن را به وضوح نشان دهد.

```js
function isInterrupted(interrupted) {
  console.log(`Scroll finished;${interrupted ? " " : " not "}interrupted`);
  if (interrupted) {
    alert("Scroll interrupted!");
  }
}
```

هنگامی که دکمه کلیک می‌شود، بلافاصله کلاس `fade-out` را به نوار ابزار اعمال می‌کنیم تا محو شود. سپس `scrollIntoView()` را روی پاراگراف end اجرا می‌کنیم تا `<section>` اسکرول کند تا پاراگراف end قابل مشاهده شود، و منتظر حل شدن promise آن می‌مانیم و `result` را در یک ثابت ذخیره می‌کنیم. هنگامی که promise حل شد، `isInterrupted()` را فراخوانی می‌کنیم تا گزارش دهد که عملیات اسکرول پایان یافته و آیا قطع شده است یا خیر. در نهایت، کلاس `fade-in` را به نوار ابزار اعمال می‌کنیم تا دوباره ظاهر شود.

```js
scrollIntoViewBtn.addEventListener("click", async () => {
  toolbar.className = "fade-out";
  const result = await end.scrollIntoView();
  isInterrupted(result.interrupted);
  toolbar.className = "fade-in";
});
```

کد غیرمرتبط با `scrollIntoView()` برای اختصار نشان داده نشده است.

#### نتیجه

روی دکمه‌ها کلیک کنید تا رفتار اسکرول را مشاهده کنید. توجه کنید که چگونه نوار ابزار هنگام فشار دادن دکمه محو می‌شود و پس از اتمام اسکرول روان دوباره ظاهر می‌شود. همچنین سعی کنید یک دکمه را فشار دهید و سپس به سرعت دکمه دیگری را قبل از اتمام اولین عملیات اسکرول فشار دهید. توجه کنید که در این موارد، اسکرول به عنوان قطع شده گزارش می‌شود.

{{EmbedGHLiveSample("dom-examples/scroll-promises/element-methods/", "100%", 620)}}

همچنین می‌توانید [دمو را در یک تب جداگانه بارگذاری کنید](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) و [کد منبع](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods) را مشاهده کنید.

#### نکته جانبی در مورد تشخیص ویژگی

اگر این مثال را در مرورگری اجرا کنید که از عملیات اسکرول بازگشت‌دهنده promise پشتیبانی نمی‌کند، عملیات اسکرول همچنان روان است، اما نوار ابزار پس از اتمام عملیات محو و دوباره ظاهر نمی‌شود. تشخیص ویژگی توسط تابعی به نام `supportsScrollPromises()` انجام می‌شود که یک عملیات اسکرول را اجرا کرده و بررسی می‌کند که آیا مقدار بازگشتی آن یک promise است:

```js
function supportsScrollPromises() {
  const test = section.scroll(0, 0);
  return test instanceof Promise;
}
```

برای مشاهده نحوه استفاده از تشخیص ویژگی، به [کد منبع](https://github.com/mdn/dom-examples/blob/main/scroll-promises/element-methods/index.js) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.scrollIntoViewIfNeeded()")}} {{non-standard_inline}}