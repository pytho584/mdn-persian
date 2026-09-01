---
title: "Element: getElementsByTagNameNS() method"
short-title: getElementsByTagNameNS()
slug: Web/API/Element/getElementsByTagNameNS
page-type: web-api-instance-method
browser-compat: api.Element.getElementsByTagNameNS
---

{{APIRef("DOM")}}

روش **`Element.getElementsByTagNameNS()`** یک {{domxref("HTMLCollection")}} زنده از عناصری را بازمی‌گرداند که دارای نام تگ داده شده و متعلق به فضای نام داده شده هستند. این روش مشابه {{Domxref("Document.getElementsByTagNameNS")}} است، با این تفاوت که جستجوی آن به فرزندان عنصر مشخص شده محدود می‌شود.

## نحو

```js-nolint
getElementsByTagNameNS(namespaceURI, localName)
```

### پارامترها

- `namespaceURI`
  - : URI فضای نام عناصری که باید جستجو شوند (به {{domxref("Element.namespaceURI")}} و {{domxref("Attr.namespaceURI")}} مراجعه کنید). برای مثال، اگر نیاز به جستجوی عناصر XHTML دارید، از URI فضای نام XHTML یعنی `http://www.w3.org/1999/xhtml` استفاده کنید.
- `localName`
  - : یا نام محلی عناصری که باید جستجو شوند، یا مقدار ویژه `"*"` که با همه عناصر مطابقت دارد (به {{domxref("Element.localName")}} و {{domxref("Attr.localName")}} مراجعه کنید).

### مقدار بازگشتی

یک {{domxref("HTMLCollection")}} زنده از عناصر یافت شده به ترتیبی که در درخت ظاهر می‌شوند.

## مثال‌ها

```js
// Check the alignment on a number of cells in a table in an XHTML document.
const table = document.getElementById("forecast-table");
const cells = table.getElementsByTagNameNS(
  "http://www.w3.org/1999/xhtml",
  "td",
);

for (const cell of cells) {
  const axis = cell.getAttribute("axis");
  if (axis === "year") {
    // Grab the data
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}