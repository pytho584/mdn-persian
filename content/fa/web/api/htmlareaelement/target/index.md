---
title: "HTMLAreaElement: target property"
short-title: target
slug: Web/API/HTMLAreaElement/target
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.target
---

{{ApiRef("HTML DOM")}}

خاصیت **`target`** در رابط {{domxref("HTMLAreaElement")}} یک رشته است که مشخص می‌کند منبعِ لینک‌شده کجا نمایش داده شود.

این خاصیت منعکس‌کنندهٔ ویژگی [`target`](/en-US/docs/Web/HTML/Reference/Elements/area#target) عنصر {{HTMLElement("area")}} است.

## مقدار

یک رشته که نمایانگر مقصد است. مقدار آن می‌تواند یکی از این‌ها باشد:

- نام یک {{HTMLElement("frame")}}.
- یکی از [کلیدواژه‌های با مقادیر خاص](/en-US/docs/Web/HTML/Reference/Elements/area#target): `_blank`، `_self`، `_parent`، یا `_top`.

## مثال

```html
<map name="image-map">
  <area href="www.example.com" target="_top" alt="left" />
</map>
```

```js
const areaElement = document.getElementsByName("image-map")[0].areas[0];
console.log(areaElement.target); // Output: "_top"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- خاصیت {{domxref("HTMLBaseElement.target")}}
- خاصیت {{domxref("HTMLFormElement.target")}}
- خاصیت {{domxref("HTMLAnchorElement.target")}}