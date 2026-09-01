---
title: "HTMLIFrameElement: allowFullscreen property"
short-title: allowFullscreen
slug: Web/API/HTMLIFrameElement/allowFullscreen
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.allowFullscreen
---

{{APIRef("HTML DOM")}}

خاصیت **`allowFullscreen`** در رابط {{domxref("HTMLIFrameElement")}} یک مقدار بولی است که ویژگی `allowfullscreen` عنصر {{HTMLElement("iframe")}} را منعکس می‌کند و مشخص می‌کند که آیا محتوای iframe مجاز است از {{domxref("Element.requestFullscreen", "requestFullscreen()")}} استفاده کند یا نه.

> [!NOTE]
> این خاصیت یک ویژگی قدیمی (legacy) محسوب می‌شود. به جای آن از `allow="fullscreen"` و {{domxref("HTMLIFrameElement.allow")}} استفاده کنید.

## مقدار

یک مقدار بولی.

## نمونه‌ها

```html
<iframe id="el" allowfullscreen></iframe>
```

```js
const el = document.getElementById("el");
console.log(el.allowFullscreen); // Output: true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- {{domxref("Element.requestFullscreen()")}}
- [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)
- دستورالعمل {{httpheader("Permissions-Policy/fullscreen", "fullscreen")}} در Permissions Policy