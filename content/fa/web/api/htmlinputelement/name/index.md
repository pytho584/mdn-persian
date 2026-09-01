---
title: "HTMLInputElement: name property"
short-title: name
slug: Web/API/HTMLInputElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.name
---

{{ApiRef("HTML DOM")}}

خاصیت **`name`** از رابط {{domxref("HTMLInputElement")}} نشان‌دهندهٔ نام عنصر {{HTMLElement("input")}} است. این خاصیت ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/input#name) عنصر را منعکس می‌کند.

## مقدار

یک رشته که نام عنصر را نشان می‌دهد.

## مثال

با توجه به HTML زیر:

```html
<p>
  <label for="planet">Which planet were you born on?</label>
  <input id="planet" type="text" name="origin" />
</p>
```

می‌توانید از خاصیت `name` برای دریافت یا تنظیم نام `<input>` استفاده کنید:

```js
const inputElement = document.querySelector("#planet");
console.log(`Element's name: ${inputElement.name}`); // "Element's name: origin"
inputElement.name = "planet"; // updates the element's name
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.type")}}