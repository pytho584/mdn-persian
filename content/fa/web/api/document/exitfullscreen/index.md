---
title: "Document: exitFullscreen() method"
short-title: exitFullscreen()
slug: Web/API/Document/exitFullscreen
page-type: web-api-instance-method
browser-compat: api.Document.exitFullscreen
---

{{ApiRef("Fullscreen API")}}

متد **`exitFullscreen()`** از {{domxref("Document")}} درخواست می‌دهد که عنصری از این سند که در حال حاضر در حالت تمام‌صفحه نمایش داده می‌شود، از حالت تمام‌صفحه خارج شود و وضعیت قبلی صفحه بازگردانی شود. این کار معمولاً اثرات فراخوانی قبلی {{domxref("Element.requestFullscreen()")}} را معکوس می‌کند.

## نحو (Syntax)

```js-nolint
exitFullscreen()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که زمانی که {{Glossary("user agent")}} خروج از حالت تمام‌صفحه را به پایان برساند، resolve می‌شود. اگر هنگام تلاش برای خروج از حالت تمام‌صفحه خطایی رخ دهد، کنترل‌کننده `catch()` برای آن promise فراخوانی می‌شود.

## مثال‌ها

این مثال باعث می‌شود سند فعلی با هر کلیک ماوس در داخل آن، بین حالت تمام‌صفحه و حالت عادی جابه‌جا شود.

```js
document.onclick = (event) => {
  if (document.fullscreenElement) {
    document
      .exitFullscreen()
      .then(() => console.log("Document Exited from Full screen mode"))
      .catch((err) => console.error(err));
  } else {
    document.documentElement.requestFullscreen();
  }
};
```

> [!NOTE]
> برای یک مثال کامل‌تر، به
> [مثال‌های `Element.requestFullscreen()`](/en-US/docs/Web/API/Element/requestFullscreen#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- [راهنمای Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide)
- {{ domxref("Element.requestFullscreen()") }}
- {{ domxref("Document.fullscreenElement") }}
- {{ cssxref(":fullscreen") }} و {{cssxref("::backdrop")}}
- ویژگی [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen) در عنصر {{HTMLElement("iframe")}}