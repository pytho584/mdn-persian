---
title: "Element: startViewTransition() method"
short-title: startViewTransition()
slug: Web/API/Element/startViewTransition
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Element.startViewTransition
---

{{APIRef("View Transition API")}}{{SeeCompatTable}}

متد **`startViewTransition()`** از واسط {{domxref("Element")}} یک [محدوده-عنصر](/en-US/docs/Web/API/View_Transition_API/Using_element-scoped) [انتقال نمای](/en-US/docs/Web/API/View_Transition_API) جدید در همان سند ({{glossary("SPA")}}) آغاز می‌کند و یک شیء {{domxref("ViewTransition")}} برای نمایش آن برمی‌گرداند.

ترتیب گام‌هایی که هنگام فراخوانی `startViewTransition()` دنبال می‌شود، در بخش [فرایند انتقال نما](/en-US/docs/Web/API/View_Transition_API/Using#the_view_transition_process) توضیح داده شده است.

## سینتکس

```js-nolint
startViewTransition()
startViewTransition(updateCallback)
startViewTransition(options)
```

### پارامترها

- `updateCallback` {{optional_inline}}
  - : یک تابع بازخواند (callback) که برای به‌روزرسانی درخت DOM عنصر در طول فرایند انتقال نمای SPA فراخوانی می‌شود. این تابع یک {{jsxref("Promise")}} برمی‌گرداند. تابع بازخواند پس از آنکه API یک عکس فوری از صفحهٔ فعلی گرفت، فراخوانی می‌شود. هنگامی که پرامیسی که تابع بازخواند برمی‌گرداند با موفقیت انجام شود، انتقال نما در فریم بعدی آغاز می‌شود. اگر پرامیسی که تابع بازخواند برمی‌گرداند رد شود، انتقال رها می‌شود.
- `options` {{optional_inline}}
  - : یک شیء حاوی گزینه‌هایی برای پیکربندی انتقال نما. می‌تواند شامل ویژگی‌های زیر باشد:
    - `update` {{optional_inline}}
      - : همان تابع `updateCallback` که در بالا توضیح داده شد. به‌صورت پیش‌فرض `null` است.
    - `types` {{optional_inline}}
      - : آرایه‌ای از رشته‌ها که نشان‌دهندهٔ نوع‌های اعمال‌شده به انتقال نما هستند. [نوع‌های انتقال نما](/en-US/docs/Web/API/View_Transition_API/Using_types) امکان اعمال انتخابی استایل‌های CSS یا منطق جاوااسکریپت را بر اساس نوع انتقالِ در حال رخ‌دادن فراهم می‌کنند. به‌صورت پیش‌فرض آرایه‌ای خالی است.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("ViewTransition")}}.

## توضیحات

فراخوانی `Element.startViewTransition()` روی یک عنصر، یک انتقال نما ایجاد می‌کند که به زیردرخت DOM آن عنصر محدوده (scope) شده است. هر تغییر DOM که درون تابع بازخواند `startViewTransition()` انجام شود، تنها در صورتی انتقال می‌یابد که آن به‌روزرسانی‌ها درون زیردرخت DOM عنصرِ فراخواننده انجام شده باشند. به این عنصر، **ریشهٔ** (root) انتقال نما گفته می‌شود و به زیردرخت DOM، **محدودهٔ** (scope) انتقال نما گفته می‌شود.

