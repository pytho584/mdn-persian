---
title: "HTMLElement: virtualKeyboardPolicy property"
---

---
title: "HTMLElement: virtualKeyboardPolicy property"
short-title: virtualKeyboardPolicy
slug: Web/API/HTMLElement/virtualKeyboardPolicy
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLElement.virtualKeyboardPolicy
---

{{APIRef("VirtualKeyboard API")}}{{SeeCompatTable}}

ویژگی **`virtualKeyboardPolicy`** از واسط {{domxref("HTMLElement")}} یک رشته را دریافت و تنظیم می‌کند که رفتار صفحه‌کلید مجازی روی صفحه را در دستگاه‌هایی مانند تبلت‌ها، تلفن‌های همراه یا سایر دستگاه‌هایی که ممکن است صفحه‌کلید سخت‌افزاری در دسترس نباشد، مشخص می‌سازد — مشروط بر اینکه محتوای عنصر قابل ویرایش باشد (برای مثال، یک عنصر {{htmlelement("input")}} یا {{htmlelement("textarea")}} باشد، یا عنصری که ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) روی آن تنظیم شده است).

این ویژگی، مقدار ویژگی سراسری HTML یعنی [`virtualkeyboardpolicy`](/en-US/docs/Web/HTML/Reference/Global_attributes/virtualkeyboardpolicy) را منعکس می‌کند.

## Value

یک مقدار شمارشی (enumerated) است؛ مقادیر ممکن عبارت‌اند از:

- `"auto"` یا یک رشتهٔ خالی (`""`)
  - مرورگر به‌طور خودکار صفحه‌کلید مجازی را وقتی کاربر روی عنصر ضربه می‌زند یا آن را فوکوس می‌کند، نمایش می‌دهد.
- `"manual"`
  - مرورگر به‌طور خودکار صفحه‌کلید مجازی را نمایش نمی‌دهد؛ نمایش/پنهان کردن صفحه‌کلید مجازی به صورت دستی و توسط اسکریپت انجام می‌شود.

## Examples

مثال زیر نشان می‌دهد که چگونه رفتار صفحه‌کلید مجازی روی صفحه را از طریق اسکریپت کنترل کنیم:

```js
const element = document.querySelector("input");

// the on-screen virtual keyboard behavior will be controlled by script manually
element.virtualKeyboardPolicy = "manual";
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [`virtualkeyboardpolicy`](/en-US/docs/Web/HTML/Reference/Global_attributes/virtualkeyboardpolicy) ویژگی سراسری HTML