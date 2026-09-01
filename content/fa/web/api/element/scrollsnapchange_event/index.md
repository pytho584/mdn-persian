---
title: "Element: scrollsnapchange event"
short-title: scrollsnapchange
slug: Web/API/Element/scrollsnapchange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.Element.scrollsnapchange_event
---

{{APIRef}}{{SeeCompatTable}}

رویداد **`scrollsnapchange`** از رابط {{domxref("Element")}} روی [scroll container](/en-US/docs/Glossary/Scroll_container) در پایان یک عملیات پیمایش، هنگامی که یک هدف snap پیمایش جدید انتخاب شده است، درست قبل از آن که رویداد متناظر {{domxref("Element/scrollend_event", "scrollend")}} فعال شود، فراخوانی می‌شود.

یک عملیات پیمایش زمانی پایان می‌یابد که کاربر پیمایش را درون یک ظرف پیمایش به پایان برساند — برای مثال با استفاده از یک حرکت لمسی یا با کشیدن اشاره‌گر ماوس روی نوار پیمایش — و حرکت را رها کند.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("scrollsnapchange", (event) => { })

onscrollsnapchange = (event) => { }
```

## Event type

یک {{domxref("SnapEvent")}} که از نوع عمومی {{domxref("Event")}} ارث‌بری می‌کند.

## Examples

### Basic usage

فرض کنید یک عنصر {{htmlelement("main")}} داریم که حاوی محتوای قابل توجهی است و باعث پیمایش آن می‌شود:

```html
<main>
  <!-- Significant content -->
</main>
```

عنصر `<main>` می‌تواند با استفاده از ترکیبی از ویژگی CSS {{cssxref("scroll-snap-type")}} و سایر ویژگی‌ها به یک ظرف پیمایش تبدیل شود که هنگام پیمایش به فرزندان خود snap کند. برای مثال:

```css
main {
  width: 250px;
  height: 450px;
  overflow: scroll;
  scroll-snap-type: block mandatory;
}
```

قطعه کد JavaScript زیر باعث می‌شود رویداد `scrollsnapchange` روی عنصر `<main>` فعال شود زمانی که یکی از فرزندان آن به یک هدف snap تازه انتخاب شده تبدیل شود. در تابع کنترل‌کننده، یک کلاس `selected` روی فرزندی که توسط ویژگی {{domxref("SnapEvent.snapTargetBlock")}} ارجاع داده شده است قرار می‌دهیم، که می‌تواند برای استایل‌دهی به آن استفاده شود تا هنگام فعال شدن رویداد، ظاهر آن انتخاب شده به نظر برسد (مثلاً با یک انیمیشن).

```js
const scrollingElem = document.querySelector("main");

scrollingElem.addEventListener("scrollsnapchange", (event) => {
  event.snapTargetBlock.classList.add("selected");
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element/scrollsnapchanging_event", "scrollsnapchanging")}} event
- {{DOMxRef("Document/scrollend_event", "scrollend")}} event
- {{domxref("SnapEvent")}}
- CSS {{cssxref("scroll-snap-type")}} property
- [CSS scroll snap module](/en-US/docs/Web/CSS/Guides/Scroll_snap)
- [Using scroll snap events](/en-US/docs/Web/CSS/Guides/Scroll_snap/Using_scroll_snap_events)
- [Scroll Snap Events](https://developer.chrome.com/blog/scroll-snap-events) on developer.chrome.com (2024)