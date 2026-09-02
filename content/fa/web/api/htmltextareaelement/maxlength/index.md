---
title: "HTMLTextAreaElement: maxLength property"
short-title: maxLength
slug: Web/API/HTMLTextAreaElement/maxLength
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.maxLength
---

{{ApiRef("HTML DOM")}}

ویژگی **`maxLength`** از رابط {{domxref("HTMLTextAreaElement")}} حداکثر تعداد کاراکترهایی (بر حسب {{glossary("UTF-16", "واحد کد UTF-16")}}) را مشخص می‌کند که می‌توان برای مقدار عنصر {{HTMLElement("textarea")}} وارد کرد؛ همچنین حداکثر تعداد کاراکترهایی را تعیین می‌کند که برای معتبر بودن مقدار لازم است. این ویژگی، ویژگی [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/textarea#maxlength) عنصر را منعکس می‌کند. مقدار `-1` به این معناست که هیچ محدودیتی برای طول مقدار وجود ندارد.

> [!NOTE]
> مرورگرها معمولاً از وارد کردن کاراکترهای بیشتر از آنچه ویژگی `maxlength` اجازه می‌دهد جلوگیری می‌کنند. اگر طول مقدار از این حد بیشتر باشد، عنصر نامعتبر در نظر گرفته می‌شود و ویژگی {{domxref("ValidityState.tooLong", "tooLong")}} از شیء {{domxref("ValidityState")}} برابر با `true` خواهد بود.

## Value

عددی که اگر ویژگی `maxlength` روی عنصر تنظیم شده باشد، آن را نشان می‌دهد؛ در غیر این صورت برابر با `-1` است.

## Example

با توجه به HTML زیر:

```html
<p>
  <label for="comment">Comment</label>
  <textarea id="comment" minlength="10" maxlength="200"></textarea>
</p>
```

می‌توانید از ویژگی `maxLength` برای دریافت یا تنظیم مقدار ویژگی `maxlength` عنصر `<textarea>` استفاده کنید:

```js
const textareaElement = document.querySelector("#comment");
console.log(`Element's maxLength: ${textareaElement.maxLength}`); // "Element's maxlength: 200"
textareaElement.maxLength = 220; // updates the element's maxlength attribute value
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLTextAreaElement.value")}}
- {{domxref("HTMLTextAreaElement.minLength")}}
- {{domxref("ValidityState.tooLong")}}