```
---
title: "Element: scrollsnapchanging event"
short-title: scrollsnapchanging
slug: Web/API/Element/scrollsnapchanging_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.Element.scrollsnapchanging_event
---

{{APIRef}}{{SeeCompatTable}}

رویداد **`scrollsnapchanging`** از رابط {{domxref("Element")}} روی [ظرف اسکرول](/en-US/docs/Glossary/Scroll_container) رخ می‌دهد زمانی که مرورگر تعیین کند که یک هدف اسنپ اسکرول جدید در انتظار است، یعنی هدفی که پس از پایان ژست اسکرول فعلی انتخاب خواهد شد.

به‌طور خاص، این رویداد در طول یک ژست اسکرول، هر بار که کاربر به اهداف اسنپ بالقوه‌ی جدید می‌رسد، رخ می‌دهد. به‌عنوان مثال، کاربر می‌تواند با کشیدن انگشت روی صفحه‌ی لمسی به‌آرامی اسکرول کند، یا دکمه‌ی ماوس را روی نوار اسکرول نگه دارد و ماوس را حرکت دهد. بنابراین، `scrollsnapchanging` ممکن است برای هر ژست اسکرول چندین بار رخ دهد.

با این حال، برای یک ژست اسکرول که از روی چندین هدف اسنپ عبور می‌کند، روی همه‌ی اهداف بالقوه رخ نمی‌دهد. بلکه فقط برای آخرین هدفی که اسنپ به‌طور بالقوه روی آن متوقف می‌شود، رخ می‌دهد.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده‌ی رویداد تنظیم کنید.

```js-nolint
addEventListener("scrollsnapchanging", (event) => { })

onscrollsnapchanging = (event) => { }
```

## نوع رویداد

یک {{domxref("SnapEvent")}} که از نوع عمومی {{domxref("Event")}} ارث می‌برد.

## مثال‌ها

### کاربرد پایه

فرض کنید یک عنصر {{htmlelement("main")}} داریم که محتوای قابل توجهی دارد و باعث اسکرول آن می‌شود:

```html
<main>
  <!-- Significant content -->
</main>
```

با ترکیب ویژگی CSS {{cssxref("scroll-snap-type")}} و سایر ویژگی‌ها، می‌توان عنصر `<main>` را به یک ظرف اسکرول تبدیل کرد که هنگام اسکرول به فرزندانش اسنپ می‌شود. برای مثال:

```css
main {
  width: 250px;
  height: 450px;
  overflow: scroll;
  scroll-snap-type: block mandatory;
}
```

قطعه‌کد جاوااسکریپت زیر باعث می‌شود که رویداد `scrollsnapchanging` روی عنصر `<main>` رخ دهد، زمانی که یکی از فرزندان آن به هدف اسنپ در انتظار تبدیل می‌شود. در تابع کنترل‌کننده، ما یک کلاس `pending` به فرزندی که توسط ویژگی {{domxref("SnapEvent.snapTargetBlock", "snapTargetBlock")}} ارجاع شده است، اختصاص می‌دهیم که می‌توان از آن برای استایل‌دهی متفاوت به آن عنصر هنگام رخ دادن رویداد استفاده کرد.

```js
scrollingElem.addEventListener("scrollsnapchanging", (event) => {
  // remove previously-set "pending" classes
  const pendingElems = document.querySelectorAll(".pending");
  pendingElems.forEach((elem) => {
    elem.classList.remove("pending");
  });

  // Set current pending snap target class to "pending"
  event.snapTargetBlock.classList.add("pending");
});
```

در ابتدای تابع، همه‌ی عناصری را که قبلاً کلاس `pending` به آن‌ها اعمال شده بود را انتخاب و آن را حذف می‌کنیم، به طوری که فقط آخرین هدف اسنپ در انتظار استایل‌دهی شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Element/scrollsnapchange_event", "scrollsnapchange")}}
- رویداد {{DOMxRef("Document/scrollend_event", "scrollend")}}
- {{domxref("SnapEvent")}}
- ویژگی CSS {{cssxref("scroll-snap-type")}}
- [ماژول اسنپ اسکرول CSS](/en-US/docs/Web/CSS/Guides/Scroll_snap)
- [استفاده از رویدادهای اسنپ اسکرول](/en-US/docs/Web/CSS/Guides/Scroll_snap/Using_scroll_snap_events)
- [رویدادهای اسنپ اسکرول](https://developer.chrome.com/blog/scroll-snap-events) در developer.chrome.com (۲۰۲۴)
```