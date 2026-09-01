---
title: "Element: requestPointerLock() method"
short-title: requestPointerLock()
slug: Web/API/Element/requestPointerLock
page-type: web-api-instance-method
browser-compat: api.Element.requestPointerLock
---

{{APIRef("Pointer Lock API")}}

متد **`requestPointerLock()`** از رابط {{domxref("Element")}} به شما اجازه می‌دهد تا به‌صورت ناهمزمان (asynchronous) درخواست قفل شدن اشاره‌گر (pointer) روی عنصر مشخص‌شده را بدهید.

برای پیگیری موفقیت یا شکست درخواست، لازم است به رویدادهای {{domxref("Document/pointerlockchange_event", "pointerlockchange")}} و {{domxref("Document/pointerlockerror_event", "pointerlockerror")}} در سطح {{domxref("Document")}} گوش دهید.

> [!NOTE]
> در مشخصات فعلی، `requestPointerLock()` موفقیت یا شکست درخواست را فقط با فرستادن رویدادهای {{domxref("Document/pointerlockchange_event", "pointerlockchange")}} یا {{domxref("Document/pointerlockerror_event", "pointerlockerror")}} اعلام می‌کند. [یک به‌روزرسانی پیشنهادی برای مشخصات](https://github.com/w3c/pointerlock/pull/49) `requestPointerLock()` را طوری تغییر می‌دهد که یک {{jsxref("Promise")}} برگرداند که موفقیت یا شکست را اعلام کند. این صفحه نسخه‌ای را مستند می‌کند که {{jsxref("Promise")}} برمی‌گرداند. اما توجه داشته باشید که این نسخه هنوز استاندارد نیست و در همه مرورگرها پیاده‌سازی نشده است. برای اطلاعات بیشتر به بخش [سازگاری با مرورگرها](#browser_compatibility) مراجعه کنید.

## نحو (Syntax)

```js-nolint
requestPointerLock()
requestPointerLock(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که می‌تواند شامل ویژگی‌های زیر باشد:
    - `unadjustedMovement` {{optional_inline}}
      - : تنظیمات سطح سیستم‌عامل برای شتاب موس (mouse acceleration) را غیرفعال کرده و به‌جای آن از ورودی خام موس استفاده می‌کند. مقدار پیش‌فرض `false` است؛ تنظیم آن به `true` شتاب موس را غیرفعال می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود.

## امنیت

{{Glossary("Transient activation", "فعال‌سازی موقت (Transient activation)")}} هنگام فراخوانی `requestPointerLock()` الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل داشته باشد تا این ویژگی کار کند. همچنین، سند مرتبط با عنصر هدف باید در حالت فعال (active state) باشد.

اگر `requestPointerLock()` بلافاصله پس از آزاد کردن قفل اشاره‌گر از طریق ژست پیش‌فرض باز کردن قفل (به‌جای فراخوانی `exitPointerLock()`) فراخوانی شود، این فراخوانی حتی اگر {{Glossary("transient activation")}} در دسترس باشد، با شکست مواجه خواهد شد.

اگر `requestPointerLock()` همراه با {{domxref("Element.requestFullscreen()", "requestFullscreen()")}} فراخوانی شود، ابتدا باید `requestPointerLock()` را فراخوانی کنید، زیرا {{domxref("Element.requestFullscreen()", "requestFullscreen()")}} وضعیت {{Glossary("Transient activation", "فعال‌سازی موقت")}} را مصرف می‌کند.

هنگام فراخوانی `requestPointerLock()` در یک عنصر {{htmlelement("iframe")}}، باید توکن [sandbox](/en-US/docs/Web/HTML/Reference/Elements/iframe#sandbox) `allow-pointer-lock` اضافه شود. همچنین، هیچ عنصر دیگری در عناصر {{htmlelement("iframe")}} دیگر نباید در حالت قفل اشاره‌گر باشد.

## مثال‌ها

قفل اشاره‌گر اغلب در بازی‌های آنلاین استفاده می‌شود، زمانی که می‌خواهید حرکت موس شما روی کنترل بازی متمرکز باشد، بدون اینکه اشاره‌گر موس در اطراف حرکت کند، از ناحیه بازی خارج شود یا به لبه پنجره برسد.

برای فعال کردن قفل اشاره‌گر، باید کاربر را به نحوی با رابط کاربری تعامل دهد، مثلاً با فشار دادن یک دکمه یا خود بوم (canvas) بازی.

```js
canvas.addEventListener("click", async () => {
  await canvas.requestPointerLock();
});
```

سیستم‌عامل‌ها به‌طور پیش‌فرض شتاب موس را فعال می‌کنند که در مواقعی که حرکت دقیق و آهسته می‌خواهید (مثلاً در نرم‌افزارهای گرافیکی) و همچنین حرکت سریع برای مسافت‌های طولانی (مثل اسکرول کردن یا انتخاب چندین فایل) مفید است. اما برای برخی بازی‌های اول شخص، داده‌های خام موس برای کنترل چرخش دوربین ترجیح داده می‌شود؛ جایی که حرکت با فاصله یکسان، چه سریع و چه آهسته، باعث چرخش یکسان می‌شود. این کار طبق نظر گیمرهای حرفه‌ای تجربه بازی بهتری و دقت بالاتری را به همراه دارد.

برای غیرفعال کردن شتاب موس در سطح سیستم‌عامل و دسترسی به ورودی خام موس، می‌توانید `unadjustedMovement` را روی `true` تنظیم کنید:

```js
canvas.addEventListener("click", async () => {
  await canvas.requestPointerLock({
    unadjustedMovement: true,
  });
});
```

برای مثال‌های کد بیشتر، به موارد زیر مراجعه کنید:

- [نمونه قفل اشاره‌گر](https://mdn.github.io/dom-examples/pointer-lock/) ([مشاهده کد منبع](https://github.com/mdn/dom-examples/tree/main/pointer-lock))
- {{domxref("Pointer Lock API", "Pointer Lock API", "", "nocode")}}
- [غیرفعال کردن شتاب موس برای تجربه بهتر بازی FPS](https://web.dev/articles/disable-mouse-acceleration)

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{ domxref("Document.pointerLockElement") }}
- {{ domxref("Document.exitPointerLock()") }}
- [قفل اشاره‌گر (Pointer Lock)](/en-US/docs/Web/API/Pointer_Lock_API)