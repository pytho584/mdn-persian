---
title: "Element: scrollBy() method"
short-title: scrollBy()
slug: Web/API/Element/scrollBy
page-type: web-api-instance-method
browser-compat: api.Element.scrollBy
---

{{APIRef("CSSOM view API")}}

متد **`scrollBy()`** از رابط {{domxref("Element")}}، عنصر را به میزان معین پیمایش می‌کند.

## سینتکس

```js-nolint
scrollBy(xCoord, yCoord)
scrollBy(options)
```

### پارامترها

- `xCoord`
  - : مقدار پیکسل افقی که می‌خواهید به آن میزان پیمایش انجام شود.
- `yCoord`
  - : مقدار پیکسل عمودی که می‌خواهید به آن میزان پیمایش انجام شود.
- `options`
  - : یک شیء شامل خصوصیات زیر:
    - `top` {{optional_inline}}
      - : تعداد پیکسل‌ها در امتداد محور Y را برای پیمایش پنجره یا عنصر مشخص می‌کند.
    - `left` {{optional_inline}}
      - : تعداد پیکسل‌ها در امتداد محور X را برای پیمایش پنجره یا عنصر مشخص می‌کند.
    - `behavior` {{optional_inline}}
      - : تعیین می‌کند که پیمایش فوری است یا به‌صورت نرم و روان انیمیشن شود. این گزینه یک رشته است که باید یکی از مقادیر زیر را بگیرد:
        - `smooth`: پیمایش به‌صورت نرم انیمیشن می‌شود.
        - `instant`: پیمایش بلافاصله و در یک پرش انجام می‌شود.
        - `auto`: رفتار پیمایش توسط مقدار محاسبه‌شده ویژگی CSS {{cssxref("scroll-behavior")}} روی عنصر تعیین می‌شود.

        اگر حذف شود، `behavior` به‌طور پیش‌فرض `auto` خواهد بود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء شامل خصوصیت زیر تکمیل می‌شود:

- `interrupted`
  - : یک مقدار بولی که نشان می‌دهد آیا عملیات پیمایش قطع شده است (`true`) یا نه (`false`). چنین قطعی معمولاً زمانی رخ می‌دهد که یک پیمایش برنامه‌ای در حال انجام است و پیمایش برنامه‌ای دیگری روی همان عنصر قبل از پایان پیمایش اول شروع می‌شود.

## مثال‌ها

### استفاده پایه

```js
// scroll an element
element.scrollBy(300, 300);
```

استفاده از `options`:

```js
element.scrollBy({
  top: 100,
  left: 100,
  behavior: "smooth",
});
```

### پاسخ به پایان پیمایش

