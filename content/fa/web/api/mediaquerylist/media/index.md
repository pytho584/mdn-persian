---
title: "MediaQueryList: media property"
---

---
title: "MediaQueryList: media property"
short-title: media
slug: Web/API/MediaQueryList/media
page-type: web-api-instance-property
browser-compat: api.MediaQueryList.media
---

{{APIRef("CSSOM view API")}}

ویژگی فقط‌خواندنی **`media`** در رابط {{DOMxRef("MediaQueryList")}} یک رشته (string) است که یک پرس‌وجوی رسانه‌ای (media query) سریال‌سازی‌شده را نمایش می‌دهد.

## مقدار

رشته‌ای که یک پرس‌وجوی رسانه‌ای سریال‌سازی‌شده را نمایش می‌دهد.

## نمونه‌ها

این مثال، پرس‌وجوی رسانه‌ای `(width <= 600px)` را اجرا می‌کند و مقدار ویژگی `media` در `MediaQueryList` حاصل را داخل یک {{HTMLElement("span")}} نمایش می‌دهد.

### JavaScript

```js
let mql = window.matchMedia("(width <= 600px)");

document.querySelector(".mq-value").innerText = mql.media;
```

کد جاوااسکریپت، پرس‌وجوی رسانه‌ای موردنظر را به {{DOMxRef("Window.matchMedia", "matchMedia()")}} می‌دهد تا آن را کامپایل کند و سپس {{DOMxRef("HTMLElement.innerText", "innerText")}} عنصر `<span>` را برابر با مقدار ویژگی `media` در نتیجه، قرار می‌دهد.

### HTML

```html
<span class="mq-value"></span>
```

یک `<span>` برای دریافت خروجی.

```css hidden
.mq-value {
  font:
    18px "Arial",
    sans-serif;
  font-weight: bold;
  color: #8888ff;
  padding: 0.4em;
  border: 1px solid #ddddee;
}
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", "60")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [پرس‌وجوهای رسانه‌ای (Media queries)](/en-US/docs/Web/CSS/Guides/Media_queries/Using)
- [استفاده از پرس‌وجوهای رسانه‌ای در کد](/en-US/docs/Web/CSS/Guides/Media_queries/Testing)
- {{DOMxRef("window.matchMedia()")}}
- {{DOMxRef("MediaQueryList")}}
- {{DOMxRef("MediaQueryListEvent")}}