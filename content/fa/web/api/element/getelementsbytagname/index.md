---
title: "Element: getElementsByTagName() method"
short-title: getElementsByTagName()
slug: Web/API/Element/getElementsByTagName
page-type: web-api-instance-method
browser-compat: api.Element.getElementsByTagName
---

{{ APIRef("DOM") }}

متد **`Element.getElementsByTagName()`** یک {{domxref("HTMLCollection")}} زنده از عناصری را بازمی‌گرداند که [نام تگ](/en-US/docs/Web/API/Element/tagName) مشخصی دارند.

همهٔ نوادگان عنصر مشخص‌شده جست‌وجو می‌شوند، اما خودِ عنصر جست‌وجو نمی‌شود. فهرست بازگشتی _زنده_ است و به‌طور خودکار با درخت DOM به‌روز می‌شود. بنابراین، اگر DOM در فاصلهٔ بین فراخوانی‌ها تغییر کند، نیازی به فراخوانی دوبارهٔ `Element.getElementsByTagName()` با همان عنصر و همان آرگومان‌ها نیست.

وقتی `getElementsByTagName` روی یک عنصر HTML در یک سند HTML فراخوانی می‌شود، پیش از جست‌وجو، آرگومان را به حروف کوچک تبدیل می‌کند. این رفتار هنگام تلاش برای یافتن عناصر SVG با نام {{Glossary("camel_case", "camel-cased")}} (مانند [`<linearGradient>`](/en-US/docs/Web/SVG/Reference/Element/linearGradient)) در یک سند HTML نامطلوب است. در عوض، از {{ domxref("Element.getElementsByTagNameNS()") }} استفاده کنید، زیرا حروف بزرگ و کوچک نام تگ را حفظ می‌کند.

`Element.getElementsByTagName` مشابه {{domxref("Document.getElementsByTagName()")}} است، با این تفاوت که فقط عناصری را جست‌وجو می‌کند که از نوادگان عنصر مشخص‌شده هستند.

## سینتکس

```js-nolint
getElementsByTagName(tagName)
```

### پارامترها

- `tagName`
  - : نام واجد شرایط (qualified name) که باید جست‌وجو شود. رشتهٔ ویژهٔ `"*"` نمایانگر همهٔ عناصر است. برای سازگاری با XHTML باید از حروف کوچک استفاده شود.

### مقدار بازگشتی

یک {{domxref("HTMLCollection")}} _زنده_ از عناصر با نام تگ منطبق، به ترتیبی که ظاهر می‌شوند. اگر هیچ عنصری یافت نشود، `HTMLCollection` خالی است.

## مثال‌ها

```js
// Check the status of each data cell in a table
const table = document.getElementById("forecast-table");
const cells = table.getElementsByTagName("td");

for (const cell of cells) {
  const status = cell.getAttribute("data-status");
  if (status === "open") {
    // Grab the data
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}