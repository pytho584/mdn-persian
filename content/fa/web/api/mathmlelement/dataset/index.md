---
title: "MathMLElement: dataset property"
short-title: dataset
slug: Web/API/MathMLElement/dataset
page-type: web-api-instance-property
browser-compat: api.MathMLElement.dataset
---

{{APIRef("MathML")}}

ویژگی فقط خواندنی **`dataset`** از رابط {{DOMxRef("MathMLElement")}} دسترسی خواندن/نوشتن به [ویژگی‌های داده سفارشی](/en-US/docs/Web/MathML/Reference/Global_attributes/data-*) (`data-*`) روی عناصر را فراهم می‌کند. این ویژگی یک نگاشت از رشته‌ها ({{domxref("DOMStringMap")}}) را با یک ورودی برای هر ویژگی `data-*` نمایش می‌دهد.

خود ویژگی `dataset` قابل خواندن است، اما نمی‌توان مستقیماً در آن نوشت. در عوض، تمام نوشتن‌ها باید روی ویژگی‌های منفرد درون `dataset` انجام شود که به نوبه خود نشان‌دهنده ویژگی‌های داده هستند.

## مقدار

یک {{domxref("DOMStringMap")}}.

## مثال‌ها

```html
<div>
  <math>
    <msup id="equation" data-value="-1" data-equation="euler">
      <mi>e</mi>
      <mrow><mi>i</mi> <mi>π</mi></mrow>
    </msup>
    <mo>+</mo>
    <mn>1</mn>
    <mo>=</mo>
    <mn>0</mn>
  </math>
</div>
```

```js
const el = document.querySelector("#equation");

console.log(el.dataset.value); // "-1"
console.log(el.dataset.equation); // "euler"
```

### نتیجه

{{EmbedLiveSample("dataset",100,100)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.dataset")}}
- [`data-*`](/en-US/docs/Web/MathML/Reference/Global_attributes/data-*)
- [استفاده از ویژگی‌های داده](/en-US/docs/Web/HTML/How_to/Use_data_attributes)