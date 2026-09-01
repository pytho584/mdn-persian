---
title: "Element: ariaInvalid property"
short-title: ariaInvalid
slug: Web/API/Element/ariaInvalid
page-type: web-api-instance-property
browser-compat: api.Element.ariaInvalid
---

{{APIRef("DOM")}}

ویژگی **`ariaInvalid`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid) را منعکس می‌کند. این ویژگی برای نقش‌های [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)، [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)، [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)، [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)، [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)، [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)، [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role) و [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role) کاربرد دارد و به API دسترسی‌پذیری نشان می‌دهد که آیا مقدار وارد شده با فرمت مورد انتظار برنامه مطابقت ندارد یا خیر.

اگر ویژگی موجود نباشد یا روی رشتهٔ خالی تنظیم شده باشد، فناوری کمکی مقدار را به‌گونه‌ای رفتار می‌کند که گویی روی `false` تنظیم شده است. اگر ویژگی وجود داشته باشد اما روی مقداری غیر از `false`، `grammar`، `spelling` یا رشتهٔ خالی (`""`) تنظیم شده باشد، فناوری کمکی مقدار را به‌عنوان `true` در نظر می‌گیرد. این ویژگی مقدار واقعی ویژگی را منعکس می‌کند، نه آن‌گونه که توسط فناوری کمکی پردازش می‌شود.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر نامعتبر است.
- `"false"` (پیش‌فرض)
  - : عنصر در حالت نامعتبر نیست.
- `"grammar"`
  - : عنصر به دلیل تشخیص خطای گرامری در حالت نامعتبر است.
- `"spelling"`
  - : عنصر به دلیل تشخیص خطای املایی در حالت نامعتبر است.

## مثال‌ها

در این مثال، ویژگی [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid) روی عنصری با شناسهٔ `quote` حذف شده است که باعث می‌شود `null` برگرداند و به‌عنوان `false` تلقی شود. با استفاده از `ariaInvalid`، مقدار را به `grammar` به‌روزرسانی می‌کنیم (زیرا دو خطا وجود دارد).

```html
<div id="quote" role="textbox" contenteditable>you are your best thing..</div>
```

```html hidden
<hr />
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const el = document.getElementById("quote");
log(`Initial value: ${el.ariaInvalid}`);
el.ariaInvalid = "grammar";
log(`Updated value: ${el.ariaInvalid}`);
```

{{EmbedLiveSample("Examples", "", "100")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.ariaRequired")}}
- [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required)
- [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)
- {{domxref("Element.ariaErrorMessageElements")}}