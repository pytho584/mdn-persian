---
title: "HTMLMediaElement: preload property"
---

---
title: "HTMLMediaElement: preload property"
short-title: preload
slug: Web/API/HTMLMediaElement/preload
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.preload
---

{{APIRef("HTML DOM")}}

ویژگی **`preload`** از رابط {{domxref("HTMLMediaElement")}} رشته‌ای است که به مرورگر راهنمایی می‌دهد درباره آنچه نویسنده فکر می‌کند بهترین تجربه کاربری را به همراه خواهد داشت.

این ویژگی، صفت `preload` عنصر {{HTMLElement("audio")}} و عنصر {{HTMLElement("video")}} را بازتاب می‌دهد.

## مقدار

یک رشته. مقادیر ممکن به این شرح است:

- `none`
  - : نشان می‌دهد که رسانه نباید از پیش بارگیری شود.
- `metadata`
  - : نشان می‌دهد که تنها فرادادهٔ رسانه (مثلاً مدت‌زمان) دریافت می‌شود.
- `auto`
  - : نشان می‌دهد که کل فایل رسانه می‌تواند دانلود شود، حتی اگر انتظار نمی‌رود کاربر از آن استفاده کند.
- _رشتهٔ خالی_
  - : مترادفی برای مقدار `auto` است.

## مثال‌ها

```html
<video
  id="el"
  controls
  src="https://example.com/media.mp4"
  poster="https://example.com/media.jpg"
  width="800"
  height="600"
  preload="metadata">
  Sorry, your browser doesn't support embedded videos, but don't worry, you can
  <a href="https://example.com/media.mp4" download="media.mp4">download it</a>
  and watch it with your favorite video player!
</video>
```

```js
const el = document.getElementById("el");
console.log(el.preload); // Output: "metadata"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}