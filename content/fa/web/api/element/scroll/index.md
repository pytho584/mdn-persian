---
title: "Element: scroll() method"
---

---
title: "Element: scroll() method"
short-title: scroll()
slug: Web/API/Element/scroll
page-type: web-api-instance-method
browser-compat: api.Element.scroll
---

{{APIRef("CSSOM view API")}}

متد **`scroll()`** از رابط {{domxref("Element")}}، به مجموعه‌ای از مختصات مشخص درون یک عنصر معیّن اسکرول می‌کند.

## ساختار

```js-nolint
scroll(xCoord, yCoord)
scroll(options)
```

### پارامترها

- `xCoord`
  - : پیکسلی در امتداد محور افقی عنصر که می‌خواهید در گوشهٔ بالا-چپ نمایش داده شود.
- `yCoord`
  - : پیکسلی در امتداد محور عمودی عنصر که می‌خواهید در گوشهٔ بالا-چپ نمایش داده شود.
- `options`
  - : یک شیء (object) حاوی ویژگی‌های زیر:
    - `top` {{optional_inline}}
      - : تعداد پیکسل‌ها در امتداد محور Y را برای اسکرول پنجره یا عنصر مشخص می‌کند.
    - `left` {{optional_inline}}
      - : تعداد پیکسل‌ها در امتداد محور X را برای اسکرول پنجره یا عنصر مشخص می‌کند.
    - `behavior` {{optional_inline}}
      - : تعیین می‌کند که اسکرول آنی باشد یا به‌صورت نرم انیمیشن شود. این گزینه یک رشته (string) است که باید یکی از مقادیر زیر را بگیرد:
        - `smooth`: اسکرول به‌صورت نرم انیمیشن می‌شود.
        - `instant`: اسکرول به‌صورت آنی و در یک پرش انجام می‌شود.
        - `auto`: رفتار اسکرول بر اساس مقدار محاسبه‌شدهٔ ویژگی CSS {{cssxref("scroll-behavior")}} روی عنصر تعیین می‌شود.

        در صورت حذف، `behavior` به‌صورت پیش‌فرض روی `auto` تنظیم می‌شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء حاوی ویژگی زیر تکمیل (fulfill) می‌شود:

- `interrupted`
  - : یک مقدار بولی که نشان می‌دهد عملیات اسکرول قطع شده است (`true`) یا خیر (`false`). چنین قطعی معمولاً زمانی رخ می‌دهد که یک اسکرول برنامه‌نویسی‌شده در حال اجراست و اسکرول برنامه‌نویسی‌شدهٔ دیگری روی همان عنصر، پیش از پایان یافتن اسکرول اول آغاز می‌شود.

## مثال‌ها

### استفادهٔ پایه

```js
// Put the 1000th vertical pixel at the top of the element
element.scroll(0, 1000);
```

استفاده از `options`:

```js
element.scroll({
  top: 100,
  left: 100,
  behavior: "smooth",
});
```

### واکنش به پایان اسکرول

