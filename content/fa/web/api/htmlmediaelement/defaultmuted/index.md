```markdown
---
title: "HTMLMediaElement: defaultMuted property"
short-title: defaultMuted
slug: Web/API/HTMLMediaElement/defaultMuted
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.defaultMuted
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.defaultMuted`** منعکس‌کنندهٔ [`ویژگی HTML`](/en-US/docs/Web/HTML/Reference/Elements/video#muted) `muted` است که مشخص می‌کند آیا خروجی صدای عنصر رسانه باید به‌طور پیش‌فرض بی‌صدا باشد. این ویژگی هیچ اثر پویایی ندارد. برای بی‌صدا کردن و بازگرداندن صدا، از ویژگی {{domxref("HTMLMediaElement.muted", "muted")}} استفاده کنید.

## مقدار

یک مقدار بولی. مقدار `true` به این معنی است که خروجی صدا به‌طور پیش‌فرض بی‌صدا خواهد بود.

## مثال‌ها

```js
const videoEle = document.createElement("video");
videoEle.defaultMuted = true;
console.log(videoEle.outerHTML); // <video muted=""></video>
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف ویژگی `HTMLMediaElement.defaultMuted` استفاده شده است
- {{domxref("HTMLMediaElement.muted")}}
- {{domxref("HTMLMediaElement.volume")}}
```