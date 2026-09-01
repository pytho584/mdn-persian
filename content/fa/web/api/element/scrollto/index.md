---
title: "Element: scrollTo() method"
short-title: scrollTo()
slug: Web/API/Element/scrollTo
page-type: web-api-instance-method
browser-compat: api.Element.scrollTo
---

{{APIRef("CSSOM view API")}}

متد **`scrollTo()`** در رابط {{domxref("Element")}} به مجموعه‌ای از مختصات مشخص در داخل یک عنصر معین پیمایش می‌کند.

این متد نام مستعاری برای {{domxref("Element.scroll()")}} است.

## Syntax

```js-nolint
scrollTo(xCoord, yCoord)
scrollTo(options)
```

### Parameters

- `xCoord`
  - : مختصات x از محتوای قابل‌پیمایش عنصر، که می‌خواهید لبه چپ درگاه پیمایش (scrollport) عنصر به آن نقطه پیمایش شود.
- `yCoord`
  - : مختصات y از محتوای قابل‌پیمایش عنصر، که می‌خواهید لبه بالای درگاه پیمایش عنصر به آن نقطه پیمایش شود.
- `options`
  - : یک شیء شامل ویژگی‌های زیر:
    - `top` {{optional_inline}}
      - : مختصات y محتوای قابل‌پیمایش عنصر که می‌خواهید لبه بالای درگاه پیمایش عنصر به آن پیمایش شود. این همان پارامتر `yCoord` است.
    - `left` {{optional_inline}}
      - : مختصات x محتوای قابل‌پیمایش عنصر که می‌خواهید لبه چپ درگاه پیمایش عنصر به آن پیمایش شود. این همان پارامتر `xCoord` است.
    - `behavior` {{optional_inline}}
      - : تعیین می‌کند که پیمایش فوری انجام شود یا نرم و متحرک. این گزینه یک رشته است و باید یکی از مقادیر زیر را داشته باشد:
        - `smooth`: پیمایش به‌صورت نرم و با انیمیشن انجام می‌شود.
        - `instant`: پیمایش بلافاصله و در یک پرش انجام می‌شود.
        - `auto`: رفتار پیمایش با توجه به مقدار محاسبه‌شدهٔ ویژگی CSS {{cssxref("scroll-behavior")}} روی عنصر تعیین می‌شود.

        اگر این گزینه حذف شود، `behavior` به‌صورت پیش‌فرض روی `auto` قرار می‌گیرد.

### Return value

یک {{jsxref("Promise")}} که با شیئی شامل ویژگی زیر resolve می‌شود:

- `interrupted`
  - : یک مقدار بولی که نشان می‌دهد عملیات پیمایش قطع شده است (`true`) یا نه (`false`). چنین قطعی معمولاً زمانی رخ می‌دهد که یک پیمایش برنامه‌ای در حال انجام است و پیمایش برنامه‌ای دیگری روی همان عنصر، قبل از پایان یافتن پیمایش اول آغاز می‌شود.

## Examples

### Basic usage

```js
element.scrollTo(0, 1000);
```

استفاده از `options`:

```js
element.scrollTo({
  top: 100,
  left: 100,
  behavior: "smooth",
});
```

### Responding to the end of the scroll

