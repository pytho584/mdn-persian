---
title: "Document: scrollsnapchange event"
short-title: scrollsnapchange
slug: Web/API/Document/scrollsnapchange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.Document.scrollsnapchange_event
---

{{APIRef}}{{SeeCompatTable}}

رویداد **`scrollsnapchange`** از رابط {{domxref("Document")}} در پایان یک عملیات پیمایش، زمانی که یک هدف جدید برای snap اسکرول انتخاب می‌شود، روی [ظرف اسکرول](/en-US/docs/Glossary/Scroll_container) سند (document) فعال می‌شود.

این رویداد دقیقاً به همان شیوه‌ای کار می‌کند که رویداد [`scrollsnapchange`](/en-US/docs/Web/API/Element/scrollsnapchange_event) در رابط {{domxref("Element")}} کار می‌کند، با این تفاوت که کل سند HTML باید به‌عنوان ظرف اسکرول‌شونده با snap تنظیم شده باشد (یعنی {{cssxref("scroll-snap-type")}} روی عنصر {{htmlelement("html")}} تنظیم شده باشد).

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("scrollsnapchange", (event) => { })

onscrollsnapchange = (event) => { }
```

## نوع رویداد

یک {{domxref("SnapEvent")}} که از نوع عمومی {{domxref("Event")}} به ارث می‌برد.

## مثال‌ها

### استفاده پایه

فرض کنید یک عنصر {{htmlelement("main")}} داریم که حاوی محتوای قابل‌توجهی است و باعث پیمایش آن می‌شود:

```html
<main>
  <!-- محتوای قابل‌توجه -->
</main>
```

عنصر `<main>` می‌تواند با ترکیبی از ویژگی‌های CSS به یک ظرف اسکرول تبدیل شود، برای مثال:

```css
main {
  width: 250px;
  height: 450px;
  overflow: scroll;
}
```

سپس می‌توانیم با مشخص کردن ویژگی {{cssxref("scroll-snap-type")}} روی عنصر {{htmlelement("html")}}، رفتار snap اسکرول را روی محتوای در حال پیمایش پیاده‌سازی کنیم:

```css
html {
  scroll-snap-type: block mandatory;
}
```

قطعه کد جاوااسکریپت زیر باعث می‌شود رویداد `scrollsnapchange` روی سند HTML زمانی فعال شود که یک فرزند از عنصر `<main>` به‌عنوان هدف جدید انتخاب‌شده برای snap تعیین شود. در تابع handler، یک کلاس `selected` به فرزندی که توسط {{domxref("SnapEvent.snapTargetBlock")}} ارجاع داده شده است اضافه می‌کنیم؛ این کلاس می‌تواند برای استایل‌دهی به عنصر استفاده شود تا هنگام فعال شدن رویداد، ظاهری «انتخاب‌شده» داشته باشد (مثلاً با یک انیمیشن).

```js
document.addEventListener("scrollsnapchange", (event) => {
  event.snapTargetBlock.classList.add("selected");
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Document/scrollsnapchanging_event", "scrollsnapchanging")}}
- رویداد {{DOMxRef("Document/scrollend_event", "scrollend")}}
- {{domxref("SnapEvent")}}
- ویژگی CSS {{cssxref("scroll-snap-type")}}
- [ماژول CSS scroll snap](/en-US/docs/Web/CSS/Guides/Scroll_snap)
- [استفاده از رویدادهای scroll snap](/en-US/docs/Web/CSS/Guides/Scroll_snap/Using_scroll_snap_events)
- [Scroll Snap Events](https://developer.chrome.com/blog/scroll-snap-events) در developer.chrome.com (2024)