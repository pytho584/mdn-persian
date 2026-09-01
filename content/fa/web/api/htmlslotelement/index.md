---
title: HTMLSlotElement
slug: Web/API/HTMLSlotElement
page-type: web-api-interface
browser-compat: api.HTMLSlotElement
---

{{APIRef("Web Components")}}

رابط (interface) **`HTMLSlotElement`** در [Shadow DOM API](/en-US/docs/Web/API/Web_components/Using_shadow_DOM) امکان دسترسی به نام و گره‌های اختصاص‌یافته‌ی یک عنصر HTML {{HTMLElement("slot")}} را فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه (Instance properties)

_همچنین ویژگی‌هایی را از رابط والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref('HTMLSlotElement.name')}}
  - : یک رشته (string) برای دریافت و تنظیم نام slot.

## روش‌های نمونه (Instance methods)

_همچنین روش‌هایی را از رابط والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref('HTMLSlotElement.assign()')}}
  - : گره‌های اختصاص‌یافته‌ی دستی برای این slot را به گره‌های داده شده تنظیم می‌کند.
- {{domxref('HTMLSlotElement.assignedNodes()')}}
  - : دنباله‌ای از گره‌های اختصاص‌یافته به این slot را برمی‌گرداند. اگر گزینه `flatten` روی `true` تنظیم شده باشد، دنباله‌ای از هر دو گره‌های اختصاص‌یافته به این slot و گره‌های اختصاص‌یافته به هر slot دیگری که از فرزندان این slot هستند را برمی‌گرداند. اگر هیچ گره اختصاص‌یافته‌ای یافت نشود، محتوای جایگزین (fallback content) slot را برمی‌گرداند.
- {{domxref('HTMLSlotElement.assignedElements()')}}
  - : دنباله‌ای از عناصر اختصاص‌یافته به این slot (و نه گره‌های دیگر) را برمی‌گرداند. اگر گزینه `flatten` روی `true` تنظیم شده باشد، دنباله‌ای از هر دو عناصر اختصاص‌یافته به این slot و عناصر اختصاص‌یافته به هر slot دیگری که از فرزندان این slot هستند را برمی‌گرداند. اگر هیچ عنصر اختصاص‌یافته‌ای یافت نشود، محتوای جایگزین slot را برمی‌گرداند.

## رویدادها (Events)

_همچنین رویدادهایی را از رابط والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

به این رویدادها با استفاده از {{DOMxRef("EventTarget.addEventListener", "addEventListener()")}} یا با تخصیص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید.

- {{domxref('HTMLSlotElement.slotchange_event', 'slotchange')}}
  - : زمانی که گره(های) داخل آن slot تغییر می‌کند، روی یک نمونه `HTMLSlotElement` (عنصر [`<slot>`](/en-US/docs/Web/HTML/Reference/Elements/slot)) فعال می‌شود.

## مثال‌ها

قطعه کد زیر از مثال [slotchange](https://github.com/mdn/web-components-examples/tree/main/slotchange) ما گرفته شده است (همچنین [به صورت زنده](https://mdn.github.io/web-components-examples/slotchange/) ببینید).

```js
let slots = this.shadowRoot.querySelectorAll("slot");
slots[1].addEventListener("slotchange", (e) => {
  let nodes = slots[1].assignedNodes();
  console.log(
    `Element in Slot "${slots[1].name}" changed to "${nodes[0].outerHTML}".`,
  );
});
```

در اینجا ما به ارجاع‌هایی از همه slotها دست می‌یابیم، سپس یک شنونده رویداد slotchange به slot دوم در الگو اضافه می‌کنیم – همان slotی که در مثال محتویات آن مدام تغییر می‌کند.

هر بار که عنصر درج‌شده در slot تغییر می‌کند، گزارشی به کنسول ثبت می‌کنیم که نشان می‌دهد کدام slot تغییر کرده و گره جدید داخل slot چیست.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}