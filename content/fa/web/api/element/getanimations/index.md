---
title: "Element: getAnimations() method"
short-title: getAnimations()
slug: Web/API/Element/getAnimations
page-type: web-api-instance-method
browser-compat: api.Element.getAnimations
---

{{APIRef("Web Animations")}}

متد `getAnimations()` در رابط {{domxref("Element")}} آرایه‌ای از تمام اشیاء {{domxref("Animation")}} را بازمی‌گرداند که روی این عنصر اثر می‌گذارند یا قرار است در آینده اثر بگذارند. این متد به‌صورت اختیاری می‌تواند اشیاء {{domxref("Animation")}} را برای عناصر فرزند و [شبه‌عنصرهای](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) آن‌ها، یا فقط برای شبه‌عنصر مشخص‌شده، بازگرداند.

> [!NOTE]
> این آرایه شامل [انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations)، [ترنزیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Transitions) و [انیمیشن‌های وب](/en-US/docs/Web/API/Web_Animations_API) است.

## نحو

```js-nolint
getAnimations()
getAnimations(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء options شامل ویژگی‌های زیر:
    - `subtree`
      - : یک مقدار بولین که اگر `true` باشد، باعث می‌شود انیمیشن‌هایی که فرزندانِ *Element* را هدف قرار می‌دهند نیز بازگردانده شوند. این شامل انیمیشن‌هایی است که هر [شبه‌عنصرِ](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) CSS متصل به *Element* یا یکی از فرزندان آن را هدف قرار می‌دهند. مقدار پیش‌فرض `false` است.
    - `pseudoElement`
      - : رشته‌ای که یک [شبه‌عنصر](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) را به‌عنوان عنصر هدف مشخص می‌کند، مانند [`::after`](/en-US/docs/Web/CSS/Reference/Selectors/::after).

    توجه داشته باشید که تعیین هم‌زمان `pseudoElement` و `subtree` معادل تعیین فقط `pseudoElement` است.

### مقدار بازگشتی

یک {{jsxref("Array")}} از اشیاء {{domxref("Animation")}}، که هر کدام نمایانگر انیمیشنی است که در حال حاضر {{domxref("Element")}} را هدف قرار می‌دهد.

اگر پارامتر `{ subtree: true }` مشخص شده باشد، مقدار بازگشتی شامل اشیاء انیمیشنی نیز می‌شود که عناصر فرزند، از جمله شبه‌عنصرها را هدف قرار می‌دهند. اگر `options.pseudoElement` مشخص شده باشد، مقدار بازگشتی فقط شامل اشیاء انیمیشنی است که با شبه‌عنصر انتخاب‌شده مطابقت دارند.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : یک شبه‌عنصر نامعتبر در پارامتر [`options.pseudoElement`](#pseudoelement) ارسال شده است.

## مثال‌ها

### منتظر ماندن برای تمام انیمیشن‌های یک عنصر و فرزندان آن

قطعه‌کد زیر منتظر می‌ماند تا همه انیمیشن‌های روی `elem` و فرزندانش تمام شوند و سپس عنصر را از سند حذف می‌کند.

```js
Promise.all(
  elem.getAnimations({ subtree: true }).map((animation) => animation.finished),
).then(() => elem.remove());
```

### دریافت انیمیشن‌های یک شبه‌عنصر هدف

این مثال یک نوار پیشرفت را با استفاده از یک شبه‌عنصر نمایش می‌دهد. از `getAnimations()` برای بازگرداندن انیمیشن‌های آن شبه‌عنصر استفاده می‌کند، آن‌ها را اجرا می‌کند و پس از کامل شدن انیمیشن، نوار پیشرفت را حذف می‌کند.

توجه داشته باشید که کد از یک رویکرد جایگزین (fallback) برای دریافت انیمیشن‌ها استفاده می‌کند، در صورتی که گزینه `pseudoElement` پشتیبانی نشود. همچنین کد پنهانی برای نمایش دکمه «Restart» وجود دارد.

#### HTML

```html
<div class="progress-bar" id="bar"></div>
```

#### CSS

CSS عنصر نوار پیشرفت را به‌گونه‌ای استایل می‌دهد که در عرض ۳ ثانیه در طول ظرف خود حرکت کند. انیمیشن در ابتدا متوقف شده است تا بتوانیم آن را از طریق جاوااسکریپت شروع کنیم.

```css
.progress-bar {
  width: 100%;
  height: 20px;
  background: #eeeeee;
  border-radius: 4px;
  overflow: hidden;
}

.progress-bar::after {
  content: "";
  display: block;
  height: 100%;
  width: 0%;
  background: #4f46e5;
  border-radius: 4px;
  animation: fill-progress 3s ease-in-out forwards paused;
}

@keyframes fill-progress {
  from {
    width: 0%;
  }
  to {
    width: 100%;
  }
}
```

#### JavaScript

ابتدا تابعی تعریف می‌کنیم که انیمیشن‌های مرتبط با یک عنصر و شبه‌عنصر مشخص را دریافت کند. این تابع `getAnimations()` را با گزینه [`pseudoElement`](#pseudoelement) فراخوانی می‌کند و اگر هیچ انیمیشنی برنگرداند، به فیلتر کردن انیمیشن‌های برگشتی از [`subtree`](#subtree) روی می‌آورد.

```js
function getAnimationsForPseudo(element, pseudo) {
  // Try the spec-compliant way first (Firefox)
  try {
    const anims = element.getAnimations({ pseudoElement: pseudo });
    // If it returned something, the option is supported, so return the result
    if (anims.length > 0) return anims;
  } catch (e) {
    // invalid selector etc
    return [];
  }

  // Fallback for browsers that only support subtree
  return element
    .getAnimations({ subtree: true })
    .filter((anim) => anim.effect?.pseudoElement === pseudo);
}
```

ما از این تابع برای دریافت تمام انیمیشن‌های مرتبط با شبه‌عنصر نوار پیشرفت استفاده می‌کنیم. کد روی انیمیشن‌ها پیمایش می‌کند تا آن‌ها را اجرا کند و سپس وقتی همه انیمیشن‌ها تمام شدند، نوار پیشرفت را حذف می‌کند. توجه داشته باشید که کد را در `requestAnimationFrame()` اجرا می‌کنیم تا مطمئن شویم انیمیشن قبل از اجرای جاوااسکریپت ما آماده است.

```js
const bar = document.getElementById("bar");

requestAnimationFrame(() => {
  const anims = getAnimationsForPseudo(bar, "::after");
  anims.forEach((a) => a.play());
  Promise.all(anims.map((a) => a.finished)).then(() => bar.remove());
});
```

```html hidden
<button id="reset" type="button">Restart</button>
```

```js hidden
const reload = document.querySelector("#reset");

reload.addEventListener("click", () => {
  window.location.reload(true);
});
```

#### نتیجه

نوار باید در عرض ظرف خود پیشروی کند و سپس ناپدید شود. می‌توانید با فشردن دکمه «Restart» آن را دوباره شروع کنید.

{{EmbedLiveSample("Get animations for a pseudo-element target", "100%", "50px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- [انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations)
- [ترنزیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Transitions)
- {{domxref("Document.getAnimations()")}} - دریافت همه انیمیشن‌های سند
- {{domxref("Animation")}}