[درخت شبه‌المان‌های](/en-US/docs/Web/API/View_Transition_API/Using#different_animations_for_different_elements) یک انتقال نمای محدوده-عنصر، درون عنصر ریشهٔ انتقال قرار می‌گیرد؛ چنانکه در مثال زیر نشان داده شده است، جایی که یک انتقال نما روی یک پیوند در حال اجراست:

```plain
<a href="#">
  ├─ ::view-transition
  │  └─ ::view-transition-group(root)
  │     └─ ::view-transition-image-pair(root)
  │        ├─ ::view-transition-old(root)
  │        └─ ::view-transition-new(root)
  |
  |
  "Link text"
</a>
```

انتقال‌های نمای محدوده-عنصر مزیت‌های زیادی نسبت به همتایان محدوده-سند خود دارند:

- می‌توانید بیش از یکی از آن‌ها را هم‌زمان اجرا کنید.
- هنگام اجرا، تنها محدودهٔ انتقال نما تا پایان انتقال غیرتعاملی می‌شود؛ بقیهٔ صفحه همچنان تعاملی باقی می‌ماند. انتقال‌های نمای محدوده-سند، کل صفحه را تا تکمیل انتقال غیرتعاملی می‌کنند.
- درخت شبه‌المان‌های انتقال تنها روی محدودهٔ عنصر قرار می‌گیرد، نه روی کل صفحه؛ یعنی هنگام شروع انیمیشن انتقال محدوده-سند، با مشکلات ناپدیدشدن عناصر روی‌هم‌قرارگرفته در زیر بخشِ در حال به‌روزرسانی صفحه مواجه نخواهید شد.
- اگر محتوای محدوده با استفاده از {{cssxref("overflow")}} برش خورده باشد، در طول انتقال نما برش‌خورده باقی می‌ماند. انتقال‌های نمای محدوده-سند از ظرف‌های برش‌دهنده بیرون می‌ریزند، زیرا درخت شبه‌المان‌های آن‌ها روی کل صفحه ترسیم می‌شود.

## مثال‌ها

برای مثال‌های بیشتر، [استفاده از انتقال‌های نمای محدوده-عنصر](/en-US/docs/Web/API/View_Transition_API/Using_element-scoped) را ببینید.

### انیمیشن‌سازی یک اسلایدشو

این یک مثال پایه از استفاده از انتقال نمای محدوده-عنصر برای انیمیشن‌سازی نرم تغییرات DOM در یک اسلایدشو هنگام کلیک روی یک دکمه است.

#### HTML

HTML شامل یک عنصر {{htmlelement("section")}} برای نمایش اسلایدشو، یک {{htmlelement("button")}} که با فشردن آن محتوای اسلاید تغییر می‌کند، و محتوای {{htmlelement("p")}} در اطراف آن‌ها است.

```html live-sample___basic_usage
<p>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Donec a diam lectus.
  Set sit amet ipsum mauris.
</p>
<section>Slide 1</section>
<button>Update slide</button>
<p>
  Maecenas congue ligula as quam viverra nec consectetur ant hendrerit. Donec et
  mollis dolor.
</p>
```

#### CSS

CSS از [flexbox](/en-US/docs/Learn_web_development/Core/CSS_layout/Flexbox) برای وسط‌چین کردن محتوای اسلاید استفاده می‌کند و {{cssxref("animation-duration")}} انتقال نما را از طریق شبه‌المان {{CSSXRef("::view-transition-group")}} روی `1s` تنظیم می‌کند.

```css hidden live-sample___basic_usage
html {
  font-family: sans-serif;
}
section {
  height: 200px;
  font-size: 2rem;
  background-color: green;
}
button {
  position: absolute;
  top: 5px;
  right: 5px;
}
```

```css live-sample___basic_usage
section {
  display: flex;
  justify-content: center;
  align-items: center;
}
::view-transition-group(root) {
  animation-duration: 1s;
}
```

#### JavaScript

اسکریپت با به‌دست آوردن ارجاع‌هایی به عناصر `<section>` و `<button>` آغاز می‌شود و یک شنوندهٔ رویداد `click` به دکمه اضافه می‌کند.

```js live-sample___basic_usage
const slide = document.querySelector("section");
const btn = document.querySelector("button");
btn.addEventListener("click", handleClick);
```

سپس تابعی به نام `updateSlide()` تعریف می‌کنیم که محتوا و رنگ پس‌زمینهٔ اسلاید را بین دو مجموعه مقدار جابه‌جا می‌کند.

```js live-sample___basic_usage
function updateSlide() {
  if (slide.textContent === "Slide 1") {
    slide.textContent = "Slide 2";
    slide.style.backgroundColor = "orange";
  } else {
    slide.textContent = "Slide 1";
    slide.style.backgroundColor = "green";
  }
}
```

در نهایت، تابع مدیریت رویداد، یعنی `handleClick()` را تعریف می‌کنیم. وقتی دکمه کلیک می‌شود، ابتدا بررسی می‌کنیم که آیا `Element.startViewTransition()` وجود دارد یا نه؛ اگر وجود نداشت، فقط تابع `updateSlide()` را اجرا می‌کنیم و `return` می‌کنیم. این کار تضمین می‌کند که به‌روزرسانی همچنان در مرورگرهای غیرپشتیبان نیز کار کند، البته بدون انیمیشن. اگر `Element.startViewTransition()` پشتیبانی شود، آن را روی عنصر `<section>` فراخوانی می‌کنیم و `updateSlide()` را درون تابع بازخواند آن صدا می‌زنیم.

```js live-sample___basic_usage
function handleClick() {
  if (!slide.startViewTransition) {
    updateSlide();
    return;
  }

  const transition = slide.startViewTransition(() => {
    updateSlide();
  });
}
```

#### نتیجه

{{EmbedLiveSample("basic_usage", "100%", "340")}}

روی دکمهٔ «Update slide» کلیک کنید تا DOM عنصر اسلاید به‌روزرسانی شود و انتقال نما را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.activeViewTransition")}}
- {{domxref("Document.startViewTransition()")}}
- شبه‌کلاس {{CSSXRef(":active-view-transition")}}
- شبه‌کلاس {{cssxref(":active-view-transition-type", ":active-view-transition-type()")}}
- [API انتقال نما](/en-US/docs/Web/API/View_Transition_API)
- [استفاده از API انتقال نما](/en-US/docs/Web/API/View_Transition_API/Using)
- [استفاده از نوع‌های انتقال نما](/en-US/docs/Web/API/View_Transition_API/Using_types)
- [استفاده از انتقال‌های نمای محدوده-عنصر](/en-US/docs/Web/API/View_Transition_API/Using_element-scoped)