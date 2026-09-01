---
title: "HTMLAnchorElement: rel property"
short-title: rel
slug: Web/API/HTMLAnchorElement/rel
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.rel
---

{{APIRef("HTML DOM")}}

خاصیت **`HTMLAnchorElement.rel`** ویژگی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) را بازتاب می‌دهد. مقدار آن رشته‌ای است که فهرستی از انواع پیوند (link types) را شامل می‌شود؛ این انواع با فاصله از هم جدا شده‌اند و رابطهٔ بین منبعِ نمایش‌داده‌شده توسط عنصر {{HTMLElement("a")}} و سندِ فعلی را نشان می‌دهند.

## مقدار

یک رشته.

## مثال‌ها

```js
const anchors = document.getElementsByTagName("a");
for (const anchor of anchors) {
  alert(`Rel: ${anchor.rel}`);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- خاصیت معادل در {{HTMLElement("area")}} و {{HTMLElement("link")}}، یعنی {{domxref("HTMLAreaElement.rel")}} و {{domxref("HTMLLinkElement.rel")}}.
- دقیقاً همان فهرست، اما به‌صورت توکن‌ها: {{domxref("HTMLAnchorElement.relList")}}