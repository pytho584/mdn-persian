---
title: "ARIA: aria-checked attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-checked attribute"
short-title: aria-checked
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-checked
page-type: aria-attribute
spec-urls:
  - https://w3c.github.io/aria/#aria-checked
  - https://www.w3.org/WAI/ARIA/apg/patterns/checkbox/examples/checkbox/
sidebar: accessibilitysidebar
---

ویژگی `aria-checked` وضعیت «انتخاب‌شده» فعلی چک‌باکس‌ها، دکمه‌های رادیویی و سایر ویجت‌ها را نشان می‌دهد.

> [!NOTE]
> در صورت امکان از عنصر HTML {{htmlelement("input")}} با `type="checkbox"` و `type="radio"` استفاده کنید؛ زیرا این عناصر معنای داخلی دارند و به ویژگی‌های ARIA نیازی ندارند.

## توضیحات

ویژگی `aria-checked` نشان می‌دهد که آیا عنصر انتخاب شده است (`true`)، انتخاب نشده است (`false)`، یا وضعیت انتخابی آن نامشخص است (`mixed`)؛ یعنی نه انتخاب شده و نه انتخاب نشده. مقدار `mixed` توسط نقش‌های ورودی سه‌حالته [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role) و [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role) پشتیبانی می‌شود.

مقدار `mixed` در [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)، [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)، یا [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role) و عناصری که از این‌ها ارث می‌برند پشتیبانی نمی‌شود. اگر `mixed` در شرایطی که پشتیبانی نمی‌شود تنظیم شود، مقدار آن false خواهد بود.

```html
<span
  role="checkbox"
  id="checkBoxInput"
  aria-checked="false"
  tabindex="0"
  aria-labelledby="chk15-label"></span>
<label id="chk15-label">Subscribe to the newsletter</label>
```

ویژگی `tabindex` برای فعال‌کردن فوکوس الزامی است. برای جابه‌جایی وضعیت `aria-checked` به جاوااسکریپت نیاز است. و اگر این چک‌باکس بخشی از یک فرم قابل ارسال باشد، جاوااسکریپت بیشتری برای تنظیم نام و مقدار مورد نیاز است.

نمونه بالا می‌توانست به صورت زیر نوشته شود:

```html
<input type="checkbox" id="chk15-label" name="Subscribe" />
<label for="chk15-label">Subscribe to the newsletter</label>
```

با استفاده از عنصر {{htmlelement("input")}} با `type="checkbox"` به جای ARIA، هیچ نیازی به جاوااسکریپت نیست.

## مقادیر

- false
  - : عنصر از انتخاب‌شدن پشتیبانی می‌کند اما در حال حاضر انتخاب نشده است.
- true
  - : عنصر انتخاب شده است.
- mixed
  - : فقط برای [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role) و [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)، معادل `indeterminate`، نشان‌دهنده یک مقدار ترکیبی است که نه انتخاب شده و نه انتخاب نشده.
- undefined (default)
  - : عنصر از انتخاب‌شدن پشتیبانی نمی‌کند.

## نقش‌های مرتبط

- [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
- [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)

## رابط‌های مرتبط

- {{domxref("Element.ariaChecked")}}
  - : ویژگی [`ariaChecked`](/en-US/docs/Web/API/Element/ariaChecked) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-checked` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaChecked")}}
  - : ویژگی [`ariaChecked`](/en-US/docs/Web/API/ElementInternals/ariaChecked) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-checked` را منعکس می‌کند.

```js
myHTMLElement.ariaChecked = true;
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)
- [`<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/radio)
- [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed)
- [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected)
- [نمونه چک‌باکس دو حالته](https://www.w3.org/WAI/ARIA/apg/example-index/checkbox/checkbox.html) - w3.org
- [نمونه چک‌باکس با حالت مختلط](https://www.w3.org/WAI/ARIA/apg/example-index/checkbox/checkbox-mixed.html) - w3.org