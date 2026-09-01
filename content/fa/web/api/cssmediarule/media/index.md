---
title: "CSSMediaRule: media property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CSSMediaRule/media"
---

---
title: "CSSMediaRule: media property"
short-title: media
slug: Web/API/CSSMediaRule/media
page-type: web-api-instance-property
browser-compat: api.CSSMediaRule.media
---

{{ APIRef("CSSOM") }}

ویژگی فقط‌خواندنی **`media`** از رابط {{domxref("CSSMediaRule")}} شامل یک شیء {{domxref("MediaList")}} است که فهرست رسانه‌ای (media query list) قانون {{cssxref("@media")}} را نمایش می‌دهد.

## مقدار

یک شیء {{domxref("MediaList")}}.

اگرچه خود ویژگی `media` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `MediaList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `media` مقدار اختصاص دهید که معادل اختصاص مقدار به ویژگی {{domxref("MediaList/mediaText", "mediaText")}} آن است. همچنین می‌توانید شیء `MediaList` را با استفاده از روش‌های {{domxref("MediaList/appendMedium", "appendMedium()")}} و {{domxref("MediaList/deleteMedium", "deleteMedium()")}} تغییر دهید.

## مثال‌ها

CSS شامل یک media query با یک قانون سبک است. این اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده می‌شود. بنابراین فراخوانی `myRules[0].media` یک شیء {{domxref("MediaList")}} برمی‌گرداند که media query را نمایش می‌دهد.

```css
@media (width >= 500px) {
  body {
    color: blue;
  }
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].media); // یک MediaList
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}