---
title: "HTMLAnchorElement: target property"
short-title: target
slug: Web/API/HTMLAnchorElement/target
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.target
---

{{ApiRef("HTML DOM")}}

ویژگی **`target`** در رابط {{domxref("HTMLAnchorElement")}} یک رشته (string) است که مشخص می‌کند منبعِ پیوند‌شده در کجا نمایش داده شود.

این ویژگی منعکس‌کنندهٔ attribute [`target`](/en-US/docs/Web/HTML/Reference/Elements/a#target) عنصر {{HTMLElement("a")}} است.

## مقدار

یک رشته که نمایانگر هدف است. مقدار آن می‌تواند:

- نام یک {{HTMLElement("frame")}} باشد.
- یکی از [کلیدواژه‌های با مقادیر خاص](/en-US/docs/Web/HTML/Reference/Elements/a#target) باشد: `_blank`، `_self`، `_parent` یا `_top`.

## مثال

```html
<a href="www.example1.com" class="link1" target="_blank">example1</a>
```

```js
const link = document.querySelector(".link1");
console.log(link.target); // output: "_blank"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLBaseElement.target")}}
- ویژگی {{domxref("HTMLFormElement.target")}}
- ویژگی {{domxref("HTMLAreaElement.target")}}