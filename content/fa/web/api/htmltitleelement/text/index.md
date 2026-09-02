---
title: "HTMLTitleElement: text property"
---

---
title: "HTMLTitleElement: text property"
short-title: text
slug: Web/API/HTMLTitleElement/text
page-type: web-api-instance-property
browser-compat: api.HTMLTitleElement.text
---

{{APIRef("HTML DOM")}}

ویژگی **`text`** در رابط {{domxref("HTMLTitleElement")}}، محتوای متنیِ فرزندِ عنوانِ سند را به‌صورت یک رشته نشان می‌دهد. این ویژگی محتوای عنصر {{HTMLelement("title")}} را به‌صورت متن در بر می‌گیرد؛ اگر برچسب‌های HTML درون عنصر `<title>` قرار داشته باشند، به‌جای آنکه به‌صورت HTML تجزیه شوند، به‌عنوان بخشی از مقدارِ رشته لحاظ می‌شوند.

تنظیم یک مقدار برای ویژگی `text`، کل محتوای متنی عنصر `<title>` را جایگزین می‌کند.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر را در نظر بگیرید:

```html
<!doctype html>
<html lang="en-US">
  <head>
    <title>
      Hello world! <span class="highlight">Isn't this wonderful</span> really?
    </title>
  </head>
  <body></body>
</html>
```

```js
const title = document.querySelector("title");
console.log(title.text); // "Hello world! <span class="highlight">Isn't this wonderful</span> really?"
title.text = "Update the title";
```

همانطور که می‌بینید، برچسب `span` بدون تجزیه باقی ماند؛ محتویات عنصر `<title>` به‌عنوان متن ساده در نظر گرفته شدند و دقیقاً به همان شکلی که در عنصر `title` ظاهر شده‌اند، بازگردانده شدند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}