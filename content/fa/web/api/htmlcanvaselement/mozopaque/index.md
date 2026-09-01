---
title: "HTMLCanvasElement: mozOpaque property"
short-title: mozOpaque
slug: Web/API/HTMLCanvasElement/mozOpaque
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.HTMLCanvasElement.mozOpaque
---

{{APIRef("Canvas API")}}{{deprecated_header}}{{non-standard_header}}

ویژگی غیراستاندارد **`HTMLCanvasElement.mozOpaque`** یک مقدار بولین است که بازتاب‌دهندهٔ ویژگی HTML [`moz-opaque`](/en-US/docs/Web/HTML/Reference/Elements/canvas#moz-opaque) عنصر {{HTMLElement("canvas")}} می‌باشد. این ویژگی به canvas اطلاع می‌دهد که آیا نیمه‌شفافی نقشی دارد یا نه. اگر canvas بداند که نیمه‌شفافی وجود ندارد، می‌توان عملکرد ترسیم را بهینه کرد.

> [!NOTE]
> این ویژگی به‌صورت استاندارد با تنظیم گزینهٔ `alpha` روی `false` هنگام ایجاد context ترسیم با {{domxref("HTMLCanvasElement.getContext()")}} جایگزین شده است. استفاده از `mozOpaque` باید اجتناب شود. فایرفاکس در آینده پشتیبانی از آن را متوقف خواهد کرد.

## مقدار

یک مقدار بولین.

## مثال‌ها

با توجه به عنصر {{HTMLElement("canvas")}} زیر:

```html
<canvas id="canvas" width="300" height="300" moz-opaque></canvas>
```

می‌توانید ویژگی `mozOpaque` را بخوانید یا تنظیم کنید. برای مثال، می‌توانید به‌صورت شرطی آن را روی `true` تنظیم کنید اگر `mimeType === 'image/jpeg'` یا موارد مشابه باشد، تا زمانی که نیمه‌شفافی موردنیاز نیست، عملکرد برنامه‌تان بهبود یابد.

```js
const canvas = document.getElementById("canvas");
console.log(canvas.mozOpaque); // true
// deactivate it
canvas.mozOpaque = false;
```

## مشخصات

بخشی از هیچ استانداردی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement")}}: رابطی که ویژگی `HTMLCanvasElement.mozOpaque` را تعریف می‌کند
- [`moz-opaque`](/en-US/docs/Web/HTML/Reference/Elements/canvas#moz-opaque): ویژگی HTML عنصر {{HTMLElement("canvas")}}
- [بهینه‌سازی بازی جاوااسکریپتی شما برای Firefox OS](https://hacks.mozilla.org/2013/05/optimizing-your-javascript-game-for-firefox-os/)