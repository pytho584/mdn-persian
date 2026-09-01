---
title: "HTMLLinkElement: relList property"
---

---
title: "HTMLLinkElement: relList property"
short-title: relList
slug: Web/API/HTMLLinkElement/relList
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.relList
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`relList`** در {{domxref("HTMLLinkElement")}} یک شیء زندهٔ {{domxref("DOMTokenList")}} برمی‌گرداند که شامل مجموعهٔ انواع پیوند است و رابطهٔ بین منبعِ نمایش‌داده‌شده توسط عنصر {{HTMLElement("link")}} و سند کنونی را نشان می‌دهد. این ویژگی، ویژگی محتوایی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) عنصر {{HTMLElement("link")}} را بازتاب می‌دهد.

## مقدار

یک شیء زندهٔ {{domxref("DOMTokenList")}}.

با اینکه خود ویژگی `relList` به این معنا فقط‌خواندنی است که نمی‌توانید شیء {{domxref("DOMTokenList")}} را جایگزین کنید، همچنان می‌توانید مستقیماً به `relList` مقدار بدهید که معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء {{domxref("DOMTokenList")}} را با استفاده از روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```js
const links = document.getElementsByTagName("link");
for (const link of links) {
  console.log("New link found.");
  link.relList.forEach((relEntry) => {
    console.log(relEntry);
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی معادل روی عناصر {{HTMLElement("a")}} و {{HTMLElement("area")}}، یعنی {{domxref("HTMLAnchorElement.relList")}} و {{domxref("HTMLAreaElement.relList")}}.
- همان فهرست، اما به‌صورت توکن‌های جدا شده با فاصله در یک رشته: {{domxref("HTMLLinkElement.rel")}}