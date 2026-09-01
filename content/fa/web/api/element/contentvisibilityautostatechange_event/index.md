---
title: "Element: رویداد contentvisibilityautostatechange"
short-title: contentvisibilityautostatechange
slug: Web/API/Element/contentvisibilityautostatechange_event
page-type: web-api-event
browser-compat: api.Element.contentvisibilityautostatechange_event
---

{{APIRef("CSS Containment")}}

رویداد **`contentvisibilityautostatechange`** روی هر عنصری که دارای ویژگی {{cssxref("content-visibility", "content-visibility: auto")}} باشد، زمانی که آن عنصر شروع به مرتبط بودن با کاربر یا توقف آن کند (و محتوایش را نادیده بگیرد) رخ می‌دهد. (مفاهیم [مرتبط با کاربر](/en-US/docs/Web/CSS/Guides/Containment/Using#relevant_to_the_user) و [نادیده گرفتن محتوا](/en-US/docs/Web/CSS/Guides/Containment/Using#skips_its_contents))

تا زمانی که عنصر مرتبط نباشد (بین رویدادهای شروع و پایان)، عامل کاربر (user agent) رندر عنصر شامل چیدمان و نقاشی را نادیده می‌گیرد که می‌تواند سرعت رندر صفحه را به طور قابل توجهی بهبود بخشد. رویداد `contentvisibilityautostatechange` راهی را فراهم می‌کند تا کد برنامه نیز بتواند فرآیندهای رندر را (مانند رسم روی یک {{htmlelement("canvas")}}) در صورت عدم نیاز شروع یا متوقف کند، در نتیجه توان پردازش را ذخیره کند.

توجه داشته باشید که حتی وقتی از دید پنهان است، محتوای عنصر همچنان از نظر معنایی مرتبط باقی می‌ماند (مثلاً برای کاربران فناوری‌های کمکی)، بنابراین این سیگنال نباید برای نادیده گرفتن به‌روزرسانی‌های معنایی مهم DOM استفاده شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("contentvisibilityautostatechange", (event) => { })

oncontentvisibilityautostatechange = (event) => { }
```

## نوع رویداد

یک {{domxref("ContentVisibilityAutoStateChangeEvent")}}.

## مثال‌ها

```js
const canvasElem = document.querySelector("canvas");

canvasElem.addEventListener("contentvisibilityautostatechange", stateChanged);
canvasElem.style.contentVisibility = "auto";

function stateChanged(event) {
  if (event.skipped) {
    stopCanvasUpdates(canvasElem);
  } else {
    startCanvasUpdates(canvasElem);
  }
}

// زمانی که نیاز به شروع به‌روزرسانی‌های canvas است، این تابع را فراخوانی کنید.
function startCanvasUpdates(canvas) {
  // …
}

// زمانی که نیاز به توقف به‌روزرسانی‌های canvas است، این تابع را فراخوانی کنید.
function stopCanvasUpdates(canvas) {
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ContentVisibilityAutoStateChangeEvent")}}
- [CSS Containment](/en-US/docs/Web/CSS/Guides/Containment)
- ویژگی {{cssxref("content-visibility")}}
- ویژگی {{cssxref("contain")}}