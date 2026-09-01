---
title: "EventTarget: removeEventListener() method"
short-title: removeEventListener()
slug: Web/API/EventTarget/removeEventListener
page-type: web-api-instance-method
browser-compat: api.EventTarget.removeEventListener
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

متد **`removeEventListener()`** در رابط {{domxref("EventTarget")}} یک شنوندهٔ رویداد (event listener) را که قبلاً با {{domxref("EventTarget.addEventListener()")}} روی هدف (target) ثبت شده است، حذف می‌کند. شنوندهٔ رویدادی که باید حذف شود، با ترکیبی از نوع رویداد، خودِ تابع شنوندهٔ رویداد، و گزینه‌های اختیاری مختلفی که ممکن است در فرایند تطبیق تأثیر داشته باشند، شناسایی می‌شود؛ همچنین به [تطبیق شنوندگان رویداد برای حذف](#matching_event_listeners_for_removal) مراجعه کنید.

فراخوانی `removeEventListener()` با آرگومان‌هایی که هیچ [شنوندهٔ رویداد](/en-US/docs/Web/API/EventTarget/addEventListener#the_event_listener_callback) ثبت‌شده‌ای را روی `EventTarget` شناسایی نمی‌کنند، هیچ اثری ندارد.

اگر یک [شنوندهٔ رویداد](/en-US/docs/Web/API/EventTarget/addEventListener#the_event_listener_callback) از یک {{domxref("EventTarget")}} حذف شود در حالی که شنوندهٔ دیگری از همان هدف در حال پردازش یک رویداد است، آن رویداد باعث فراخوانی این شنوندهٔ حذف‌شده نخواهد شد. با این حال، می‌توان آن را دوباره متصل کرد.

> [!WARNING]
> اگر یک شنونده دوبار ثبت شود، یک بار با پرچم _capture_ و یک بار بدون آن، باید هر کدام را جداگانه حذف کنید. حذف یک شنوندهٔ ضبط‌کننده (capturing listener) روی نسخهٔ غیر ضبط‌کنندهٔ همان شنونده تأثیری ندارد و بالعکس.

شنوندگان رویداد را می‌توان با ارسال یک {{domxref("AbortSignal")}} به {{domxref("EventTarget/addEventListener()", "addEventListener()")}} و سپس فراخوانی {{domxref("AbortController/abort()", "abort()")}} روی کنترلری که صاحب آن سیگنال است، نیز حذف کرد.

## نحو (Syntax)

```js-nolint
removeEventListener(type, listener)
removeEventListener(type, listener, options)
removeEventListener(type, listener, useCapture)
```

### پارامترها

- `type`
  - : رشته‌ای که نوع رویدادی را مشخص می‌کند که می‌خواهید شنوندهٔ رویداد آن را حذف کنید.
- `listener`
  - : تابع [شنوندهٔ رویداد](/en-US/docs/Web/API/EventTarget/addEventListener#the_event_listener_callback) مربوط به مدیریت‌کنندهٔ رویدادی که باید از هدف رویداد حذف شود.
- `options` {{optional_inline}}
  - : یک شیء گزینه که ویژگی‌های مربوط به شنوندهٔ رویداد را مشخص می‌کند.

    گزینه‌های موجود عبارت‌اند از:
    - `capture`: یک مقدار بولین که مشخص می‌کند آیا [شنوندهٔ رویداد](/en-US/docs/Web/API/EventTarget/addEventListener#the_event_listener_callback) موردنظر برای حذف، به‌عنوان یک شنوندهٔ ضبط‌کننده (capturing listener) ثبت شده است یا نه. اگر این پارامتر وجود نداشته باشد، مقدار پیش‌فرض `false` در نظر گرفته می‌شود.

- `useCapture` {{optional_inline}}
  - : یک مقدار بولین که مشخص می‌کند آیا [شنوندهٔ رویداد](/en-US/docs/Web/API/EventTarget/addEventListener#the_event_listener_callback) موردنظر برای حذف، به‌عنوان یک شنوندهٔ ضبط‌کننده ثبت شده است یا نه. اگر این پارامتر وجود نداشته باشد، مقدار پیش‌فرض `false` در نظر گرفته می‌شود.

### مقدار بازگشتی

هیچ‌کدام (None).

### تطبیق شنوندگان رویداد برای حذف

با توجه به یک شنوندهٔ رویداد که قبلاً با فراخوانی {{domxref("EventTarget.addEventListener", "addEventListener()")}} اضافه شده است، ممکن است در نهایت به نقطه‌ای برسید که باید آن را حذف کنید. واضح است که باید پارامترهای `type` و `listener` یکسانی را به `removeEventListener()` بدهید. اما در مورد پارامترهای `options` یا `useCapture` چطور؟

در حالی که `addEventListener()` به شما اجازه می‌دهد همان شنونده را برای همان نوع رویداد بیش از یک بار اضافه کنید (اگر گزینه‌ها متفاوت باشند)، تنها گزینه‌ای که `removeEventListener()` بررسی می‌کند پرچم `capture`/`useCapture` است. مقدار آن باید مطابقت داشته باشد تا `removeEventListener()` بتواند تطبیق را انجام دهد، اما سایر مقادیر مهم نیستند.

برای مثال، این فراخوانی `addEventListener()` را در نظر بگیرید:

```js
element.addEventListener("mousedown", handleMouseDown, true);
```

حالا هر یک از این دو فراخوانی `removeEventListener()` را در نظر بگیرید:

```js
element.removeEventListener("mousedown", handleMouseDown, false); // شکست می‌خورد
element.removeEventListener("mousedown", handleMouseDown, true); // موفق می‌شود
```

فراخوانی اول شکست می‌خورد، زیرا مقدار `useCapture` مطابقت ندارد. فراخوانی دوم موفق می‌شود، زیرا `useCapture` مطابقت دارد.

حال این مورد را در نظر بگیرید:

```js
element.addEventListener("mousedown", handleMouseDown, { passive: true });
```

در اینجا، یک شیء `options` مشخص کرده‌ایم که در آن `passive` برابر `true` است، در حالی که سایر گزینه‌ها با مقدار پیش‌فرض `false` رها شده‌اند.

حالا به ترتیب به هر یک از این فراخوانی‌های `removeEventListener()` نگاه کنید. هر کدام از آن‌ها که در آن `capture` یا `useCapture` برابر `true` باشد، شکست می‌خورد؛ بقیه موفق می‌شوند.

فقط تنظیم `capture` برای `removeEventListener()` اهمیت دارد.

```js
element.removeEventListener("mousedown", handleMouseDown, { passive: true }); // موفق
element.removeEventListener("mousedown", handleMouseDown, { capture: false }); // موفق
element.removeEventListener("mousedown", handleMouseDown, { capture: true }); // شکست
element.removeEventListener("mousedown", handleMouseDown, { passive: false }); // موفق
element.removeEventListener("mousedown", handleMouseDown, false); // موفق
element.removeEventListener("mousedown", handleMouseDown, true); // شکست
```

شایان ذکر است که برخی از نسخه‌های مرورگر در این زمینه رفتاری ناسازگار داشته‌اند، و اگر دلیل خاصی برای خلاف این ندارید، احتمالاً عاقلانه است که هنگام فراخوانی `removeEventListener()` از همان مقادیری استفاده کنید که در فراخوانی `addEventListener()` به کار رفته‌اند.

## مثال

این مثال نشان می‌دهد که چگونه یک شنوندهٔ رویداد مبتنی بر `mouseover` اضافه کنیم که یک شنوندهٔ رویداد مبتنی بر `click` را حذف می‌کند.

```js
const body = document.querySelector("body");
const clickTarget = document.getElementById("click-target");
const mouseOverTarget = document.getElementById("mouse-over-target");

let toggle = false;
function makeBackgroundYellow() {
  body.style.backgroundColor = toggle ? "white" : "yellow";

  toggle = !toggle;
}

clickTarget.addEventListener("click", makeBackgroundYellow);

mouseOverTarget.addEventListener("mouseover", () => {
  clickTarget.removeEventListener("click", makeBackgroundYellow);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("EventTarget.addEventListener()")}}