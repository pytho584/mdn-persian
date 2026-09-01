```yaml
---
title: "HTMLSlotElement: slotchange event"
short-title: slotchange
slug: Web/API/HTMLSlotElement/slotchange_event
page-type: web-api-event
browser-compat: api.HTMLSlotElement.slotchange_event
---

{{APIRef("Web Components")}}

رویداد **`slotchange`** روی یک نمونه از {{DOMxRef("HTMLSlotElement")}} (عنصر {{HTMLElement("slot")}}) هنگامی که گره(های) موجود در آن حفره (slot) تغییر می‌کند، منتشر می‌شود.

> [!NOTE]
> رویداد `slotchange` زمانی که فرزندان یک گره‌ی حفره‌شده (slotted node) تغییر می‌کنند، فعال نمی‌شود — تنها زمانی که خود گره‌ها را تغییر دهید (مثلاً اضافه یا حذف کنید) این رویداد رخ می‌دهد.

برای فعال کردن رویداد **slotchange**، باید صفت `slot` را تنظیم یا حذف کنید.

این رویداد قابل لغو (cancelable) نیست.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم یک ویژگی مدیریت رویداد (event handler property) به کار می‌رود.

```js-nolint
addEventListener("slotchange", (event) => { })

onslotchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
element.setAttribute("slot", slotName);
// element.assignedSlot = $slot
element.removeAttribute("slot");
// element.assignedSlot = null
```

قطعه کد زیر از [مثال slotchange](https://github.com/mdn/web-components-examples/tree/main/slotchange) ما گرفته شده است ([همچنین به صورت زنده مشاهده کنید](https://mdn.github.io/web-components-examples/slotchange/)).

```js
let slots = this.shadowRoot.querySelectorAll("slot");
slots[1].addEventListener("slotchange", (e) => {
  let nodes = slots[1].assignedNodes();
  console.log(
    `Element in Slot "${slots[1].name}" changed to "${nodes[0].outerHTML}".`,
  );
});
```

در اینجا به تمام عناصر `<slot>` ارجاع می‌دهیم، سپس یک شنونده رویداد `slotchange` به دومین حفره (slot) الگو اضافه می‌کنیم — حفره‌ای که محتوایش در مثال تغییر می‌کند.

هر بار که عنصر درون حفره تغییر می‌کند، گزارشی در کنسول ثبت می‌شود که نشان می‌دهد کدام حفره تغییر کرده و گره جدید درون حفره چیست.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSlotElement")}}
```