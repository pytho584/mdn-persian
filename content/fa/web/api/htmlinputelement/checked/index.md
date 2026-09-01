---
title: "HTMLInputElement: checked property"
short-title: checked
slug: Web/API/HTMLInputElement/checked
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.checked
---

{{ APIRef("HTML DOM") }}

ویژگی **`checked`** در رابط {{DOMxRef("HTMLInputElement")}} وضعیتِ علامت‌خورده بودن فعلی عنصر را مشخص می‌کند؛ یعنی اینکه آیا کنترل فرم علامت خورده است یا خیر.

ویژگی بولی `checked` برای نوع ورودی‌های `radio` ([`<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/radio)) و `checkbox` ([`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)) کاربرد دارد.

وجود ویژگی HTML [`checked`](/en-US/docs/Web/HTML/Reference/Elements/input#checked) نشان می‌دهد که چک‌باکس به‌صورت پیش‌فرض علامت خورده است. اما نشان‌دهنده این نیست که آیا این چک‌باکس در حال حاضر علامت خورده است یا نه: اگر وضعیت چک‌باکس تغییر کند، این ویژگی محتوایی (content attribute) تغییر را منعکس نمی‌کند؛ فقط ویژگی IDL به‌نام `checked` در `HTMLInputElement` به‌روزرسانی می‌شود. ویژگی `checked` توسط ویژگی {{domxref("HTMLInputElement.defaultChecked", "defaultChecked")}} منعکس می‌شود.

وقتی ویژگی `checked` یک ورودی رادیویی `true` باشد، تمام ورودی‌های رادیویی دیگری که {{DOMxRef("HTMLInputElement.name", "name")}} یکسانی دارند، `false` می‌شوند. اگر هر دکمه رادیویی در گروهی از دکمه‌های رادیویی با نام یکسان، {{DOMxRef("HTMLInputElement.required", "required")}} باشد، تا زمانی که حداقل یک دکمه در گروه `checked` باشد، ویژگیِ فقط‌خواندنی {{domxref('ValidityState.valueMissing','valueMissing')}} در شیء {{domxref('ValidityState')}} برای هر دکمه رادیویی در آن گروه، `false` خواهد بود.

مقدار یک چک‌باکس فقط زمانی در داده‌های ارسالی هنگام ارسال فرم گنجانده می‌شود که `checked` برابر با `true` باشد. مقدار ویژگی {{DOMxRef("HTMLInputElement.indeterminate")}} هیچ تأثیری بر مقدار `checked` چک‌باکس ندارد.

## مقدار

یک مقدار بولی (boolean).

## مثال‌ها

```js
const inputElement = document.getElementById("contactMail");
console.log(inputElement.checked);
inputElement.checked = true;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.validity")}}
- شبه‌کلاس {{cssxref(":checked")}}