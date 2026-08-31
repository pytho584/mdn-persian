---
title: "Animation: commitStyles() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/commitStyles"
translated_by: "n8n + AI"
---

---
title: "Animation: commitStyles() method"
short-title: commitStyles()
slug: Web/API/Animation/commitStyles
page-type: web-api-instance-method
browser-compat: api.Animation.commitStyles
---

{{APIRef("Web Animations")}}

متود `commitStyles()` از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) در رابط {{domxref("Animation")}}، [مقادیر محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) استایل‌های فعلی انیمیشن را در ویژگی [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) عنصر هدف می‌نویسد.

این متود عمدتاً برای نوشتن استایل‌های حالت نهایی یک انیمیشن در عنصر هدف استفاده می‌شود، به‌طوری‌که استایل‌بندی پس از پایان انیمیشن باقی بماند.

## نحو (Syntax)

```js-nolint
commitStyles()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## توضیحات

متود `commitStyles()` عمدتاً برای نوشتن [مقادیر محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) حالت نهایی یک انیمیشن در ویژگی [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) عنصر هدف استفاده می‌شود، به‌طوری‌که استایل‌بندی پس از پایان انیمیشن باقی بماند.
این کار می‌تواند زمانی انجام شود که انیمیشن به پایان رسیده است (یعنی ویژگی {{domxref("Animation.finished","finished")}} شیء {{domxref("Animation")}} حل شده باشد).

### `commitStyles()` همراه با حالت fill

در مرورگرهای قدیمی‌تر، برای اینکه بتوانید استایل‌ها را _پس از_ پایان انیمیشن روی عنصر commit کنید، باید [`حالت fill`](/en-US/docs/Web/API/KeyframeEffect/KeyframeEffect#fill) را مشخص کنید.

کد زیر نشان می‌دهد که چگونه می‌توانید یک عنصر به نام `animatedElement` را انیمیت کنید و با تنظیم [`fill: "forwards"`](/en-US/docs/Web/API/KeyframeEffect/KeyframeEffect#fill) استایل‌های انیمیشن را پس از پایان حفظ کنید.
پس از پایان انیمیشن، استایل‌ها را با `commitStyles()` روی عنصر commit می‌کنیم.

```js
// شروع انیمیشن
const animation = animatedElement.animate(
  { transform: "translate(100px)" },
  { duration: 500, fill: "forwards" },
);

// منتظر ماندن برای پایان انیمیشن
await animation.finished;
// commit کردن state انیمیشن روی ویژگی style عنصر animatedElement
animation.commitStyles();
// لغو انیمیشن
animation.cancel();
```

چون `fill` انیمیشن را به‌طور نامحدود حفظ می‌کند، پس از commit کردن استایل‌ها، انیمیشن را لغو می‌کنیم.

توجه داشته باشید که همان اثر را می‌توان تنها با `fill` نیز به دست آورد، اما [استفاده از انیمیشن‌های با fill نامحدود توصیه نمی‌شود](https://drafts.csswg.org/web-animations-1/#fill-behavior).
انیمیشن‌ها [بر همه استایل‌های استاتیک اولویت دارند](/en-US/docs/Web/CSS/Guides/Cascade/Introduction#cascading_order)، بنابراین یک انیمیشن با fill نامحدود می‌تواند مانع از استایل‌دهی عادی عنصر هدف شود.

> [!NOTE]
> همچنین ممکن است بتوانید با تنظیم حالت نهایی به‌عنوان استایل‌های اولیه عنصر و انیمیت کردن به سمت حالت نهایی، از ذخیره صریح حالت نهایی اجتناب کنید.

### `commitStyles()` بدون تنظیم حالت fill

در مرورگرهای جدیدتر نیازی به تنظیم [`حالت fill`](/en-US/docs/Web/API/KeyframeEffect/KeyframeEffect#fill) ندارید (برای نسخه‌های خاص به [جدول سازگاری مرورگر](#browser_compatibility) مراجعه کنید).

> [!NOTE]
> هیچ راهی برای بررسی ویژگی (feature check) این رفتار جدید وجود ندارد.
> در حال حاضر بیشتر کدها باید همچنان `fill` را مطابق بخش قبل تنظیم کنند.

کد زیر نشان می‌دهد که چگونه می‌توانید یک عنصر به نام `animatedElement` را انیمیت کنید، با استفاده از ویژگی {{domxref("Animation.finished","finished")}} منتظر پایان انیمیشن بمانید و سپس استایل‌ها را با `commitStyles()` روی عنصر commit کنید.
چون `fill` را تنظیم نکرده‌ایم، نیازی به لغو انیمیشن پس از آن نداریم.

```js
// شروع انیمیشن
const animation = animatedElement.animate(
  { transform: "translate(100px)" },
  { duration: 500 },
);

// منتظر ماندن برای پایان انیمیشن
await animation.finished;

