---
title: "HTMLSelectElement: size property"
---

---
title: "HTMLSelectElement: size property"
short-title: size
slug: Web/API/HTMLSelectElement/size
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.size
---

{{ APIRef("HTML DOM") }}

خاصیت **`size`** در رابط {{DOMxRef("HTMLSelectElement")}} تعداد گزینه‌ها یا ردیف‌هایی را که باید در یک زمان قابل مشاهده باشند مشخص می‌کند. این خاصیت بازتاب‌دهندهٔ ویژگی [`size`](/en-US/docs/Web/HTML/Reference/Elements/select#size) عنصر {{htmlelement("select")}} است. اگر این ویژگی تنظیم نشده باشد، مقدار آن `0` است.

> [!NOTE]
> به‌طور پیش‌فرض، یک `<select>` تنها یک ردیف را نمایش می‌دهد، مگر اینکه {{DOMXref("HTMLSelectElement.multiple", "multiple")}} برابر با `true` باشد که در آن صورت چهار ردیف نمایش داده می‌شود؛ با این حال، مقدار پیش‌فرض خاصیت `size` برابر با `0` است.

## Value

یک عدد.

## Examples

```js
const selectElement = document.getElementById("fruits");
console.log(selectElement.size);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("select")}}
- {{HTMLElement("option")}}
- {{DOMXref("HTMLSelectElement.selectedOptions")}}
- {{DOMXref("HTMLSelectElement.length")}}