در [دموی متدهای عنصر](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) ([مشاهدهٔ کد منبع](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods)) نشان داده شده است که چگونه می‌توان از مقدار بازگشتیِ Promise در `scroll()` برای واکنش به پایان یک عملیات اسکرول استفاده کرد. این تکنیک عمدتاً در مواردی مفید است که اسکرول به‌مرور زمان و به‌صورت نرم انجام می‌شود (با تنظیم گزینهٔ [`behavior`](#behavior) روی `smooth` یا با تنظیم ویژگی {{cssxref("scroll-behavior")}} عنصر اسکرول‌شونده روی `smooth` حاصل می‌شود).

#### HTML

در HTML ما یک عنصر {{htmlelement("section")}} وجود دارد که حاوی چند پاراگراف محتوا است. همچنین یک نوار ابزار به شکل عنصر {{htmlelement("div")}} داریم که شامل چند عنصر {{htmlelement("button")}} است. این دکمه‌ها عملیات‌های اسکرول مختلفی را روی `<section>` فعال می‌کنند.

```html
<div>
  <button class="scroll">scroll() to 1000</button>
  <button class="scroll-to">scrollTo() top</button>
  <button class="scroll-by">scrollBy() 200</button>
  <button class="scroll-into-view">Scroll last &lt;p&gt; into view</button>
</div>

<section>...</section>
```

#### CSS

به عنصر `<section>` یک {{cssxref("height")}} ثابت و مقدار {{cssxref("overflow-y")}} برابر با `scroll` می‌دهیم تا به‌صورت عمودی اسکرول شود؛ ویژگی {{cssxref("scroll-behavior")}} آن را نیز روی `smooth` تنظیم می‌کنیم تا هر عملیات اسکرول به‌جای انجام آنی، به‌مرور زمان و به‌صورت نرم انیمیشن شود.

همچنین دو انتخابگر کلاس ایجاد می‌کنیم؛ زمانی که کلاس `fade-out` یا `fade-in` روی یک عنصر اعمال شود، یک {{cssxref("animation")}} روی آن اعمال می‌شود تا عنصر به‌ترتیب به‌صورت نرم محو یا ظاهر شود. همچنین بلوک‌های {{cssxref("@keyframes")}} را برای تعریف تغییرات {{cssxref("opacity")}} مورد نیاز این انیمیشن‌ها تعریف می‌کنیم.

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

بقیهٔ CSS برای اختصار نشان داده نشده است.

#### JavaScript

ابتدا ارجاع‌هایی به دکمهٔ `<button>` که عملیات `scroll()` را اجرا می‌کند، نوار ابزار `<div>` و عنصر اسکرول‌شوندهٔ `<section>` می‌گیریم:

```js
const scrollBtn = document.querySelector(".scroll");
const toolbar = document.querySelector("div");
const section = document.querySelector("section");
```

در ادامه، تابعی به نام `isInterrupted()` تعریف می‌کنیم که برای اجرا در پاسخ به پایان یافتن یک عملیات اسکرول طراحی شده است و یک مقدار بولی `interrupted` را به‌عنوان پارامتر می‌گیرد. این تابع پیامی را در کنسول ثبت می‌کند که نشان می‌دهد اسکرول به پایان رسیده و اینکه آیا عملیات قطع شده است (`interrupted` برابر با `true` است) یا خیر. علاوه بر این، اگر `interrupted` برابر با `true` باشد، یک `alert()` فراخوانی می‌کند تا وقفه را به‌وضوح نشان دهد.

```js
function isInterrupted(interrupted) {
  console.log(`Scroll finished;${interrupted ? " " : " not "}interrupted`);
  if (interrupted) {
    alert("Scroll interrupted!");
  }
}
```

وقتی روی دکمه کلیک می‌شود، بلافاصله کلاس `fade-out` را روی نوار ابزار اعمال می‌کنیم تا محو شود. سپس `scroll(0, 1000)` را روی `<section>` اجرا می‌کنیم تا محتوای آن ۱۰۰۰ پیکسل به پایین اسکرول شود؛ در همین حال منتظر حل شدن (resolve) پرامیس آن می‌مانیم و `result` را در یک ثابت ذخیره می‌کنیم. وقتی پرامیس حل شد، `isInterrupted()` را فراخوانی می‌کنیم تا گزارش دهد که عملیات اسکرول به پایان رسیده و آیا قطع شده است یا خیر. در نهایت، کلاس `fade-in` را روی نوار ابزار اعمال می‌کنیم تا دوباره ظاهر شود.

```js
scrollBtn.addEventListener("click", async () => {
  toolbar.className = "fade-out";
  const result = await section.scroll(0, 1000);
  isInterrupted(result.interrupted);
  toolbar.className = "fade-in";
});
```

برای اختصار، کدهایی که به `scroll()` مرتبط نیستند نشان داده نشده‌اند.

#### نتیجه

برای مشاهدهٔ رفتار اسکرول، روی دکمه‌ها کلیک کنید. توجه کنید که با فشردن یک دکمه، نوار ابزار محو می‌شود و پس از پایان اسکرول نرم، دوباره ظاهر می‌شود. همچنین سعی کنید یک دکمه را فشار دهید و پیش از پایان یافتن اولین عملیات اسکرول، سریعاً دکمهٔ دیگری را فشار دهید. توجه کنید که در این موارد، اسکرول به‌عنوان «قطع‌شده» گزارش می‌شود.

{{EmbedGHLiveSample("dom-examples/scroll-promises/element-methods/", "100%", 620)}}

همچنین می‌توانید [دمو را در یک تب جداگانه بارگذاری کنید](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) و [کد منبع](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods) را مشاهده کنید.

#### نکتهٔ جانبی دربارهٔ تشخیص ویژگی

اگر این مثال را در مرورگری اجرا کنید که از عملیات‌های اسکرول بازگردانندهٔ Promise پشتیبانی نمی‌کند، عملیات‌های اسکرول همچنان نرم خواهند بود، اما نوار ابزار پس از پایان عملیات محو و دوباره ظاهر نمی‌شود. تشخیص ویژگی توسط تابعی به نام `supportsScrollPromises()` انجام می‌شود که یک عملیات اسکرول را اجرا می‌کند و بررسی می‌کند که آیا مقدار بازگشتی آن یک پرامیس است:

```js
function supportsScrollPromises() {
  const test = section.scroll(0, 0);
  return test instanceof Promise;
}
```

برای مشاهدهٔ نحوهٔ استفاده از تشخیص ویژگی، به [کد منبع](https://github.com/mdn/dom-examples/blob/main/scroll-promises/element-methods/index.js) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}