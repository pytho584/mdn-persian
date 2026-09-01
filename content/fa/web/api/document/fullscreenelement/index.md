---
title: "Document: fullscreenElement property"
short-title: fullscreenElement
slug: Web/API/Document/fullscreenElement
page-type: web-api-instance-property
browser-compat: api.Document.fullscreenElement
---

{{ApiRef("Fullscreen API")}}

ویژگی فقط-خواندنی **`Document.fullscreenElement`**، عنصر {{domxref("Element")}}ای را برمی‌گرداند که در حال حاضر در این سند در حالت تمام‌صفحه نمایش داده می‌شود؛ یا اگر حالت تمام‌صفحه در حال استفاده نباشد، مقدار `null` را برمی‌گرداند.

اگرچه این ویژگی فقط-خواندنی است، اما در صورت تغییر آن (حتی در حالت سخت‌گیرانه) خطایی پرتاب نمی‌کند؛ ست‌کننده‌ی آن هیچ کاری انجام نمی‌دهد و نادیده گرفته می‌شود.

## مقدار

شیء {{domxref("Element")}} که در حال حاضر در حالت تمام‌صفحه قرار دارد؛ اگر حالت تمام‌صفحه در حال حاضر توسط `document` استفاده نشود، مقدار بازگشتی `null` است. اگر چندین عنصر در حالت تمام‌صفحه باشند، بالاترین عنصر (عنصری که آخرین بار درخواست شده) بازگردانده می‌شود.

## مثال‌ها

این مثال تابعی به نام `isVideoInFullscreen()` ارائه می‌دهد که مقدار بازگشتی `fullscreenElement` را بررسی می‌کند؛ اگر سند در حالت تمام‌صفحه باشد (`fullscreenElement` برابر با `null` نباشد) و {{domxref("Node.nodeName", "nodeName")}} عنصر تمام‌صفحه، `VIDEO` باشد — که نشان‌دهنده‌ی یک عنصر {{HTMLElement("video")}} است — تابع مقدار `true` برمی‌گرداند و نشان می‌دهد که ویدئو در حالت تمام‌صفحه است.

```js
function isVideoInFullscreen() {
  if (document.fullscreenElement?.nodeName === "VIDEO") {
    return true;
  }
  return false;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API)
- [راهنمای استفاده از API تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API/Guide)
- {{ domxref("Element.requestFullscreen()") }}
- {{ domxref("Document.exitFullscreen()") }}
- {{ cssxref(":fullscreen") }} و {{cssxref("::backdrop")}}
- ویژگی [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen) عنصر {{HTMLElement("iframe")}}