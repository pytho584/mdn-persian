---
title: "Element: animate() method"
---

---
title: "Element: animate() method"
short-title: animate()
slug: Web/API/Element/animate
page-type: web-api-instance-method
browser-compat: api.Element.animate
---

{{APIRef("Web Animations")}}

متد **`animate()`** در رابط {{domxref("Element")}} یک روش میانبر است که یک {{domxref("Animation")}} جدید ایجاد می‌کند، آن را روی عنصر اعمال می‌کند و سپس انیمیشن را اجرا می‌کند. این متد نمونه شی {{domxref("Animation")}} ایجادشده را بازمی‌گرداند.

> [!NOTE]
> عناصر می‌توانند چندین انیمیشن روی آن‌ها اعمال شود. برای دریافت فهرست انیمیشن‌هایی که روی یک عنصر اثر می‌گذارند، می‌توانید با {{domxref("Element.getAnimations()")}} تماس بگیرید.

## نحو (Syntax)

```js-nolint
animate(keyframes, options)
```

### پارامترها

- `keyframes`
  - : یا آرایه‌ای از اشیاء keyframe، **یا** شیء keyframe که خصوصیات آن آرایه‌هایی از مقادیر برای پیمایش هستند. برای جزئیات بیشتر به [قالب‌های Keyframe](/en-US/docs/Web/API/Web_Animations_API/Keyframe_Formats) مراجعه کنید.