در [نمونه روش‌های عنصر](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) ([مشاهده کد منبع](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods)) نشان داده می‌شود که چگونه می‌توان از مقدار بازگشتی Promise متد `scrollTo()` برای واکنش به پایان یک عملیات پیمایش استفاده کرد. این روش بیشتر در مواردی مفید است که پیمایش به‌مرور زمان و به‌صورت نرم انجام می‌شود (با قرار دادن گزینه [`behavior`](#behavior) روی `smooth`، یا با تنظیم ویژگی {{cssxref("scroll-behavior")}} عنصر پیمایش‌شونده روی `smooth`).

#### HTML

HTML ما شامل یک عنصر {{htmlelement("section")}} با چند پاراگراف محتوا و یک نوار ابزار از نوع {{htmlelement("div")}} است که شامل عناصر {{htmlelement("button")}} می‌شود و عملیات‌های مختلف پیمایش را روی `<section>` فعال می‌کنند.

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

به عنصر `<section>` یک {{cssxref("height")}} ثابت و مقدار {{cssxref("overflow-y")}} برابر با `scroll` می‌دهیم تا به‌صورت عمودی پیمایش شود؛ همچنین ویژگی {{cssxref("scroll-behavior")}} آن را روی `smooth` تنظیم می‌کنیم تا همه عملیات‌های پیمایش به‌صورت نرم و در طول زمان انجام شوند، نه به‌طور آنی.

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

همچنین دو انتخابگر کلاس (class selector) ایجاد می‌کنیم؛ هرگاه کلاس `fade-out` یا `fade-in` به عنصری اعمال شود، یک {{cssxref("animation")}} اعمال می‌شود تا بهترتیب به‌آرامی محو شود یا ظاهر گردد. علاوه بر این، بلوک‌های {{cssxref("@keyframes")}} را تعریف می‌کنیم تا تغییرات موردنیاز {{cssxref("opacity")}} برای آن انیمیشن‌ها مشخص شود.

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

باقی CSS برای اختصار نمایش داده نشده است.

#### JavaScript

ابتدا با گرفتن ارجاع به دکمه‌ای که عملیات `scrollTo()` را اجرا می‌کند، نوار ابزار `<div>` و بخش پیمایش‌شونده `<section>` شروع می‌کنیم:

```js
const scrollToBtn = document.querySelector(".scroll-to");
const toolbar = document.querySelector("div");
const section = document.querySelector("section");
```

سپس تابعی به نام `isInterrupted()` تعریف می‌کنیم که برای اجرا در پاسخ به پایان یک عملیات پیمایش طراحی شده است و یک مقدار بولی `interrupted` را به‌عنوان پارامتر می‌گیرد. این تابع پیامی را در کنسول ثبت می‌کند تا بگوید پیمایش تمام شده است و مشخص کند که آیا عملیات قطع شده است (`interrupted` برابر `true`) یا نه. علاوه بر این، اگر `interrupted` برابر `true` باشد، یک `alert()` فراخوانی می‌شود تا قطع شدن را به‌وضوح نشان دهد.

```js
function isInterrupted(interrupted) {
  console.log(`Scroll finished;${interrupted ? " " : " not "}interrupted`);
  if (interrupted) {
    alert("Scroll interrupted!");
  }
}
```

هنگامی که دکمه کلیک می‌شود، بلافاصله کلاس `fade-out` را روی نوار ابزار اعمال می‌کنیم تا محو شود. سپس `scrollTo(0, 0)` را روی `<section>` اجرا می‌کنیم تا محتوای آن به بالا پیمایش شود؛ هم‌زمان منتظر resolve شدن Promise می‌مانیم و `result` را در یک ثابت ذخیره می‌کنیم. وقتی Promise resolve شد، `isInterrupted()` را فراخوانی می‌کنیم تا گزارش دهد عملیات پیمایش پایان یافته است و آیا قطع شده است. در پایان، کلاس `fade-in` را روی نوار ابزار اعمال می‌کنیم تا دوباره ظاهر شود.

```js
scrollToBtn.addEventListener("click", async () => {
  toolbar.className = "fade-out";
  const result = await section.scrollTo(0, 0);
  isInterrupted(result.interrupted);
  toolbar.className = "fade-in";
});
```

کدهای نامرتبط با `scrollTo()` برای اختصار نمایش داده نشده‌اند.

#### Result

برای دیدن رفتار پیمایش، روی دکمه‌ها کلیک کنید. توجه کنید که با فشردن دکمه، نوار ابزار محو می‌شود و پس از پایان یافتن پیمایش نرم، دوباره ظاهر می‌شود. همچنین دکمه‌ای را فشار دهید و سپس قبل از پایان یافتن عملیات پیمایش اول، دکمه دیگری را سریع فشار دهید. توجه کنید که در این حالت‌ها پیمایش به‌عنوان قطع‌شده گزارش می‌شود.

{{EmbedGHLiveSample("dom-examples/scroll-promises/element-methods/", "100%", 620)}}

همچنین می‌توانید [نمونه را در یک تب جداگانه بارگذاری کنید](https://mdn.github.io/dom-examples/scroll-promises/element-methods/) و [کد منبع را مشاهده کنید](https://github.com/mdn/dom-examples/tree/main/scroll-promises/element-methods).

#### نکته: تشخیص ویژگی

اگر این مثال را در مرورگری اجرا کنید که از عملیات‌های پیمایش بازگشت‌دهنده Promise پشتیبانی نمی‌کند، پیمایش همچنان نرم انجام می‌شود، اما نوار ابزار پس از پایان عملیات، محو و دوباره ظاهر نمی‌شود. تشخیص ویژگی (feature detection) توسط تابعی به نام `supportsScrollPromises()` انجام می‌شود که یک عملیات پیمایش را اجرا می‌کند و بررسی می‌کند که آیا مقدار بازگشتی آن یک Promise است:

```js
function supportsScrollPromises() {
  const test = section.scroll(0, 0);
  return test instanceof Promise;
}
```

برای دیدن نحوه استفاده از تشخیص ویژگی، [کد منبع](https://github.com/mdn/dom-examples/blob/main/scroll-promises/element-methods/index.js) را بررسی کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element.scrollTop")}}, {{domxref("Element.scrollLeft")}}
- {{domxref("Window.scrollTo()")}}