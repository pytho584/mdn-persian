---
title: "HTMLTextAreaElement: minLength property"
short-title: minLength
slug: Web/API/HTMLTextAreaElement/minLength
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.minLength
---

{{ApiRef("HTML DOM")}}

ویژگی **`minLength`** از رابط {{domxref("HTMLTextAreaElement")}} حداقل تعداد کاراکترها (در {{glossary("UTF-16", "واحدهای کد UTF-16")}}) مورد نیاز برای معتبر بودن مقدار عنصر {{HTMLElement("textarea")}} را نشان می‌دهد. این ویژگی منعکس‌کنندهٔ ویژگی [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/textarea#minlength) عنصر است. مقدار `1-` به معنای عدم وجود حداقل طول است.

> **توجه:** اگر textarea مقداری داشته باشد و آن مقدار کاراکترهای کمتری از آنچه ویژگی `minlength` نیاز دارد داشته باشد، عنصر نامعتبر در نظر گرفته می‌شود و ویژگی {{domxref("ValidityState.tooShort", "tooShort")}} از شیء {{domxref("ValidityState")}} برابر با `true` خواهد بود.

## مقدار

عددی که نشان‌دهندهٔ `minlength` عنصر در صورت وجود است، یا `1-`.

## مثال

با توجه به HTML زیر:

```html
<p>
  <label for="comment">Comment</label>
  <textarea id="comment" minlength="10" maxlength="200"></textarea>
</p>
```

می‌توانید از ویژگی `minLength` برای دریافت یا تنظیم مقدار ویژگی `minlength` عنصر `<textarea>` استفاده کنید:

```js
const textareaElement = document.querySelector("#comment");
console.log(`Element's minLength: ${textareaElement.minLength}`); // "Element's minlength: 10"
textareaElement.minLength = 5; // updates the element's minlength attribute value
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTextAreaElement.value")}}
- {{domxref("HTMLTextAreaElement.maxLength")}}
- {{domxref("ValidityState.tooShort")}}