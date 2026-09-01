---
title: "HTMLImageElement: Image() constructor"
short-title: Image()
slug: Web/API/HTMLImageElement/Image
page-type: web-api-constructor
browser-compat: api.HTMLImageElement.Image
---

{{APIRef("HTML DOM")}}

سازندهٔ **`Image()`** یک نمونهٔ جدید از {{DOMxRef("HTMLImageElement")}} ایجاد می‌کند. این سازنده از نظر عملکردی معادل {{DOMxRef("Document.createElement()", "document.createElement('img')")}} است.

> [!NOTE]
> این تابع را نباید با تابع [`image()`](/en-US/docs/Web/CSS/Reference/Values/image/image) در CSS اشتباه گرفت.

## نحو (Syntax)

```js-nolint
new Image()
new Image(width)
new Image(width, height)
```

### پارامترها

- `width` {{optional_inline}}
  - : عرض تصویر (یعنی مقدار مربوط به ویژگی [`width`](/en-US/docs/Web/HTML/Reference/Elements/img#width)).
- `height` {{optional_inline}}
  - : ارتفاع تصویر (یعنی مقدار مربوط به ویژگی [`height`](/en-US/docs/Web/HTML/Reference/Elements/img#height)).

## نکتهٔ استفاده

کل بیت‌نگار (bitmap) بدون توجه به اندازه‌های مشخص‌شده در سازنده بارگذاری می‌شود. اندازه‌ای که در سازنده مشخص شده است از طریق ویژگی‌های {{DOMxRef("HTMLImageElement.width")}} و {{DOMxRef("HTMLImageElement.height")}} در نمونهٔ حاصل بازتاب می‌یابد. عرض و ارتفاع ذاتی تصویر بر حسب پیکسل CSS نیز از طریق ویژگی‌های {{DOMxRef("HTMLImageElement.naturalWidth")}} و {{DOMxRef("HTMLImageElement.naturalHeight")}} بازتاب می‌شوند. اگر در سازنده اندازه‌ای مشخص نشود، هر دو جفت ویژگی مقادیر یکسانی خواهند داشت.

## مثال‌ها

```js
const myImage = new Image(100, 200);
myImage.src = "picture.jpg";
document.body.appendChild(myImage);
```

این کد معادل تعریف تگ HTML زیر در داخل {{HTMLElement("body")}} است:

```html
<img width="100" height="200" src="picture.jpg" />
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}