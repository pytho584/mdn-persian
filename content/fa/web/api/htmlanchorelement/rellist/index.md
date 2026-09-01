---
title: "HTMLAnchorElement: relList property"
short-title: relList
slug: Web/API/HTMLAnchorElement/relList
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.relList
---

{{APIRef("HTML DOM")}}

خاصیت فقط‌خواندنی **`relList`** در {{domxref("HTMLAnchorElement")}} یک شیء زندهٔ {{domxref("DOMTokenList")}} برمی‌گرداند که شامل مجموعه‌ای از انواع پیوند است و رابطه بین منبع نمایش‌داده‌شده توسط عنصر {{HTMLElement("a")}} و سند فعلی را مشخص می‌کند. این خاصیت، ویژگی محتوایی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) عنصر {{HTMLElement("a")}} را منعکس می‌کند.

## مقدار

یک شیء زندهٔ {{domxref("DOMTokenList")}}.

اگرچه خود خاصیت `relList` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، همچنان می‌توانید مستقیماً به خاصیت `relList` مقدار اختصاص دهید که معادل تخصیص مقدار به خاصیت {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```js
const anchors = document.getElementsByTagName("a");
for (const anchor of anchors) {
  const list = anchor.relList;
  console.log(
    `New anchor node found with ${list.length} link types in relList.`,
  );
  list.forEach((relValue) => {
    console.log(relValue);
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- خاصیت معادل در {{HTMLElement("area")}} و {{HTMLElement("link")}}، یعنی
  {{domxref("HTMLAreaElement.relList")}} و {{domxref("HTMLLinkElement.relList")}}.
- همان فهرست اما به‌صورت نشانه‌های جدا شده با فاصله در یک رشته:
  {{domxref("HTMLAnchorElement.rel")}}