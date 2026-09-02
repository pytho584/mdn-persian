---
title: "IntersectionObserver: observe() method"
short-title: observe()
slug: Web/API/IntersectionObserver/observe
page-type: web-api-instance-method
browser-compat: api.IntersectionObserver.observe
---

{{APIRef("Intersection Observer API")}}

متد **`observe()`** از رابط {{domxref("IntersectionObserver")}} یک عنصر را به مجموعهٔ عناصر هدفی اضافه می‌کند که توسط `IntersectionObserver` تحت نظارت قرار دارند.
هر observer دارای یک مجموعه آستانه (threshold) و یک ریشه (root) است، اما می‌تواند چندین عنصر هدف را برای تغییرات دید مطابق با آن‌ها نظارت کند.

برای توقف مشاهدهٔ عنصر، متد {{domxref("IntersectionObserver.unobserve()")}} را فراخوانی کنید.

هنگامی که دید عنصر مشخص‌شده از یکی از آستانه‌های دید observer عبور کند (همان‌طور که در {{domxref("IntersectionObserver.thresholds")}} فهرست شده است)، تابع callback مربوط به observer با آرایه‌ای از اشیاء {{domxref("IntersectionObserverEntry")}} اجرا می‌شود که تغییرات تقاطع رخ‌داده را نشان می‌دهند.
توجه داشته باشید که این طراحی امکان می‌دهد تغییرات تقاطع چندین عنصر در یک فراخوانی واحد از تابع callback پردازش شوند.

> [!NOTE]
> تابع [callback](/en-US/docs/Web/API/IntersectionObserver/IntersectionObserver#callback) مربوط به observer همیشه در اولین چرخهٔ رندر پس از فراخوانی `observe()` اجرا می‌شود، حتی اگر عنصر مشاهده‌شده هنوز نسبت به viewport جابه‌جا نشده باشد.
> این بدان معناست که، برای مثال، اگر عنصری هنگام فراخوانی `observe()` روی آن خارج از viewport باشد، تابع callback بلافاصله با حداقل یک [ورودی](/en-US/docs/Web/API/IntersectionObserverEntry) که [`intersecting`](/en-US/docs/Web/API/IntersectionObserverEntry/isIntersecting) آن روی `false` تنظیم شده است فراخوانی می‌شود.
> عنصری که داخل viewport باشد باعث می‌شود تابع callback بلافاصله با حداقل یک ورودی که `intersecting` آن روی `true` تنظیم شده است فراخوانی شود.

## Syntax

```js-nolint
observe(targetElement)
```

### Parameters

- `targetElement`
  - : یک {{domxref("element")}} که دید آن در داخل ریشه باید نظارت شود.
    این عنصر باید از نوادگان عنصر ریشه باشد (یا در داخل سند جاری قرار داشته باشد، اگر ریشه، viewport سند باشد).
    اگر این عنصر از قبل در حال مشاهده باشد، این متد هیچ کاری انجام نمی‌دهد.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

```js
// Register IntersectionObserver
const io = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.intersectionRatio > 0) {
      // Add 'active' class if observation target is inside viewport
      entry.target.classList.add("active");
    } else {
      // Remove 'active' class otherwise
      entry.target.classList.remove("active");
    }
  });
});

// Declares what to observe, and observes its properties.
const boxElList = document.querySelectorAll(".box");
boxElList.forEach((el) => {
  io.observe(el);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("IntersectionObserver.unobserve()")}}