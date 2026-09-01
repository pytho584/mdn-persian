---
title: "HTMLInputElement: minLength property"
---
---
title: "HTMLInputElement: minLength property"
short-title: minLength
slug: Web/API/HTMLInputElement/minLength
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.minLength
---

{{ApiRef("HTML DOM")}}

خاصیت **`minLength`** از رابط {{domxref("HTMLInputElement")}} نشان‌دهندهٔ حداقل تعداد کاراکترها (بر حسب {{glossary("UTF-16", "واحدهای کد UTF-16")}}) است که برای معتبر بودن مقدار عنصر {{HTMLElement("input")}} لازم است. این خاصیت، ویژگی [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/input#minlength) عنصر را منعکس می‌کند. مقدار `1-` به معنای عدم وجود شرط حداقل طول است.

> [!NOTE]
> اگر ورودی دارای مقدار باشد و آن مقدار کاراکترهای کمتری نسبت به ویژگی `minlength` داشته باشد، عنصر نامعتبر در نظر گرفته می‌شود و خاصیت {{domxref("ValidityState.tooShort", "tooShort")}} از شیء {{domxref("ValidityState")}} برابر `true` خواهد بود.

## مقدار

یک عدد که مقدار `minlength` عنصر را در صورت وجود، یا `1-` را نشان می‌دهد.

## مثال

با توجه به HTML زیر:

```html
<p>
  <label for="password">Your password</label>
  <input id="password" type="password" minlength="8" maxlength="20" />
</p>
```

می‌توانید از خاصیت `minLength` برای دریافت یا تنظیم مقدار ویژگی `minlength` عنصر `<input>` استفاده کنید:

```js
const inputElement = document.querySelector("#password");
console.log(`Element's minLength: ${inputElement.minLength}`); // "Element's minlength: 8"
inputElement.minLength = 12; // updates the element's minlength attribute value
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.maxLength")}}
- {{domxref("ValidityState.tooShort")}}