- `options`
  - : یا یک **عدد صحیح که نشان‌دهنده مدت زمان انیمیشن** (بر حسب میلی‌ثانیه) است، **یا** یک شیء شامل یک یا چند ویژگی زمان‌بندی که در [پارامتر options مربوط به `KeyframeEffect()`](/en-US/docs/Web/API/KeyframeEffect/KeyframeEffect#parameters) توضیح داده شده است و/یا گزینه‌های زیر:

    - `id` {{optional_inline}}
      - : ویژگی‌ای مختص `animate()`: رشته‌ای که برای ارجاع به انیمیشن استفاده می‌شود.
    - `rangeEnd` {{optional_inline}}
      - : پایان محدوده اتصال انیمیشن را در طول خط زمانی آن مشخص می‌کند، یعنی جایی در طول خط زمانی که انیمیشن در آن به پایان می‌رسد. معادل جاوااسکریپتی ویژگی CSS {{cssxref("animation-range-end")}}. `rangeEnd` می‌تواند انواع مختلفی از مقادیر را بپذیرد، به شرح زیر:
        - یک رشته که می‌تواند `normal` باشد (به این معنی که تغییری در محدوده اتصال انیمیشن ایجاد نمی‌شود)، یک {{cssxref("length-percentage")}} CSS که یک آفست را نشان می‌دهد، یک `<timeline-range-name>`، یا یک `<timeline-range-name>` به‌همراه یک `<length-percentage>` که پس از آن می‌آید. برای مثال: `"normal"`، `"entry"` یا `"cover 100%"`.

          برای توضیح دقیق مقادیر موجود، به {{cssxref("animation-range")}} مراجعه کنید. همچنین [تجسم‌گر محدوده‌های خط زمانی](https://scroll-driven-animations.style/tools/view-timeline/ranges/) را ببینید که دقیقاً نشان می‌دهد مقادیر مختلف در قالبی بصری و آسان چه معنایی دارند.
        - یک شیء حاوی خصوصیات `rangeName` (یک رشته) و `offset` (یک {{domxref("CSSNumericValue")}}) که یک `<timeline-range-name>` و یک `<length-percentage>` را نشان می‌دهند، همانطور که در مورد قبلی توضیح داده شد. برای مثال: `{ rangeName: "entry", offset: CSS.percent("100") }`.
        - یک {{domxref("CSSNumericValue")}} که یک آفست را نشان می‌دهد، برای مثال: `CSS.percent("100")`.
    - `rangeStart` {{optional_inline}}
      - : شروع محدوده اتصال انیمیشن را در طول خط زمانی آن مشخص می‌کند، یعنی جایی در طول خط زمانی که انیمیشن در آن شروع می‌شود. معادل جاوااسکریپتی ویژگی CSS {{cssxref("animation-range-start")}}. `rangeStart` می‌تواند همان انواع مقادیری را بپذیرد که `rangeEnd` می‌پذیرد.
    - `timeline` {{optional_inline}}
      - : ویژگی‌ای مختص `animate()`: {{domxref("AnimationTimeline")}} که باید با انیمیشن مرتبط شود. به‌طور پیش‌فرض {{domxref("Document.timeline")}} است. معادل جاوااسکریپتی ویژگی CSS {{cssxref("animation-timeline")}}.

### مقدار بازگشتی

یک {{domxref("Animation")}} بازمی‌گرداند.

## مثال‌ها

### چرخش و تغییر مقیاس

در این مثال از متد `animate()` برای چرخش و تغییر مقیاس یک عنصر استفاده می‌کنیم.

#### HTML

```html
<div class="newspaper">Spinning newspaper<br />causes dizziness</div>
```

#### CSS

```css
html,
body {
  height: 100%;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: black;
}

.newspaper {
  padding: 0.5rem;
  text-transform: uppercase;
  text-align: center;
  background-color: white;
  cursor: pointer;
}
```

#### JavaScript

```js
const newspaperSpinning = [
  { transform: "rotate(0) scale(1)" },
  { transform: "rotate(360deg) scale(0)" },
];

const newspaperTiming = {
  duration: 2000,
  iterations: 1,
};

const newspaper = document.querySelector(".newspaper");

newspaper.addEventListener("click", () => {
  newspaper.animate(newspaperSpinning, newspaperTiming);
});
```

#### نتیجه

{{EmbedLiveSample("Rotating and scaling")}}

### دموی Down the Rabbit Hole

در دموی [Down the Rabbit Hole (با Web Animation API)](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#moving_it_to_javascript)، از متد راحت `animate()` استفاده می‌کنیم تا بلافاصله یک انیمیشن روی عنصر `#tunnel` ایجاد و اجرا کنیم تا آن را به‌طور نامحدود به سمت بالا جاری کند. به آرایه اشیاء ارسال‌شده به‌عنوان keyframe و همچنین بلوک گزینه‌های زمان‌بندی توجه کنید.

```js
document.getElementById("tunnel").animate(
  [
    // keyframes
    { transform: "translateY(0px)" },
    { transform: "translateY(-300px)" },
  ],
  {
    // timing options
    duration: 1000,
    iterations: Infinity,
  },
);
```

### کیفریم‌های ضمنی از/به

مرورگر می‌تواند حالت شروع یا پایان انیمیشن را با استفاده از حالت فعلی استنتاج کند. به‌طور پیش‌فرض، اگر یک keyframe واحد ارائه شود، به‌عنوان حالت پایان در نظر گرفته می‌شود و حالت شروع از سبک محاسبه‌شده فعلی عنصر استنتاج می‌شود. با این حال، می‌توانید `offset` را برای مشخص کردن اینکه keyframe ارائه‌شده در کجای خط زمانی انیمیشن قرار گیرد، تعیین کنید.

```html hidden
<div>
  <img
    id="logo"
    src="/shared-assets/images/examples/firefox-logo.svg"
    alt="Firefox logo" />
</div>
<button id="run">Animate - use current as start</button>
<button id="run2">Animate - use current as end</button>
<button id="run3">Animate - use current as both ends</button>
```

```css hidden
div {
  width: 100%;
}

#logo {
  width: 200px;
  height: 200px;
}
```

```js
const logo = document.getElementById("logo");
document.getElementById("run").addEventListener("click", () => {
  logo.animate({ transform: "translateX(300px)" }, 1000);
});
document.getElementById("run2").addEventListener("click", () => {
  logo.animate({ transform: "translateX(300px)", offset: 0 }, 1000);
});
document.getElementById("run3").addEventListener("click", () => {
  logo.animate({ transform: "translateX(300px)", offset: 0.5 }, 1000);
});
```

ما یک فریم واحد در خط زمانی مشخص کرده‌ایم و حالت‌های شروع و/یا پایان می‌توانند پر شوند تا یک انیمیشن کامل ایجاد شود.

{{EmbedLiveSample("Implicit to/from keyframes", "", 300)}}

### timeline، rangeStart و rangeEnd

استفاده معمول از ویژگی‌های `timeline`، `rangeStart` و `rangeEnd` ممکن است به این شکل باشد:

```js
const img = document.querySelector("img");

const timeline = new ViewTimeline({
  subject: img,
  axis: "block",
});

img.animate(
  {
    opacity: [0, 1],
    transform: ["scaleX(0)", "scaleX(1)"],
  },
  {
    fill: "both",
    duration: 1,
    timeline,
    rangeStart: "cover 0%",
    rangeEnd: "cover 100%",
  },
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Animation")}}
- {{domxref("Element.getAnimations()")}}
- {{cssxref("animation-range-end")}}، {{cssxref("animation-range-start")}}، {{cssxref("animation-timeline")}}
- [انیمیشن‌های مبتنی بر اسکرول CSS](/en-US/docs/Web/CSS/Guides/Scroll-driven_animations)
- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)