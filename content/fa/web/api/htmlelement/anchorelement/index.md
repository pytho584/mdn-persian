---
title: "HTMLElement: anchorElement property"
---

---
title: "HTMLElement: anchorElement property"
short-title: anchorElement
slug: Web/API/HTMLElement/anchorElement
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.HTMLElement.anchorElement
---

{{APIRef("HTML DOM")}}{{Non-standard_Header}}{{SeeCompatTable}}

ویژگی **`anchorElement`** از رابط {{domxref("HTMLElement")}} مرجعی به عنصر لنگرِ آن عنصر برمی‌گرداند. این ویژگی فقط در مورد عناصری کار می‌کند که از طریق صفت HTML [`anchor`](/en-US/docs/Web/HTML/Reference/Global_attributes/anchor) به لنگر خود مرتبط شده‌اند، نه عناصری که از طریق ویژگی‌های CSS {{cssxref("anchor-name")}} و {{cssxref("position-anchor")}} به لنگر خود مرتبط شده‌اند.

## مقدار

یک نمونه از {{domxref("HTMLElement")}} که عنصر لنگرِ عنصر را نمایش می‌دهد؛ یا اگر عنصر لنگری نداشته باشد، مقدار `null` برمی‌گرداند.

## مثال‌ها

### استفادهٔ پایه

این مثال یک عنصر را در HTML به یک لنگر مرتبط می‌کند و با استفاده از جاوااسکریپت، مرجعی به عنصر لنگر را بازیابی می‌کند.

#### HTML

در کد HTML، یک عنصر {{htmlelement("div")}} با [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) برابر با `example-anchor` می‌سازیم. این عنصر، عنصر لنگر ما خواهد بود. سپس یک `<div>` دیگر با کلاس `infobox` و صفت [`anchor`](/en-US/docs/Web/HTML/Reference/Global_attributes/anchor) که روی `example-anchor` تنظیم شده است اضافه می‌کنیم. این کار، `<div>` اول را به‌عنوان لنگرِ `<div>` دوم تعیین می‌کند و آن دو را به یکدیگر مرتبط می‌سازد.

همچنین یک عنصر {{htmlelement("p")}} برای نمایش نتایج اضافه می‌کنیم.

```html
<div class="anchor" id="example-anchor">⚓︎</div>

<div class="infobox" anchor="example-anchor">
  <p>This is an information box.</p>
</div>

<p class="output"></p>
```

#### جاوااسکریپت

با استفاده از جاوااسکریپت، ارجاع‌هایی به عنصر موقعیت‌داده‌شده (positioned element) و عنصر خروجی می‌گیریم و سپس مقدارِ `id` مرتبط با ویژگی `anchorElement` عنصر موقعیت‌داده‌شده را در خروجی چاپ می‌کنیم تا نشان دهیم عنصر لنگر، همان `anchorElement` عنصر موقعیت‌داده‌شده است.

```js
const posElem = document.querySelector(".infobox");
const outputElem = document.querySelector(".output");

try {
  outputElem.textContent = `The positioned element's anchor element is the ${posElem.anchorElement.id}.`;
} catch (e) {
  outputElem.textContent = `Your browser doesn't support the anchorElement property.`;
}
```

#### نتیجه

نتیجه به این صورت است.

{{EmbedLiveSample("Basic usage", "100%", 110)}}

## مشخصات

این ویژگی در حال حاضر بخشی از مشخصات HTML نیست. بحث مربوط به افزودن ویژگی `anchorElement` را در [https://github.com/whatwg/html/pull/9144](https://github.com/whatwg/html/pull/9144) بخوانید.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- صفت HTML [`anchor`](/en-US/docs/Web/HTML/Reference/Global_attributes/anchor)
- ویژگی‌های CSS {{cssxref("anchor-name")}} و {{cssxref("position-anchor")}}
- ماژول [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning)