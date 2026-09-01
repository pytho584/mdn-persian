---
title: "HTMLBaseElement: target property"
short-title: target
slug: Web/API/HTMLBaseElement/target
page-type: web-api-instance-property
browser-compat: api.HTMLBaseElement.target
---

{{ApiRef("HTML DOM")}}

ویژگی `target` در رابط {{domxref("HTMLBaseElement")}} یک رشته است که نمایانگر تب هدف پیش‌فرض برای نمایش خروجی حاصل از پیوندها و عناصر فرم می‌باشد.

این ویژگی منعکس‌کنندهٔ صفت [`target`](/en-US/docs/Web/HTML/Reference/Elements/base#target) عنصر {{HTMLElement("base")}} است.

## مقدار

یک رشته که نمایانگر هدف است. مقدار آن می‌تواند:

- نام یک {{HTMLElement("frame")}}.
- یکی از [کلمات کلیدی با مقادیر مشخص](/en-US/docs/Web/HTML/Reference/Elements/base#target): `_blank`، `_self`، `_parent`، یا `_top`.

## مثال

```html
<head>
  <base target="_top" />
</head>
```

```js
const baseElement = document.getElementsByTagName("base")[0];
console.log(baseElement.target); // Output: '_top'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAnchorElement.target")}} property
- {{domxref("HTMLAreaElement.target")}} property
- {{domxref("HTMLFormElement.target")}} property