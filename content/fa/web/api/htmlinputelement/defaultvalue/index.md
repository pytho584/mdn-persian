---
title: "HTMLInputElement: defaultValue property"
short-title: defaultValue
slug: Web/API/HTMLInputElement/defaultValue
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.defaultValue
---

{{ApiRef("HTML DOM")}}

ویژگی **`defaultValue`** در رابط {{domxref("HTMLInputElement")}} مقدار اصلی (یا پیش‌فرض) عنصر {{HTMLElement("input")}} را نشان می‌دهد. این ویژگی منعکس‌کنندهٔ صفت [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) عنصر است.

## مقدار

یک رشته (string) که مقدار پیش‌فرض یا اصلی عنصر `<input>` را نشان می‌دهد.

## مثال

با توجه به HTML زیر:

```html
<label for="planet">Which planet were you born on?</label>
<input id="planet" type="text" value="Azarath" />
```

کد زیر صرف‌نظر از اینکه کاربر چه متنی در ورودی متن وارد کند، نتیجهٔ یکسانی را ارائه می‌دهد:

```js
const inputElement = document.querySelector("#planet");
console.log(`Original value: ${inputElement.defaultValue}`); // "Original value: Azarath"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.value")}}
- {{domxref("HTMLInputElement.type")}}