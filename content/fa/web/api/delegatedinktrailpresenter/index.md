---
title: DelegatedInkTrailPresenter
slug: Web/API/DelegatedInkTrailPresenter
page-type: web-api-interface
status:
  - experimental
browser-compat: api.DelegatedInkTrailPresenter
---

{{APIRef("Ink API")}}{{SeeCompatTable}}

رابط **`DelegatedInkTrailPresenter`** از [Ink API](/en-US/docs/Web/API/Ink_API) قابلیت دستور به کامپوزیتور سطح سیستم‌عامل برای رندر کردن خطوط جوهر بین ارسال‌های رویداد اشاره‌گر را فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("DelegatedInkTrailPresenter.expectedImprovement", "expectedImprovement")}} {{Deprecated_Inline}} {{Non-standard_Inline}} {{ReadOnlyInline}}
  - : مقداری را بر حسب میلی‌ثانیه برمی‌گرداند که نشان‌دهنده بهبود تأخیر قابل انتظار با استفاده از این ارائه‌دهنده است.
- {{domxref("DelegatedInkTrailPresenter.presentationArea", "presentationArea")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : {{domxref("Element")}}ای را برمی‌گرداند که رندر کردن خطوط جوهر درون آن محدود شده است.

## روش‌های نمونه

- {{domxref("DelegatedInkTrailPresenter.updateInkTrailStartPoint", "updateInkTrailStartPoint()")}} {{Experimental_Inline}}
  - : {{domxref("PointerEvent")}}ای را که به عنوان آخرین نقطه رندر برای فریم فعلی استفاده شده است، ارسال می‌کند و به کامپوزیتور سطح سیستم‌عامل اجازه می‌دهد یک رد جوهر تفویض‌شده را جلوتر از ارسال رویداد اشاره‌گر بعدی رندر کند.

## مثال

در این مثال، یک رد روی بوم دوبعدی رسم می‌کنیم. در نزدیکی شروع کد، {{domxref("Ink.requestPresenter()")}} را فراخوانی می‌کنیم، بوم را به عنوان منطقه ارائه برای آن ارسال می‌کنیم و پرامیسی که برمی‌گرداند را در متغیر `presenter` ذخیره می‌کنیم.

بعداً، در شنونده رویداد `pointermove`، موقعیت جدید سر رد هر بار که رویداد رخ می‌دهد روی بوم رسم می‌شود. علاوه بر این، شیء `DelegatedInkTrailPresenter` که وقتی پرامیس `presenter` fulfilled می‌شود برگردانده می‌شود، متد {{domxref("DelegatedInkTrailPresenter.updateInkTrailStartPoint", "updateInkTrailStartPoint()")}} آن فراخوانی می‌شود؛ این متد ارسال می‌کند:

- آخرین رویداد اشاره‌گر معتبر که نقطه رندر برای فریم جاری را نشان می‌دهد.
- یک شیء `style` شامل تنظیمات رنگ و قطر.

نتیجه این است که یک رد جوهر تفویض‌شده جلوتر از رندر پیش‌فرض مرورگر به نمایندگی از برنامه، با سبک مشخص‌شده، تا زمانی که رویداد `pointermove` بعدی دریافت شود، رسم می‌شود.

```js
const ctx = canvas.getContext("2d");
let presenter = navigator.ink.requestPresenter({ presentationArea: canvas });
let moveCnt = 0;
let style = { color: "rgb(0 0 255 / 100%)", diameter: 10 };

function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

canvas.addEventListener("pointermove", (evt) => {
  const pointSize = 10;
  ctx.fillStyle = "black";
  ctx.fillRect(evt.pageX, evt.pageY, pointSize, pointSize);
  if (moveCnt === 50) {
    let r = getRandomInt(0, 255);
    let g = getRandomInt(0, 255);
    let b = getRandomInt(0, 255);
    style = {
      color: `rgb(${r} ${g} ${b} / 100%)`,
      diameter: 10,
    };
    moveCnt = 0;
    document.getElementById("div").style.backgroundColor =
      `rgb(${r} ${g} ${b} / 100%)`;
  }
  moveCnt += 1;
  presenter.then((v) => {
    v.updateInkTrailStartPoint(evt, style);
  });
});

window.addEventListener("pointerdown", (evt) => {
  evt.pointerId;
  ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height);
});

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
```

> [!NOTE]
> این مثال را به صورت زنده ببینید — [رد جوهر تفویض‌شده](https://mabian-ms.github.io/delegated-ink-trail.html).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}