// commit کردن state انیمیشن روی ویژگی style عنصر animatedElement
animation.commitStyles();
```

`commitStyles()` حتی اگر انیمیشن [به‌طور خودکار حذف شده باشد](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#automatically_removing_filling_animations) نیز کار می‌کند.
پس از commit شدن استایل‌های عنصر، می‌توان آن‌ها را مانند حالت عادی تغییر داد و جایگزین کرد.

## مثال‌ها

### انیمیشن با و بدون استفاده از fill

این مثال نشان می‌دهد که چگونه می‌توانید از `commitStyles()` برای ذخیره استایل‌های محاسبه‌شده در پایان انیمیشن، هم با استفاده از `fill` و هم بدون آن استفاده کنید.
همچنین مثالی از آنچه که اگر نه `commitStyles()` و نه `fill` استفاده شود اتفاق می‌افتد، برای مقایسه ارائه می‌دهد.

مثال ابتدا دو دکمه با برچسب‌های "commitStyles() only" و "commitStyles() with fill" نمایش می‌دهد.
هر دو دکمه هنگام کلیک انیمیت می‌شوند و هر دو دکمه برای حفظ حالت نهایی انیمیشن، `commitStyles()` را فراخوانی می‌کنند.
تفاوت این است که "commitStyles() only" برای حفظ حالت نهایی انیمیشن، `fill: "forwards"` را مشخص نمی‌کند.
در مرورگرهایی که با مشخصات فعلی مطابقت ندارند، ممکن است حالت نهایی ذخیره نشود.

سپس کد یک دکمه "No commitStyles() or fill" برای مقایسه و یک دکمه "Reset" نمایش می‌دهد.

#### HTML

```html
<button class="commit-styles">commitStyles() only</button>
<button class="commit-with-fill">commitStyles() with fill</button>
<button class="no-commit-or-fill">No commitStyles() or fill</button>
```

```html hidden
<button id="reset" type="button">Reset</button>
```

```css hidden
button {
  margin: 0.5rem;
  display: block;
}
```

```js hidden
const reload = document.querySelector("#reset");

reload.addEventListener("click", () => {
  window.location.reload(true);
});
```

#### JavaScript

این کد یک handler کلیک برای دکمه "commitStyles() only" تعریف می‌کند.
این دکمه هنگام کلیک به سمت راست یا چپ حرکت می‌کند.
توجه کنید که `commitStyles()` بلافاصله پس از پایان انیمیشن فراخوانی می‌شود.

```js
let offset1 = 0;

const commitStyles = document.querySelector(".commit-styles");

commitStyles.addEventListener("click", async (event) => {
  // شروع انیمیشن
  offset1 = 100 - offset1;
  const animation = commitStyles.animate(
    { transform: `translate(${offset1}px)` },
    { duration: 500 },
  );

  // منتظر ماندن برای پایان انیمیشن
  await animation.finished;
  // commit کردن state انیمیشن روی ویژگی style
  animation.commitStyles();
});
```

این کد یک handler کلیک برای دکمه "commitStyles() with fill" تعریف می‌کند.
این دکمه نیز هنگام کلیک به سمت راست یا چپ حرکت می‌کند.
چون `fill` تعریف شده است، باید انیمیشن را پس از آن لغو کند.

توجه کنید که `commitStyles()` بلافاصله پس از پایان انیمیشن فراخوانی می‌شود.

```js
const commitStylesWithFill = document.querySelector(".commit-with-fill");
let offset2 = 0;

commitStylesWithFill.addEventListener("click", async (event) => {
  // شروع انیمیشن
  offset2 = 100 - offset2;
  const animation = commitStylesWithFill.animate(
    { transform: `translate(${offset2}px)` },
    { duration: 500, fill: "forwards" },
  );

  // منتظر ماندن برای پایان انیمیشن
  await animation.finished;
  // commit کردن state انیمیشن روی ویژگی style
  animation.commitStyles();
  // لغو انیمیشن
  animation.cancel();
});
```

این کد یک handler کلیک برای دکمه "No commitStyles() or fill" تعریف می‌کند.
این دکمه نیز هنگام کلیک به سمت راست یا چپ حرکت می‌کند.
نه `fill` تعریف می‌کند و نه انیمیشن را لغو می‌کنیم.

```js
const noCommitStylesOrFill = document.querySelector(".no-commit-or-fill");
let offset3 = 0;

noCommitStylesOrFill.addEventListener("click", async (event) => {
  // شروع انیمیشن
  offset3 = 100 - offset3;
  const animation = noCommitStylesOrFill.animate(
    { transform: `translate(${offset3}px)` },
    { duration: 500 },
  );
});
```

#### نتیجه

برای انیمیت کردن دکمه‌ها روی آن‌ها کلیک کنید.
توجه کنید که اگر مرورگر فعلی همچنان برای commit شدن استایل‌ها پس از پایان انیمیشن به `fill` نیاز داشته باشد، دکمه اول در پایان انیمیشن "پرش" خواهد کرد.
دکمه "No commitStyles() or fill" همیشه در پایان پرش می‌کند، زیرا حالت نهایی ذخیره نشده است.

{{EmbedLiveSample("Animation with and without using fill")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}} برای سایر متودها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.