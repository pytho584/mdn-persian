---
title: "HTMLInputElement: maxLength property"
short-title: maxLength
slug: Web/API/HTMLInputElement/maxLength
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.maxLength
---

{{ApiRef("HTML DOM")}}

خصوصیت **`maxLength`** در رابط {{domxref("HTMLInputElement")}}، حداکثر تعداد نویسه‌ها (بر حسب {{glossary("UTF-16", "UTF-16 code units")}}) را مشخص می‌کند که می‌توان برای مقدار عنصر {{HTMLElement("input")}} وارد کرد و همچنین حداکثر تعداد نویسه‌هایی است که برای معتبر بودن مقدار مجاز شمرده می‌شود. این ویژگی، خصوصیت [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/input#maxlength) عنصر را بازتاب می‌دهد. مقدار `-1` به این معناست که هیچ محدودیتی برای طول مقدار وجود ندارد.

> [!NOTE]
> مرورگرها معمولاً از وارد کردن نویسه‌های بیشتر از آنچه ویژگی `maxlength` مجاز می‌داند، جلوگیری می‌کنند. اگر طول مقدار بیشتر از این حد باشد، عنصر نامعتبر در نظر گرفته می‌شود و ویژگی {{domxref("ValidityState.tooLong", "tooLong")}} در شیء {{domxref("ValidityState")}} برابر با `true` خواهد بود.

## مقدار

عددی که نشان‌دهندهٔ `maxlength` عنصر است، در صورت وجود؛ در غیر این صورت `-1`.

## مثال

با توجه به HTML زیر:

```html
<p>
  <label for="password">Your password</label>
  <input id="password" type="password" minlength="8" maxlength="20" />
</p>
```

می‌توانید از خصوصیت `maxLength` برای دریافت یا تنظیم مقدار ویژگی `maxlength` عنصر `<input>` استفاده کنید:

```js
const inputElement = document.querySelector("#password");
console.log(`Element's maxLength: ${inputElement.maxLength}`); // "Element's maxlength: 20"
inputElement.maxLength = 18; // updates the element's maxlength attribute value
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.minLength")}}
- {{domxref("ValidityState.tooLong")}}