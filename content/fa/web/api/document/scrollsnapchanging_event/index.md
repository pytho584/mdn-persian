---
title: "Document: scrollsnapchanging event"
---

---
title: "Document: scrollsnapchanging event"
short-title: scrollsnapchanging
slug: Web/API/Document/scrollsnapchanging_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.Document.scrollsnapchanging_event
---

{{APIRef}}{{SeeCompatTable}}

رویداد **`scrollsnapchanging`** از رابط {{domxref("Document")}} روی [ظرف اسکرول](/en-US/docs/Glossary/Scroll_container) صادر می‌شود، زمانی که مرورگر تشخیص دهد یک هدف اسنپ اسکرولِ جدید در انتظار است؛ یعنی هدفی که با پایان یافتن ژست اسکرولِ فعلی انتخاب خواهد شد.

این رویداد تقریباً به همان شیوهٔ رویداد [`scrollsnapchanging`](/en-US/docs/Web/API/Element/scrollsnapchanging_event) در رابط {{domxref("Element")}} کار می‌کند؛ با این تفاوت که کل سند HTML باید به عنوان ظرف اسنپ اسکرول تنظیم شده باشد (یعنی {{cssxref("scroll-snap-type")}} روی عنصر {{htmlelement("html")}} تنظیم شده باشد).

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("scrollsnapchanging", (event) => { })

onscrollsnapchanging = (event) => { }
```

## نوع رویداد

یک {{domxref("SnapEvent")}} که از نوع عمومی {{domxref("Event")}} به ارث می‌رسد.

## مثال‌ها

### کاربرد پایه

فرض کنید یک عنصر {{htmlelement("main")}} داریم که محتوای قابل توجهی دارد و باعث اسکرول شدن آن می‌شود:

```html
<main>
  <!-- Significant content -->
</main>
```

عنصر `<main>` را می‌توان با استفاده از ترکیبی از ویژگی‌های CSS به یک ظرف اسکرول تبدیل کرد، برای مثال:

```css
main {
  width: 250px;
  height: 450px;
  overflow: scroll;
}
```

سپس می‌توانیم با تنظیم ویژگی {{cssxref("scroll-snap-type")}} روی عنصر {{htmlelement("html")}}، رفتار اسنپ اسکرول را روی محتوای اسکرول‌شونده پیاده‌سازی کنیم:

```css
html {
  scroll-snap-type: block mandatory;
}
```

قطعه‌کد جاوااسکریپت زیر باعث می‌شود که رویداد `scrollsnapchanging` روی سند HTML صادر شود؛ زمانی که یکی از فرزندان عنصر `<main>` به هدف اسنپ اسکرولِ در انتظار تبدیل شود. در تابع کنترل‌کننده، کلاس `pending` را روی همان فرزندی تنظیم می‌کنیم که ویژگی {{domxref("SnapEvent.snapTargetBlock", "snapTargetBlock")}} به آن اشاره می‌کند. از این کلاس می‌توان برای استایل‌دهی متفاوت به آن عنصر هنگام صدور رویداد استفاده کرد.

```js
document.addEventListener("scrollsnapchanging", (event) => {
  // remove previously-set "pending" classes
  const pendingElems = document.querySelectorAll(".pending");
  pendingElems.forEach((elem) => {
    elem.classList.remove("pending");
  });

  // Set current pending snap target class to "pending"
  event.snapTargetBlock.classList.add("pending");
});
```

در ابتدای تابع، همهٔ عناصری را که قبلاً کلاس `pending` به آن‌ها اعمال شده بود انتخاب و این کلاس را حذف می‌کنیم؛ به این ترتیب فقط جدیدترین هدف اسنپ اسکرولِ در انتظار استایل می‌گیرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Document/scrollsnapchange_event", "scrollsnapchange")}}
- رویداد {{DOMxRef("Document/scrollend_event", "scrollend")}}
- {{domxref("SnapEvent")}}
- ویژگی CSS {{cssxref("scroll-snap-type")}}
- [ماژول اسنپ اسکرول CSS](/en-US/docs/Web/CSS/Guides/Scroll_snap)
- [استفاده از رویدادهای اسنپ اسکرول](/en-US/docs/Web/CSS/Guides/Scroll_snap/Using_scroll_snap_events)
- [رویدادهای اسنپ اسکرول](https://developer.chrome.com/blog/scroll-snap-events) در developer.chrome.com (2024)