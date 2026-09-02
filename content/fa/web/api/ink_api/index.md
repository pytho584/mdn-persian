---
title: Ink API
slug: Web/API/Ink_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.Ink
---

{{DefaultAPISidebar("Ink API")}}{{SeeCompatTable}}

API Ink به مرورگرها امکان می‌دهد هنگام رسم ضربه‌های قلم در یکی از قابلیت‌های نقاشی برنامه، مستقیماً از کامپوزیتورهای موجود در سطح سیستم‌عامل استفاده کنند؛ این کار تأخیر را کاهش داده و کارایی را افزایش می‌دهد.

## مفاهیم و کاربرد

نقاشی با جوهر روی وب به ویژگی‌هایی در برنامه‌ها اشاره دارد که از رویدادهای اشاره‌گر برای کشیدن ضربه‌های قلم نرم استفاده می‌کنند؛ برای مثال، یک برنامه طراحی یا قابلیت امضای سند.

رویدادهای اشاره‌گر معمولاً ابتدا به فرایند مرورگر ارسال می‌شوند و سپس مرورگر این رویدادها را به حلقه رویداد جاوااسکریپت ارسال می‌کند تا توابع کنترل‌کننده مرتبط اجرا شده و نتیجه در برنامه رندر شود. تأخیر زمانی بین شروع و پایان این فرایند می‌تواند قابل توجه باشد و در نتیجه بین شروع کشیدن توسط کاربر (مثلاً با قلم دیجیتال یا ماوس) و ظاهر شدن ضربه قلم روی صفحه، تأخیر ایجاد شود.

API Ink این تأخیر را به‌طور قابل توجهی کاهش می‌دهد و به مرورگرها اجازه می‌دهد حلقه رویداد جاوااسکریپت را کاملاً دور بزنند. در صورت امکان، مرورگرها چنین دستورالعمل‌های رندر را مستقیماً به کامپوزیتورهای سطح سیستم‌عامل ارسال می‌کنند. اگر سیستم‌عامل زیرین، کامپوزیتور تخصصی در سطح سیستم‌عامل برای این منظور نداشته باشد، مرورگرها از کد رندر بهینه‌سازی‌شده خودشان استفاده می‌کنند. این کد به اندازه یک کامپوزیتور قدرتمند نیست، اما همچنان بهبودهایی را به همراه دارد.

> [!NOTE]
> کامپوزیتورها بخشی از سازوکار رندر هستند که رابط کاربری را در مرورگر یا سیستم‌عامل روی صفحه ترسیم می‌کنند. برای آشنایی با نحوه عملکرد کامپوزیتور در داخل یک مرورگر وب، مقاله [نگاهی به درون مرورگر مدرن (بخش ۳)](https://developer.chrome.com/blog/inside-browser-part3/) را ببینید.

نقطه ورود، ویژگی {{domxref("Navigator.ink")}} است که یک شیء {{domxref("Ink")}} را برای سند جاری برمی‌گرداند. متد {{domxref("Ink.requestPresenter","Ink.requestPresenter()")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک نمونه از شیء {{domxref("DelegatedInkTrailPresenter")}} تکمیل می‌شود. این شیء به کامپوزیتور سطح سیستم‌عامل دستور می‌دهد تا ضربه‌های قلم را بین ارسال رویدادهای اشاره‌گر در اولین فریم موجود بعدی رندر کند.

## رابط‌ها

- {{domxref("Ink")}} {{Experimental_Inline}}
  - : دسترسی به اشیاء {{domxref("DelegatedInkTrailPresenter")}} را برای برنامه فراهم می‌کند تا از آن‌ها برای رندر کردن ضربه‌ها استفاده کند.
- {{domxref("DelegatedInkTrailPresenter")}} {{Experimental_Inline}}
  - : به کامپوزیتور سطح سیستم‌عامل دستور می‌دهد تا ضربه‌های قلم را بین ارسال رویدادهای اشاره‌گر رندر کند.

### افزونه‌های رابط‌های دیگر

- {{domxref("Navigator.ink")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("Ink")}} را برای سند جاری برمی‌گرداند.

## مثال‌ها

### رسم یک رد قلم

در این مثال، یک رد قلم را روی بوم (Canvas) دوبعدی رسم می‌کنیم. در نزدیکی ابتدای کد، {{domxref("Ink.requestPresenter()")}} را فراخوانی می‌کنیم و بوم را به عنوان ناحیه نمایش به آن می‌دهیم تا مدیریت آن را بر عهده بگیرد؛ پرامیس بازگشتی را در متغیر `presenter` ذخیره می‌کنیم.

بعداً، در شنونده رویداد `pointermove`، هر بار که رویداد رخ می‌دهد، موقعیت جدید نقطه شروع رد روی بوم رسم می‌شود. علاوه بر این، متد {{domxref("DelegatedInkTrailPresenter.updateInkTrailStartPoint", "updateInkTrailStartPoint()")}} روی شیء {{domxref("DelegatedInkTrailPresenter")}}ای که پس از تکمیل پرامیس `presenter` به دست می‌آید، فراخوانی می‌شود. به این متد موارد زیر ارسال می‌گردد:

- آخرین رویداد اشاره‌گر معتبر (trusted) که نقطه رندر را برای فریم جاری نشان می‌دهد.
- یک شیء `style` شامل تنظیمات رنگ و قطر.

نتیجه این می‌شود که یک رد جوهر تفویض‌شده، به نمایندگی از برنامه و با سبک مشخص‌شده، جلوتر از رندر پیش‌فرض مرورگر رسم می‌شود و تا دریافت رویداد `pointermove` بعدی ادامه می‌یابد.

#### HTML

```html
<canvas id="canvas"></canvas>
<div id="div">Delegated ink trail should match the color of this div.</div>
```

#### CSS

```css
div {
  background-color: lime;
  position: fixed;
  top: 1rem;
  left: 1rem;
}
```

#### JavaScript

```js
const ctx = canvas.getContext("2d");
const presenter = navigator.ink.requestPresenter({ presentationArea: canvas });
let moveCnt = 0;
let style = { color: "lime", diameter: 10 };

function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

canvas.addEventListener("pointermove", async (evt) => {
  const pointSize = 10;
  ctx.fillStyle = style.color;
  ctx.fillRect(evt.pageX, evt.pageY, pointSize, pointSize);
  if (moveCnt === 20) {
    const r = getRandomInt(0, 255);
    const g = getRandomInt(0, 255);
    const b = getRandomInt(0, 255);

    style = { color: `rgb(${r} ${g} ${b} / 100%)`, diameter: 10 };
    moveCnt = 0;
    document.getElementById("div").style.backgroundColor =
      `rgb(${r} ${g} ${b} / 60%)`;
  }
  moveCnt += 1;
  (await presenter).updateInkTrailStartPoint(evt, style);
});

window.addEventListener("pointerdown", () => {
  ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height);
});

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
```

#### نتیجه

{{EmbedLiveSample("Drawing an ink trail")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}