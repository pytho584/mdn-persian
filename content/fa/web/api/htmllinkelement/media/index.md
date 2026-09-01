---
title: "HTMLLinkElement: media property"
short-title: media
slug: Web/API/HTMLLinkElement/media
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.media
---

{{APIRef("HTML DOM")}}

ویژگی **`media`** در رابط {{domxref("HTMLLinkElement")}} یک رشته است که فهرستی از یک یا چند قالب رسانه‌ای را که منبع برای آن‌ها کاربرد دارد، نشان می‌دهد.

این ویژگی منعکس‌کنندهٔ ویژگی `media` عنصر {{HTMLElement("link")}} است.

## مقدار

یک رشته.

## مثال‌ها

```html
<link
  id="el"
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
  rel="stylesheet"
  media="screen and (width >= 600px)"
  crossorigin="anonymous" />
```

```js
const el = document.getElementById("el");
console.log(el.media); // خروجی: "screen and (width >= 600px)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```