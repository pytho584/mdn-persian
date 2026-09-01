---
title: "HTMLAreaElement: ping property"
short-title: ping
slug: Web/API/HTMLAreaElement/ping
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.ping
---

{{ApiRef("HTML DOM")}}

ویژگی **`ping`** در رابط {{domxref("HTMLAreaElement")}} یک لیست جدا شده با فاصله از URLها است. هنگامی که پیوند دنبال می‌شود، مرورگر درخواست‌های {{HTTPMethod("POST")}} با بدنه‌ی PING به آن URLها ارسال می‌کند.

این ویژگی منعکس‌کننده‌ی ویژگی `ping` عنصر {{HTMLElement("area")}} است.

> [!NOTE]
> این ویژگی در فایرفاکس کارایی ندارد و ممکن است استفاده از آن به دلیل نگرانی‌های حریم خصوصی و امنیتی محدود شود.

## مثال

```html
<map name="example-map" id="example-map">
  <area
    href="https://example.com"
    ping="https://example-tracking.com https://example-analytics.com"
    alt="example" />
</map>
```

```js
const areaCollection = document.getElementById("example-map").areas;
console.log(areaCollection[0].ping); // خروجی: "https://example-tracking.com https://example-analytics.com"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLAnchorElement.ping")}}