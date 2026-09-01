---
title: "HTMLImageElement: crossOrigin property"
---

---
title: "HTMLImageElement: crossOrigin property"
short-title: crossOrigin
slug: Web/API/HTMLImageElement/crossOrigin
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.crossOrigin
---

{{APIRef("HTML DOM")}}

ویژگی **`crossOrigin`** در رابط {{domxref("HTMLImageElement")}} یک رشته است که تنظیمات اشتراک‌گذاری منابع متقاطع ({{Glossary("CORS")}}) را برای زمانی که تصویر دریافت می‌شود تعیین می‌کند. این ویژگی، ویژگی محتوایی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Elements/img#crossorigin) عنصر `<img>` را بازتاب می‌دهد.

## مقدار

رشته‌ای که مقدار آن یکی از `anonymous` یا `use-credentials` است. برای آگاهی از معانی آن‌ها، به مرجع ویژگی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) در HTML مراجعه کنید.

## مثال‌ها

### تنظیم ویژگی crossorigin

در این مثال، یک عنصر جدید {{HTMLElement("img")}} ساخته و به سند اضافه می‌شود؛ تصویر با حالت Anonymous بارگذاری می‌شود. تصویر با استفاده از CORS بارگذاری خواهد شد و برای همه بارگذاری‌های متقاطع، از اعتبارنامه‌ها استفاده می‌شود.

#### JavaScript

کد زیر نحوه تنظیم ویژگی `crossOrigin` روی یک عنصر `<img>` را برای پیکربندی دسترسی CORS هنگام واکشی یک تصویر تازه‌ساخته‌شده نشان می‌دهد.

```js
const container = document.querySelector(".container");

function loadImage(url) {
  const image = new Image(200, 200);
  image.addEventListener("load", () => container.prepend(image));

  image.addEventListener("error", () => {
    const errMsg = document.createElement("output");
    errMsg.value = `Error loading image at ${url}`;
    container.append(errMsg);
  });

  image.crossOrigin = "anonymous";
  image.alt = "";
  image.src = url;
}

loadImage("/shared-assets/images/examples/balloon.jpg");
```

#### HTML

```html
<div class="container">
  <p>
    Here's a paragraph. It's a very interesting paragraph. You are captivated by
    this paragraph. Keep reading this paragraph. Okay, now you can stop reading
    this paragraph. Thanks for reading me.
  </p>
</div>
```

#### CSS

```css
body {
  font:
    1.125rem/1.5 "Helvetica",
    "Arial",
    sans-serif;
}

.container {
  display: flow-root;
  width: 37.5em;
  border: 1px solid #d2d2d2;
}

img {
  float: left;
  padding-right: 1.5em;
}

output {
  background: rgb(100 100 100 / 100%);
  font-family: "Courier New", monospace;
  width: 95%;
}
```

#### نتیجه

{{EmbedLiveSample("Setting the crossorigin attribute", 600, 260)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLLinkElement.crossOrigin")}}
- {{domxref("HTMLMediaElement.crossOrigin")}}
- {{domxref("HTMLScriptElement.crossOrigin")}}