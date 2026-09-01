---
title: "HTMLSlotElement: assignedElements() method"
short-title: assignedElements()
slug: Web/API/HTMLSlotElement/assignedElements
page-type: web-api-instance-method
browser-compat: api.HTMLSlotElement.assignedElements
---

{{APIRef("Shadow DOM API")}}

روش **`assignedElements()`** در interface {{domxref("HTMLSlotElement")}} دنباله‌ای از عناصر اختصاص‌داده‌شده به این slot را برمی‌گرداند (و هیچ گره دیگری را).

اگر گزینه `flatten` برابر با `true` تنظیم شود، دنباله‌ای شامل هم عناصر اختصاص‌داده‌شده به این slot و هم عناصر اختصاص‌داده‌شده به هر slot فرزند دیگری که از نوادگان این slot هستند، برگردانده می‌شود. اگر هیچ عنصر اختصاص‌داده‌شده‌ای یافت نشود، محتوای جایگزین (fallback) slot برگردانده می‌شود.

## سینتکس

```js-nolint
assignedElements()
assignedElements(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء که گزینه‌های مربوط به گره‌های بازگشتی را تنظیم می‌کند. گزینه‌های موجود عبارت‌اند از:
    - `flatten`
      - : یک مقدار بولی که مشخص می‌کند آیا عناصر اختصاص‌داده‌شده به هر عنصر `<slot>` فرزند موجود بازگردانده شوند (`true`) یا نه (`false`). پیش‌فرض `false` است.

### مقدار بازگشتی

یک آرایه از عناصر.

## مثال‌ها

```js
let slots = this.shadowRoot.querySelector("slot");
let elements = slots.assignedElements({ flatten: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
