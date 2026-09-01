---
title: "HTMLLinkElement: rel property"
short-title: rel
slug: Web/API/HTMLLinkElement/rel
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.rel
---

{{APIRef("HTML DOM")}}

ویژگی **`rel`** از رابط {{domxref("HTMLLinkElement")}} منعکس‌کنندهٔ ویژگی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) است. این یک رشته شامل فهرستی جدا شده با فاصله از انواع پیوند است که رابطه بین منبع نمایش‌داده‌شده توسط عنصر {{HTMLElement("link")}} و سند فعلی را نشان می‌دهد.

رایج‌ترین استفاده از این ویژگی مشخص کردن پیوند به یک شیوه‌نامهٔ خارجی است:
ویژگی به `stylesheet` تنظیم می‌شود و ویژگی [`href`](/en-US/docs/Web/HTML/Reference/Elements/link#href) به URL یک شیوه‌نامهٔ خارجی برای قالب‌بندی صفحه تنظیم می‌گردد.

## مقدار

یک رشته.

## مثال‌ها

```js
const links = document.getElementsByTagName("link");
for (const link of links) {
  console.log(link);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی معادل در {{HTMLElement("a")}} و {{HTMLElement("area")}}، {{domxref("HTMLAnchorElement.rel")}} و {{domxref("HTMLAreaElement.rel")}}.
- همین فهرست به صورت توکن‌ها: {{domxref("HTMLLinkElement.relList")}}