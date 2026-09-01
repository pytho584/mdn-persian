---
title: "HTMLInputElement: list property"
---

{{ApiRef("HTML DOM")}}

خاصیت فقط خواندنی **`list`** از رابط {{domxref("HTMLInputElement")}}، عنصر {{domxref("HTMLDataListElement")}} که توسط ویژگی [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list) عنصر اشاره شده است را برمی‌گرداند، یا اگر ویژگی `list` تعریف نشده باشد یا مقدار ویژگی `list` با هیچ `<datalist>` در همان درخت مرتبط نباشد، `null` را برمی‌گرداند.

> [!NOTE]
> این یک خاصیت فقط خواندنی است. برای مرتبط کردن یک `<datalist>` با یک عنصر، مقدار ویژگی `list` را با استفاده از {{domxref("Element.setAttribute", "setAttribute()")}} تنظیم کنید.

## مقدار

یک {{domxref("HTMLDataListElement")}} یا `null`.

## مثال

با توجه به HTML زیر:

```html
<label for="planet">Which planet are you from?</label>
<input id="planet" type="text" list="superhero" />
<datalist id="superhero">
  <option value="Azarath"></option>
  <option value="Krypton"></option>
  <option value="Tamaran"></option>
</datalist>
```

می‌توانید عنصر `<datalist>` مرتبط با `<input>` را بازیابی کنید:

```js
const inputElement = document.querySelector("#planet");
console.log(inputElement.list); // returns the superhero HTMLDatalistElement
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.type")}}
- {{domxref("HTMLDataListElement")}}
- {{domxref("HTMLOptionElement")}}
- {{domxref("HTMLCollection")}}
- {{htmlelement("input")}}
- {{htmlelement("datalist")}}
- {{htmlelement("option")}}