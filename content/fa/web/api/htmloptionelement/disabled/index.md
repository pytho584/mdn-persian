---
title: "HTMLOptionElement: disabled property"
short-title: disabled
slug: Web/API/HTMLOptionElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLOptionElement.disabled
---

{{ APIRef("HTML DOM") }}

ویژگی **`disabled`** در {{domxref("HTMLOptionElement")}} یک مقدار بولین است که نشان می‌دهد آیا عنصر {{htmlelement("option")}} برای انتخاب در دسترس نیست یا خیر. این ویژگی مقدارِ ویژگی `disabled` در HTML را بازتاب می‌دهد (برای اطلاعات بیشتر به [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/option#disabled) مراجعه کنید).

این ویژگی، مقدار صفت `disabled` را روی خودِ عنصر `<option>` بازتاب می‌دهد. اگر یک گزینه به این دلیل غیرفعال باشد که فرزند یک عنصر {{HTMLElement("optgroup")}} غیرفعال است، مقدار `true` مربوط به ویژگی {{domxref("HTMLOptGroupElement.disabled")}} به خودِ گزینه به ارث نمی‌رسد.

## مقدار

یک مقدار بولین.

## مثال‌ها

### HTML

```html
<label for="drink-options">انتخاب نوشیدنی:</label>
<select id="drink-options">
  <option value="water">آب</option>
  <option value="lemonade">لیموناد</option>
  <option value="beer">آبجو</option>
  <option value="whisky" disabled>ویسکی</option>
</select>
```

### JavaScript

```js
const drinks = document.querySelectorAll("#drink-options option");
console.log(drinks[0].disabled); // false
console.log(drinks[3].disabled); // true
drinks[1].disabled = true; // گزینه آبجو را غیرفعال می‌کند
```

### نتیجه

{{EmbedLiveSample('Examples')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("option")}}
- {{HTMLElement("select")}}
- {{HTMLElement("optgroup")}}
- {{DOMxRef("HTMLSelectElement.disabled")}}
- {{DOMxRef("HTMLOptGroupElement.disabled")}}
- {{DOMxRef("HTMLOptionElement.selected")}}
- {{DOMxRef("HTMLOptionElement.index")}}
- {{DOMxRef("HTMLOptionsCollection")}}
- {{cssxref(":disabled")}}