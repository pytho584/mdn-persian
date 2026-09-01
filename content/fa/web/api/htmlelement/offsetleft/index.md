---
title: "HTMLElement: offsetLeft property"
short-title: offsetLeft
slug: Web/API/HTMLElement/offsetLeft
page-type: web-api-instance-property
browser-compat: api.HTMLElement.offsetLeft
---

{{ APIRef("HTML DOM") }}

ویژگی فقط‌خواندنی **`offsetLeft`** در رابط {{domxref("HTMLElement")}} تعداد پیکسل‌هایی را برمی‌گرداند که _گوشهٔ بالا-چپ_ عنصر جاری نسبت به گرهٔ {{domxref("HTMLElement.offsetParent")}} به سمت چپ جابه‌جا شده است.

برای عناصر بلوکی، `offsetTop`، `offsetLeft`، `offsetWidth` و `offsetHeight`، جعبهٔ حاشیهٔ یک عنصر را نسبت به `offsetParent` توصیف می‌کنند.

با این حال، برای عناصر درون‌خطی (مانند `<span>`) که ممکن است از یک خط به خط بعد بپیچند، `offsetTop` و `offsetLeft` موقعیت _اولین_ جعبهٔ حاشیه را توصیف می‌کنند (برای دریافت عرض و ارتفاع آن از {{domxref("Element.getClientRects()")}} استفاده کنید)، در حالی که `offsetWidth` و `offsetHeight` ابعاد _جعبهٔ حاشیهٔ فراگیر_ را توصیف می‌کنند (برای دریافت موقعیت آن از {{domxref("Element.getBoundingClientRect()")}} استفاده کنید). بنابراین، جعبه‌ای با چپ، بالا، عرض و ارتفاع برابر با `offsetLeft`، `offsetTop`، `offsetWidth` و `offsetHeight`، برای یک `span` با متنی که به خط بعد رفته است، جعبهٔ مرزی (bounding box) نخواهد بود.

## مقدار

یک عدد صحیح.

## مثال‌ها

```js
const colorTable = document.getElementById("t1");
const tOLeft = colorTable.offsetLeft;

if (tOLeft > 5) {
  // large left offset: do something here
}
```

این مثال یک جملهٔ «بلند» را نشان می‌دهد که درون یک `div` با حاشیهٔ آبی به خط بعد می‌رود و یک جعبهٔ قرمز که ممکن است تصور شود مرزهای آن `<span>` را توصیف می‌کند.

![جمله‌ای با متن «Short span» که کاملاً داخل یک div با حاشیهٔ آبی قرار دارد. جمله‌ای با متن «Long span that wraps within this div». عبارت «long span that wraps» داخل یک جعبه با حاشیهٔ قرمز است و عبارت «within this div» داخل div با حاشیهٔ آبی قرار دارد.](offsetleft.jpg)

```html
<div class="span-container">
  <span>Short span.</span>
  <span id="long-span">Long span that wraps within this div.</span>
</div>

<div id="box"></div>
```

```css
.span-container {
  width: 300px;
  border-color: blue;
  border-style: solid;
  border-width: 1px;
}

#box {
  position: absolute;
  border-color: red;
  border-width: 1px;
  border-style: solid;
  z-index: 10;
}
```

```js
const box = document.getElementById("box");
const longSpan = document.getElementById("long-span");
box.style.left = `${longSpan.offsetLeft}${document.body.scrollLeft}px`;
box.style.top = `${longSpan.offsetTop}${document.body.scrollTop}px`;
box.style.width = `${longSpan.offsetWidth}px`;
box.style.height = `${longSpan.offsetHeight}px`;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("Element.clientLeft")}}
- {{domxref("Element.scrollLeft")}}
- {{domxref("HTMLElement.offsetHeight")}}
- {{domxref("HTMLElement.offsetWidth")}}
- {{domxref("HTMLElement.offsetTop")}}
- {{domxref("Element.getBoundingClientRect()")}}