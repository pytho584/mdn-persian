---
title: "Document: getElementsByTagName() method"
short-title: getElementsByTagName()
slug: Web/API/Document/getElementsByTagName
page-type: web-api-instance-method
browser-compat: api.Document.getElementsByTagName
---

{{APIRef("DOM")}}

متد **`getElementsByTagName`** از رابط {{domxref("Document")}} یک {{domxref("HTMLCollection")}} از عناصر با نام تگ مشخص‌شده برمی‌گرداند.

کل سند، از جمله گره ریشه، جستجو می‌شود. `HTMLCollection` برگشتی **زنده** است، به این معنی که خود را به‌طور خودکار به‌روزرسانی می‌کند تا با درخت DOM همگام بماند بدون نیاز به فراخوانی دوباره `document.getElementsByTagName()`.

## Syntax

```js-nolint
getElementsByTagName(name)
```

### Parameters

- `name`
  - : یک رشته که نام عناصر را مشخص می‌کند. رشته خاص `*` نشان‌دهنده همه عناصر است.

### Return value

یک {{domxref("HTMLCollection")}} زنده از عناصر یافت‌شده به ترتیبی که در درخت ظاهر می‌شوند.

## Examples

در مثال زیر، `getElementsByTagName()` از یک عنصر والد مشخص شروع می‌کند و به صورت بازگشتی از بالا به پایین در DOM از آن عنصر والد جستجو می‌کند و مجموعه‌ای از تمام عناصر فرزند که با پارامتر نام تگ مطابقت دارند را می‌سازد. این هم `document.getElementsByTagName()` و هم {{domxref("Element.getElementsByTagName()")}} را که از یک عنصر خاص در درخت DOM جستجو را شروع می‌کند، نشان می‌دهد.

کلیک روی دکمه‌ها از `getElementsByTagName()` برای شمارش عناصر پاراگراف فرزند یک والد خاص (یا خود سند یا یکی از دو عنصر {{HTMLElement("div")}} تو در تو) استفاده می‌کند.

```html
<p>Some outer text</p>
<p>Some outer text</p>

<div id="div1">
  <p>Some div1 text</p>
  <p>Some div1 text</p>
  <p>Some div1 text</p>

  <div id="div2">
    <p>Some div2 text</p>
    <p>Some div2 text</p>
  </div>
</div>

<p>Some outer text</p>
<p>Some outer text</p>

<button id="btn1">Show all p elements in document</button>
<br />
<button id="btn2">Show all p elements in div1 element</button>
<br />
<button id="btn3">Show all p elements in div2 element</button>
```

```css
body {
  border: solid green 3px;
}

#div1 {
  border: solid blue 3px;
}

#div2 {
  border: solid red 3px;
}
```

```js
function getAllParaElems() {
  const allParas = document.getElementsByTagName("p");
  const num = allParas.length;
  alert(`There are ${num} paragraph in this document`);
}

function div1ParaElems() {
  const div1 = document.getElementById("div1");
  const div1Paras = div1.getElementsByTagName("p");
  const num = div1Paras.length;
  alert(`There are ${num} paragraph in #div1`);
}

function div2ParaElems() {
  const div2 = document.getElementById("div2");
  const div2Paras = div2.getElementsByTagName("p");
  const num = div2Paras.length;
  alert(`There are ${num} paragraph in #div2`);
}

document.getElementById("btn1").addEventListener("click", getAllParaElems);
document.getElementById("btn2").addEventListener("click", div1ParaElems);
document.getElementById("btn3").addEventListener("click", div2ParaElems);
```

## Notes

هنگامی که روی یک سند HTML فراخوانی می‌شود، `getElementsByTagName()` آرگومان خود را قبل از انجام عملیات به حروف کوچک تبدیل می‌کند. این امر هنگام تلاش برای تطبیق عناصر SVG با نام‌های camel case در یک زیردرخت در یک سند HTML نامطلوب است. {{Domxref("document.getElementsByTagNameNS()")}} در این مورد مفید است. همچنین به [باگ فایرفاکس 499656](https://bugzil.la/499656) مراجعه کنید.

`document.getElementsByTagName()` مشابه {{domxref("Element.getElementsByTagName()")}} است، با این تفاوت که جستجوی آن کل سند را در بر می‌گیرد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element.getElementsByTagName()")}}
- {{domxref("document.getElementById()")}} برای بازگرداندن ارجاع به یک عنصر با `id` آن
- {{domxref("document.getElementsByName()")}} برای بازگرداندن ارجاع به یک عنصر با `name` آن
- {{domxref("document.querySelector()")}} برای انتخابگرهای قدرتمند با استفاده از کوئری‌هایی مانند `'div.myclass'`