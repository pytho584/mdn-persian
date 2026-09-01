---
title: "HTMLAreaElement: relList property"
short-title: relList
slug: Web/API/HTMLAreaElement/relList
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.relList
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`relList`** از {{domxref("HTMLAreaElement")}} یک شیء زندهٔ {{domxref("DOMTokenList")}} بازمی‌گرداند که شامل مجموعهٔ انواع پیوندها نشان‌دهندهٔ رابطه بین منبع نمایش‌داده‌شده توسط عنصر {{HTMLElement("area")}} و سند فعلی است. این ویژگی، ویژگی محتوایی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) عنصر {{HTMLElement("area")}} را منعکس می‌کند.

## مقدار

یک شیء زندهٔ {{domxref("DOMTokenList")}}.

اگرچه خود ویژگی `relList` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `relList` مقدار اختصاص دهید که معادل اختصاص مقدار به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```js
const areas = document.getElementsByTagName("area");

for (const area of areas) {
  console.log("New area found.");
  area.relList.forEach((relValue) => {
    console.log(relValue);
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- ویژگی معادل روی {{HTMLElement("a")}} و {{HTMLElement("link")}}،
  {{domxref("HTMLAnchorElement.relList")}} و {{domxref("HTMLLinkElement.relList")}}.
- همان فهرست اما به‌صورت توکن‌های جدا شده با فاصله در یک رشته:
  {{domxref("HTMLAreaElement.rel")}}