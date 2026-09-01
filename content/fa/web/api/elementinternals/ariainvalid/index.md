---
title: "ElementInternals: ariaInvalid property"
short-title: ariaInvalid
slug: Web/API/ElementInternals/ariaInvalid
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaInvalid
---

{{APIRef("Web Components")}}

ویژگی **`ariaInvalid`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid) را منعکس می‌کند. این ویژگی برای نقش‌های [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)، [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)، [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)، [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)، [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)، [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)، [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role) و [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role) مرتبط است و به API دسترس‌پذیری نشان می‌دهد که آیا مقدار واردشده با قالبی که برنامه انتظار دارد ناسازگار است.

> [!NOTE]
> تنظیم ویژگی‌های ARIA روی `ElementInternals` امکان تعریف معناشناسی‌های پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این معناشناسی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما این کار تضمین می‌کند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکند، معناشناسی‌های پیش‌فرض حفظ شوند. برای اطلاعات بیشتر، به [سند توضیحی مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر نامعتبر است.
- `"false"` (پیش‌فرض)
  - : عنصر در وضعیت نامعتبر نیست.
- `"grammar"`
  - : عنصر به این دلیل در وضعیت نامعتبر است که خطای گرامری تشخیص داده شده است.
- `"spelling"`
  - : عنصر به این دلیل در وضعیت نامعتبر است که خطای املایی تشخیص داده شده است.

## مثال‌ها

در این مثال، عنصر `<custom-text>` را تعریف و ایجاد می‌کنیم و سپس مقدار `ariaInvalid` را از اولین عنصر `<custom-text>` در سند بازیابی می‌کنیم.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this._internals = this.attachInternals();
    this._internals.ariaInvalid = "false";
  }
  // …
}

window.customElements.define("custom-text", CustomControl);

const element = document.querySelector("custom-text");
console.log(element._internals.ariaInvalid);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ElementInternals.ariaRequired")}}
- [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required)
- [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)