---
title: "ContentVisibilityAutoStateChangeEvent"
---

---
title: ContentVisibilityAutoStateChangeEvent
slug: Web/API/ContentVisibilityAutoStateChangeEvent
page-type: web-api-interface
browser-compat: api.ContentVisibilityAutoStateChangeEvent
---

{{APIRef("CSS Containment")}}

رابط **`ContentVisibilityAutoStateChangeEvent`**، شیء رویداد برای رویداد {{domxref("element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}} است. این رویداد روی هر عنصری که دارای ویژگی {{cssxref("content-visibility", "content-visibility: auto")}} باشد، هنگامی که [مرتبط بودن برای کاربر](/en-US/docs/Web/CSS/Guides/Containment/Using#relevant_to_the_user) یا [رد شدن از محتویات آن](/en-US/docs/Web/CSS/Guides/Containment/Using#skips_its_contents) برای عنصر شروع یا متوقف می‌شود، فعال می‌گردد.

هنگامی که عنصر مرتبط نیست (بین رویدادهای شروع و پایان)، عامل کاربر رندر آن عنصر، از جمله چیدمان و نقاشی را رد می‌کند. این کار می‌تواند سرعت رندر صفحه را به‌طور قابل توجهی بهبود بخشد. رویداد {{domxref("element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}} راهی در اختیار کد برنامه قرار می‌دهد تا فرآیندهای رندر (مثلاً رسم روی {{htmlelement("canvas")}}) را نیز در زمانی که نیازی به آن‌ها نیست شروع یا متوقف کند و در نتیجه توان پردازشی را حفظ نماید.

توجه داشته باشید که حتی وقتی از دید پنهان است، محتویات عنصر از نظر معنایی مرتبط باقی می‌مانند (مثلاً برای کاربران فناوری کمکی)، بنابراین این سیگنال نباید برای رد کردن به‌روزرسانی‌های معنایی مهم DOM استفاده شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("ContentVisibilityAutoStateChangeEvent.ContentVisibilityAutoStateChangeEvent", "ContentVisibilityAutoStateChangeEvent()")}}
  - یک نمونه شیء جدید از `ContentVisibilityAutoStateChangeEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{DOMxRef("Event")}} را به ارث می‌برد._

- {{domxref("ContentVisibilityAutoStateChangeEvent.skipped", "skipped")}} {{ReadOnlyInline}}
  - اگر عامل کاربر رندر عنصر را رد کند، `true` و در غیر این صورت `false` برمی‌گرداند.

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

// Call this when the canvas updates need to start.
function startCanvasUpdates(canvas) {
  // …
}

// Call this when the canvas updates need to stop.
function stopCanvasUpdates(canvas) {
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}}
- [CSS Containment](/en-US/docs/Web/CSS/Guides/Containment)
- ویژگی {{cssxref("content-visibility")}}
- ویژگی {{cssxref("contain")}}