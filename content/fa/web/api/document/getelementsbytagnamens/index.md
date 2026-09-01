```
---
title: "Document: getElementsByTagNameNS() method"
short-title: getElementsByTagNameNS()
slug: Web/API/Document/getElementsByTagNameNS
page-type: web-api-instance-method
browser-compat: api.Document.getElementsByTagNameNS
---

{{APIRef("DOM")}}

فهرستی از عناصر با نام تگ داده‌شده که به فضای نام (namespace) داده‌شده تعلق دارند را برمی‌گرداند. کل سند، از جمله گره ریشه، جستجو می‌شود.

## سینتکس

```js-nolint
getElementsByTagNameNS(namespace, name)
```

### پارامترها

- `namespace`
  - : URI فضای نام عناصری که به دنبال آنها هستید (به {{domxref("Element.namespaceURI", "element.namespaceURI")}} مراجعه کنید).
- `name`
  - : یا نام محلی (local name) عناصری که به دنبال آنها هستید، یا مقدار ویژهٔ `*` که با همه عناصر مطابقت دارد (به {{domxref("Element.localName", "element.localName")}} مراجعه کنید).

    > [!NOTE]
    > برخلاف {{domxref("document.getElementsByTagName()")}}، پارامترهای `getElementsByTagNameNS()` به بزرگی/کوچکی حروف حساس هستند.

### مقدار بازگشتی

یک {{DOMxRef("HTMLCollection")}} زنده از عناصر یافت‌شده، به ترتیبی که در درخت DOM ظاهر می‌شوند.

## مثال‌ها

در مثال زیر، `getElementsByTagNameNS` از یک عنصر والد مشخص شروع می‌کند و از آن عنصر والد به‌صورت بازگشتی و از بالا به پایین در DOM جستجو می‌کند و به دنبال عناصر فرزندی می‌گردد که با پارامتر تگ `name` مطابقت دارند.

توجه داشته باشید که وقتی گره‌ای که `getElementsByTagName` روی آن فراخوانی می‌شود، گرهٔ `document` نباشد، در واقع از متد {{domxref("element.getElementsByTagNameNS")}} استفاده می‌شود.

برای استفاده از مثال زیر، کافی است آن را در یک فایل جدید با پسوند `.xhtml` کپی و جای‌گذاری کنید.

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
  const allParas = document.getElementsByTagNameNS(
    "http://www.w3.org/1999/xhtml",
    "p",
  );
  const num = allParas.length;
  alert(`There are ${num} &lt;p&gt; elements in this document`);
}

function div1ParaElems() {
  const div1 = document.getElementById("div1");
  const div1Paras = div1.getElementsByTagNameNS(
    "http://www.w3.org/1999/xhtml",
    "p",
  );
  const num = div1Paras.length;
  alert(`There are ${num} &lt;p&gt; elements in div1 element`);
}

function div2ParaElems() {
  const div2 = document.getElementById("div2");
  const div2Paras = div2.getElementsByTagNameNS(
    "http://www.w3.org/1999/xhtml",
    "p",
  );
  const num = div2Paras.length;
  alert(`There are ${num} &lt;p&gt; elements in div2 element`);
}

document.getElementById("btn1").addEventListener("click", getAllParaElems);
document.getElementById("btn2").addEventListener("click", div1ParaElems);
document.getElementById("btn3").addEventListener("click", div2ParaElems);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("Element.getElementsByTagNameNS()")}}
```