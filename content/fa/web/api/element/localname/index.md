---
title: "Element: localName property"
short-title: localName
slug: Web/API/Element/localName
page-type: web-api-instance-property
browser-compat: api.Element.localName
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`Element.localName`** بخش محلی از نام واجد شرایط (qualified name) یک عنصر را بازمی‌گرداند.

## مقدار

یک رشته (string) که بخش محلی نام واجد شرایط عنصر را نشان می‌دهد.

## مثال‌ها

(باید با نوع محتوای XML ارائه شود، مانند `text/xml` یا `application/xhtml+xml`.)

```xml
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:svg="http://www.w3.org/2000/svg">
<head>
  <script><![CDATA[
function test() {
  const text = document.getElementById("text");
  const circle = document.getElementById("circle");

  text.value = `<svg:circle> has:
localName = "${circle.localName}"
namespaceURI = "${circle.namespaceURI}"`;
}
  ]]></script>
</head>
<body onload="test()">
  <svg:svg version="1.1"
    width="100px" height="100px"
    viewBox="0 0 100 100">
    <svg:circle cx="50" cy="50" r="30" fill="#aaaaaa" id="circle"/>
  </svg:svg>
  <textarea id="text" rows="4" cols="55"/>
</body>
</html>
```

## یادداشت‌ها

نام محلی یک گره، بخشی از نام واجد شرایط گره است که بعد از دونقطه می‌آید. نام‌های واجد شرایط معمولاً در XML به‌عنوان بخشی از فضای نام (namespace) اسناد XML خاص استفاده می‌شوند. برای مثال، در نام واجد شرایط `comm:partners`، نام محلی `partners` و پیشوند `comm` است:

```xml
<comm:business id="soda_shop" type="brick_n_mortar" xmlns:comm="http://example.com/comm">
  <comm:partners>
    <comm:partner id="1001">Tony's Syrup Warehouse
    </comm:partner>
  </comm:partner>
</comm:business>
```

> [!NOTE]
> در حالی که این ویژگی نام را با همان حالت حروف ذخیره‌شده در DOM داخلی بازمی‌گرداند که کوچک است، توجه داشته باشید که ویژگی {{domxref("element.tagName","tagName")}} برای عناصر HTML در DOMهای HTML، نام را با حروف بزرگ بازمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.tagName")}}
- {{domxref("Element.namespaceURI")}}
- {{domxref("Element.prefix")}}
- {{domxref("Attr.localName")}}