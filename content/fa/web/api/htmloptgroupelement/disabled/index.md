---
title: "HTMLOptGroupElement: disabled property"
---

---
title: "HTMLOptGroupElement: disabled property"
short-title: disabled
slug: Web/API/HTMLOptGroupElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLOptGroupElement.disabled
---

{{ APIRef("HTML DOM") }}

ویژگی **`disabled`** از رابط {{domxref("HTMLOptGroupElement")}} یک مقدار بولی است که ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/optgroup#disabled) عنصر {{htmlelement("optgroup")}} را منعکس می‌کند و نشان می‌دهد که آیا کنترل غیرفعال است یا نه.

هنگامی که غیرفعال باشد، عناصر فرعی {{htmlelement("option")}} که فرزندان عنصر `<optgroup>` هستند، غیرقابل استفاده، غیرقابل کلیک و غیرقابل انتخاب می‌شوند. این `<option>`های غیرفعال با انتخابگر {{cssxref(":disabled")}} مطابقت می‌کنند، حتی اگر مقدار ویژگی `disabled` آن‌ها `false` باشد.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const optionGroup = document.getElementById("groupB");
console.log(optionGroup.disabled);
optionGroup.disabled = true;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled) در HTML
- شبه‌کلاس‌های CSS {{cssxref(":disabled")}} و {{cssxref(":enabled")}}