---
title: "HTMLAreaElement: rel property"
short-title: rel
slug: Web/API/HTMLAreaElement/rel
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.rel
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLAreaElement.rel`** صفت [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) را منعکس می‌کند. این یک رشته است که شامل فهرست جداشده با فاصله از انواع پیوند است و رابطهٔ میان سند جاری و منبعی را نشان می‌دهد که عنصر {{HTMLElement("area")}} نمایندهٔ آن است.

## مقدار

یک رشته.

## مثال‌ها

```js
const areas = document.getElementsByTagName("area");
for (const area of areas) {
  console.log(`Rel: ${area.rel}`);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی معادل در عناصر {{HTMLElement("a")}} و {{HTMLElement("link")}}:
  {{domxref("HTMLAnchorElement.rel")}} و {{domxref("HTMLLinkElement.rel")}}.
- دقیقاً همان فهرست، اما به‌صورت توکن‌ها: {{domxref("HTMLAreaElement.relList")}}