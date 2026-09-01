---
title: "HTMLFieldSetElement: disabled property"
short-title: disabled
slug: Web/API/HTMLFieldSetElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLFieldSetElement.disabled
---

{{ APIRef("HTML DOM") }}

ویژگی **`disabled`** در رابط {{domxref("HTMLFieldSetElement")}} یک مقدار بولی است که ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/fieldset#disabled) عنصر {{htmlelement("fieldset")}} را بازتاب می‌دهد و نشان می‌دهد که آیا کنترل غیرفعال است یا نه.

هنگامی که غیرفعال باشد، تمام عناصر کنترلی فرم که از نوادگان عنصر `<fieldset>` هستند، به‌جز عناصری که از نوادگان فرزند {{htmlelement("legend")}} آن `<fieldset>` باشند (در صورت وجود)، غیرفعال می‌شوند. یک عنصر غیرفعال غیرقابل‌استفاده و غیرقابل‌کلیک است و با انتخابگر {{cssxref(":disabled")}} مطابقت دارد، حتی اگر مقدار ویژگی `disabled` آن false باشد.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const fs = document.getElementById("billing-address");
console.log(fs.disabled);
fs.disabled = true;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- ویژگی HTML [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
- شبه‌کلاس‌های CSS {{cssxref(":disabled")}} و {{cssxref(":enabled")}}