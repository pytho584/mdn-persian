---
title: "Document: fullscreenEnabled property"
short-title: fullscreenEnabled
slug: Web/API/Document/fullscreenEnabled
page-type: web-api-instance-property
browser-compat: api.Document.fullscreenEnabled
---

{{APIRef("Fullscreen API")}}

خصوصیتِ فقط‌خواندنی **`fullscreenEnabled`** در رابط {{domxref("Document")}} نشان می‌دهد که آیا حالت تمام‌صفحه در دسترس است یا نه.

حالت تمام‌صفحه فقط برای صفحه‌ای در دسترس است که هیچ پلاگین پنجره‌ای در هیچ‌یک از اسناد آن وجود نداشته باشد و تمام عناصر {{HTMLElement("iframe")}} که سند را در خود دارند، ویژگی [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen) را تنظیم کرده باشند.

اگرچه این خصوصیت فقط‌خواندنی است، اما اگر تغییر داده شود (حتی در حالت سخت‌گیرانه) خطایی پرتاب نمی‌کند؛ تنظیم‌کننده آن یک عملیات بی‌اثر است و نادیده گرفته می‌شود.

## مقدار

یک مقدار بولی که اگر سند و عناصر داخل آن بتوانند با فراخوانی {{domxref("Element.requestFullscreen()")}} در حالت تمام‌صفحه قرار گیرند، `true` است. اگر حالت تمام‌صفحه در دسترس نباشد، این مقدار `false` است.

## مثال‌ها

در این مثال، قبل از تلاش برای درخواست حالت تمام‌صفحه برای یک عنصر {{htmlElement("video")}}، مقدار `fullscreenEnabled` بررسی می‌شود تا در صورت در دسترس نبودن، از انجام این تلاش جلوگیری شود.

```js
function requestFullscreen() {
  if (document.fullscreenEnabled) {
    videoElement.requestFullscreen();
  } else {
    console.log("Your browser cannot use fullscreen right now");
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- [Guide to the Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide)
- {{domxref("Element.requestFullscreen()")}}
- {{domxref("Document.exitFullscreen()")}}
- {{domxref("Document.fullscreenElement")}}
- {{cssxref(":fullscreen") }} و {{cssxref("::backdrop")}}
- ویژگی [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen) در عنصر {{HTMLElement("iframe")}}