---
title: "HTMLStyleElement: media property"
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLStyleElement.media`** رسانهٔ مقصد مورد نظر برای اطلاعات سبک را مشخص می‌کند.

## مقدار

یک رشته که یک رسانهٔ واحد یا یک لیست جدا شده با کاما را توصیف می‌کند.

## مثال‌ها

فرض کنید در بخش `<head>` موارد زیر وجود دارد:

```html
<style id="inline-style" media="screen, print">
  p {
    color: blue;
  }
</style>
```

سپس:

```js
const style = document.getElementById("inline-style");

console.log(style.media); // 'screen, print'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}