---
title: "HTMLSlotElement: assignedNodes() method"
---

---
title: "HTMLSlotElement: assignedNodes() method"
short-title: assignedNodes()
slug: Web/API/HTMLSlotElement/assignedNodes
page-type: web-api-instance-method
browser-compat: api.HTMLSlotElement.assignedNodes
---

{{APIRef("Shadow DOM API")}}

متد **`assignedNodes()`** از رابط {{domxref("HTMLSlotElement")}} دنباله‌ای از گره‌های اختصاص‌یافته به این اسلات را برمی‌گرداند.

اگر گزینه `flatten` روی `true` تنظیم شود، دنباله‌ای شامل گره‌های اختصاص‌یافته به این اسلات و همچنین گره‌های اختصاص‌یافته به هر اسلات دیگری که فرزند این اسلات است برگردانده می‌شود. اگر هیچ گره اختصاص‌یافته‌ای یافت نشود، محتوای جایگزین اسلات برگردانده می‌شود.

## نحو

```js-nolint
assignedNodes()
assignedNodes(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : شیای که گزینه‌های مربوط به گره‌های بازگردانده‌شده را تعیین می‌کند. گزینه‌های موجود عبارت‌اند از:
    - `flatten`
      - : یک مقدار بولین که مشخص می‌کند آیا گره‌های اختصاص‌یافته هر عنصر `<slot>` فرزند موجود برگردانده شوند (`true`) یا خیر (`false`). مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

یک آرایه از گره‌ها.

## مثال‌ها

قطعه کد زیر از [مثال slotchange](https://github.com/mdn/web-components-examples/tree/main/slotchange) ما گرفته شده است ([مشاهده نسخه زنده](https://mdn.github.io/web-components-examples/slotchange/)).

```js
let slots = this.shadowRoot.querySelectorAll("slot");
slots[1].addEventListener("slotchange", (e) => {
  let nodes = slots[1].assignedNodes();
  console.log(
    `Element in Slot "${slots[1].name}" changed to "${nodes[0].outerHTML}".`,
  );
});
```

در اینجا ارجاع‌هایی به همه اسلات‌ها می‌گیریم و سپس یک شنونده رویداد `slotchange` به دومین اسلات در قالب اضافه می‌کنیم — همان اسلاتی که محتوایش در این مثال مرتباً تغییر می‌کند.

هر بار که عنصر درج‌شده در اسلات تغییر کند، گزارشی در کنسول ثبت می‌کنیم که مشخص می‌کند کدام اسلات تغییر کرده است و گره جدید داخل اسلات چیست.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}