دموی [متدهای عنصر](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) ما ([مشاهده سورس کد](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods)) نشان می‌دهد که چگونه می‌توان از مقدار بازگشتی promise از `scrollBy()` برای پاسخ به پایان یک عملیات پیمایش استفاده کرد. این تکنیک بیشتر در مواردی مفید است که پیمایش به‌صورت نرم و در طول زمان انجام می‌شود (با قرار دادن گزینه [`behavior`](#behavior) روی `smooth` یا با تنظیم ویژگی {{cssxref("scroll-behavior")}} عنصر پیمایش‌شونده روی `smooth`).

#### HTML

HTML ما شامل یک عنصر {{htmlelement("section")}} است که چند پاراگراف محتوا و یک نوار ابزار از عنصر {{htmlelement("div")}} شامل عناصر {{htmlelement("button")}} که عملیات پیمایش مختلفی را روی `<section>` فعال می‌کنند، دارد.

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

ما به عنصر `<section>` یک {{cssxref("height")}} ثابت و مقدار {{cssxref("overflow-y")}} برابر با `scroll` می‌دهیم تا به‌صورت عمودی پیمایش شود، و ویژگی {{cssxref("scroll-behavior")}} آن را روی `smooth` تنظیم می‌کنیم تا هر عملیات پیمایش به‌جای انجام فوری، به‌صورت نرم و در طول زمان انیمیشن شود.

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

همچنین دو انتخاب‌گر کلاس ایجاد می‌کنیم؛ هنگامی که یک کلاس `fade-out` یا `fade-in` روی یک عنصر اعمال می‌شود، یک {{cssxref("animation")}} اعمال می‌شود تا به‌ترتیب به‌صورت نرم محو یا ظاهر شود. ما همچنین بلوک‌های {{cssxref("@keyframes")}} را برای تعریف تغییرات {{cssxref("opacity")}} موردنیاز برای آن انیمیشن‌ها تعریف می‌کنیم.

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

ما با دریافت ارجاع به `<button>` که عملیات `scrollBy()` را اجرا می‌کند، `<div>` نوار ابزار، و `<section>` در حال پیمایش شروع می‌کنیم:

```js
const scrollByBtn = document.querySelector(".scroll-by");
const toolbar = document.querySelector("div");
const section = document.querySelector("section");
```

در ادامه، تابعی به نام `isInterrupted()` تعریف می‌کنیم که برای اجرا در پاسخ به پایان یک عملیات پیمایش طراحی شده است و یک مقدار بولی `interrupted` را به‌عنوان پارامتر می‌گیرد. این تابع یک پیام در کنسول ثبت می‌کند تا بگوید پیمایش تمام شده و مشخص کند آیا عملیات قطع شده است (`interrupted` برابر با `true`) یا نه. علاوه بر این، اگر `interrupted` برابر با `true` باشد، یک `alert()` فراخوانی می‌کند تا قطع شدن را به‌وضوح نشان دهد.

```js
function isInterrupted(interrupted) {
  console.log(`Scroll finished;${interrupted ? " " : " not "}interrupted`);
  if (interrupted) {
    alert("Scroll interrupted!");
  }
}
```

وقتی دکمه کلیک می‌شود، بلافاصله کلاس `fade-out` را روی نوار ابزار اعمال می‌کنیم تا محو شود. سپس `scrollBy(0, 200)` را روی `<section>` اجرا می‌کنیم تا محتوای آن ۲۰۰ پیکسل به پایین پیمایش شود، در حالی که منتظر resolve شدن promise آن هستیم و `result` را در یک ثابت ذخیره می‌کنیم. وقتی promise resolve شد، `isInterrupted()` را فراخوانی می‌کنیم تا گزارش دهد عملیات پیمایش تمام شده است و آیا قطع شده یا نه. در نهایت، کلاس `fade-in` را روی نوار ابزار اعمال می‌کنیم تا دوباره ظاهر شود.

```js
scrollByBtn.addEventListener("click", async () => {
  toolbar.className = "fade-out";
  const result = await section.scrollBy(0, 200);
  isInterrupted(result.interrupted);
  toolbar.className = "fade-in";
});
```

کدهای نامرتبط با `scrollBy()` برای اختصار نشان داده نشده‌اند.

#### نتیجه

برای مشاهده رفتار پیمایش، دکمه‌ها را کلیک کنید. توجه کنید که با فشردن یک دکمه، نوار ابزار محو می‌شود و پس از پایان پیمایش نرم دوباره ظاهر می‌شود. همچنین سعی کنید یک دکمه را فشار دهید و سپس قبل از پایان اولین عملیات پیمایش، دکمه دیگری را سریع فشار دهید. توجه کنید که در این موارد، پیمایش به‌عنوان قطع‌شده گزارش می‌شود.

{{EmbedGHLiveSample("dom-examples/scroll-promises/element-methods/", "100%", 620)}}

همچنین می‌توانید [دمو را در برگه‌ای جداگانه بارگذاری کنید](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) و [کد منبع](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods) را مشاهده کنید.

#### نکته‌ای درباره تشخیص ویژگی

اگر این مثال را در مرورگری اجرا کنید که از عملیات پیمایش بازگشت‌دهنده promise پشتیبانی نمی‌کند، عملیات پیمایش همچنان نرم خواهد بود، اما نوار ابزار پس از پایان عملیات محو و دوباره ظاهر نمی‌شود. تشخیص ویژگی توسط تابعی به نام `supportsScrollPromises()` انجام می‌شود که یک عملیات پیمایش اجرا می‌کند و بررسی می‌کند که آیا مقدار بازگشتی آن یک promise است یا نه:

```js
function supportsScrollPromises() {
  const test = section.scroll(0, 0);
  return test instanceof Promise;
}
```

برای مشاهده نحوه استفاده از تشخیص ویژگی، به [کد منبع](https://github.com/mdn/dom-examples/blob/main/scroll-promises/element-methods/index.js) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}
