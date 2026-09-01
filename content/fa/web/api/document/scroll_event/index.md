---
title: "Document: scroll event"
short-title: scroll
slug: Web/API/Document/scroll_event
page-type: web-api-event
browser-compat: api.Document.scroll_event
---

{{APIRef("CSSOM view API")}}

رویداد **`scroll`** زمانی رخ می‌دهد که نمای سند (document view) پیمایش (scroll) شده باشد. برای تشخیص پایان پیمایش، به رویداد {{domxref("Document/scrollend_event", "scrollend")}} در `Document` مراجعه کنید. برای پیمایش عناصر، به رویداد {{domxref("Element/scroll_event", "scroll")}} در `Element` مراجعه کنید.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("scroll", (event) => { })

onscroll = (event) => { }
```

## نوع رویداد (Event type)

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### محدودسازی نرخ رویداد (Throttling) scroll

از آنجا که رویدادهای `scroll` می‌توانند با نرخ بالایی رخ دهند، کنترل‌کننده رویداد نباید عملیات‌های محاسباتی سنگین مانند تغییرات DOM را اجرا کند. اگر هنگام پیمایش سریع متوجه {{glossary("jank", "لرزش (jank)")}} شدید، باید محدودسازی نرخ ({{glossary("throttle", "throttling")}}) رویداد را در نظر بگیرید.

توجه داشته باشید که ممکن است کدی ببینید که کنترل‌کننده رویداد `scroll` را با استفاده از {{domxref("Window.requestAnimationFrame()", "requestAnimationFrame()")}} محدود می‌کند. این کار _بی‌فایده_ است زیرا فراخوانی‌های فریم انیمیشن با همان نرخ کنترل‌کننده‌های رویداد `scroll` اجرا می‌شوند. در عوض، باید خودتان زمان‌بندی (timeout) را اندازه‌گیری کنید، مثلاً با استفاده از {{domxref("Window.setTimeout", "setTimeout()")}}.

```js
let lastKnownScrollPosition = 0;
let ticking = false;

function doSomething(scrollPos) {
  // با موقعیت پیمایش کاری انجام دهید
}

document.addEventListener("scroll", (event) => {
  lastKnownScrollPosition = window.scrollY;

  if (!ticking) {
    // رویداد را محدود کنید تا هر ۲۰ میلی‌ثانیه "کاری انجام دهد"
    setTimeout(() => {
      doSomething(lastKnownScrollPosition);
      ticking = false;
    }, 20);

    ticking = true;
  }
});
```

به‌عنوان جایگزین، استفاده از {{domxref("IntersectionObserver")}} را در نظر بگیرید که امکان شنود مبتنی بر آستانه (threshold) را فراهم می‌کند.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [Document: رویداد `scrollend`](/en-US/docs/Web/API/Document/scrollend_event)
- [Element: رویداد `scroll`](/en-US/docs/Web/API/Element/scroll_event)
- [Element: رویداد `scrollend`](/en-US/docs/Web/API/Element/scrollend_event)