---
title: "HTMLAnchorElement: attributionSourceId property"
short-title: attributionSourceId
slug: Web/API/HTMLAnchorElement/attributionSourceId
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.attributionSourceId
---

{{APIRef("HTML DOM")}}

ویژگی **`attributionSourceId`** از رابط {{domxref("HTMLAnchorElement")}}، مقدار ویژگی HTML `attributionsourceid` را روی یک عنصر {{htmlelement("a")}} دریافت و تنظیم می‌کند.

`attributionSourceId` به‌عنوان بخشی از مشخصات [Private Click Measurement](https://privacycg.github.io/private-click-measurement/) برای شناسایی محتوایی استفاده می‌شود که هنگام دنبال کردن پیوند به سایت دیگر کلیک شده است.

## مقدار

یک عدد. مقادیر معتبر برای اندازه‌گیری کلیک خصوصی بین `0` و `255` است. مقدار پیش‌فرض `0` است. مقادیر خارج از این محدوده هنگام تنظیم ویژگی خطایی ایجاد نمی‌کنند، اما توسط مرورگر برای اهداف انتساب نادیده گرفته می‌شوند.

## مثال‌ها

### تنظیم شناسه منبع انتساب روی یک پیوند

```html
<a
  id="ad-link"
  href="https://example.com"
  attributiondestination="https://example.com">
  Click to visit our shop
</a>
```

```js
const adLink = document.getElementById("ad-link");
adLink.attributionSourceId = 17;

console.log(adLink.attributionSourceId); // 17
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAnchorElement")}}
- عنصر HTML {{htmlelement("a")}}
- مشخصات [Private Click Measurement](https://privacycg.github.io/private-click-measurement/)