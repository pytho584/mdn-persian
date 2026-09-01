---
title: "Element: ariaRequired property"
---

---
title: "Element: ariaRequired property"
short-title: ariaRequired
slug: Web/API/Element/ariaRequired
page-type: web-api-instance-property
browser-compat: api.Element.ariaRequired
---

{{APIRef("DOM")}}

ویژگی **`ariaRequired`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار صفت `aria-required` است که نشان می‌دهد آیا ورودی کاربر در این عنصر قبل از ارسال فرم ضروری است یا خیر.

> [!NOTE]
> در صورت امکان از یک عنصر HTML {{htmlelement("input")}} با `type="text"` یا یک {{htmlelement("textarea")}} استفاده کنید زیرا این‌ها معنای داخلی دارند و به صفات ARIA نیاز ندارند.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : کاربران باید قبل از ارسال فرم، ورودی را در یک عنصر ارائه دهند.
- `"false"`
  - : ورودی کاربر برای ارسال فرم ضروری نیست.

## مثال‌ها

در این مثال، صفت `aria-required` روی عنصری با شناسهٔ `txtBoxInput` روی `"true"` تنظیم شده است که نشان می‌دهد این ورودی باید تکمیل شود. با استفاده از `ariaRequired` مقدار را به `"false"` به‌روز می‌کنیم.

```html
<div id="txtboxMultilineLabel">برچسب‌های مقاله را وارد کنید</div>
<div
  role="textbox"
  id="txtBoxInput"
  contenteditable="true"
  aria-multiline="true"
  aria-labelledby="txtboxMultilineLabel"
  aria-required="true"></div>
```

```js
let el = document.getElementById("txtBoxInput");
console.log(el.ariaRequired); // "true"
el.ariaRequired = "false";
console.log(el.ariaRequired); // "false"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش textbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)