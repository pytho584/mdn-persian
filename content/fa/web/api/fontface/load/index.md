---
title: "FontFace: load() method"
short-title: load()
slug: Web/API/FontFace/load
page-type: web-api-instance-method
browser-compat: api.FontFace.load
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

متد **`load()`** از رابط {{domxref("FontFace")}} درخواست بارگذاری قلمی را می‌دهد که `source` آن به‌صورت URL مشخص شده است. این متد یک {{jsxref('Promise')}} برمی‌گرداند که با شیء فعلی `FontFace` حل می‌شود.

اگر `source` قلم به‌صورت داده دودویی مشخص شده باشد، یا ویژگی {{domxref("FontFace/status", "status")}} قلم چیزی غیر از `unloaded` باشد، این متد هیچ کاری انجام نمی‌دهد.

## نحو (Syntax)

```js-nolint
load()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که وقتی قلم بارگذاری می‌شود با ارجاعی به شیء فعلی `FontFace` حل می‌شود، یا اگر فرآیند بارگذاری شکست بخورد، با یک {{domxref("DOMException")}} از نوع `NetworkError` رد می‌شود.

### استثناها

- `NetworkError` {{domxref("DOMException")}}
  - : نشان می‌دهد که تلاش برای بارگذاری قلم ناموفق بوده است.

## مثال‌ها

این مثال ساده یک قلم را بارگذاری می‌کند و از آن برای نمایش متنی در یک عنصر canvas (با شناسه `js-canvas`) استفاده می‌کند.

```html hidden
<canvas id="js-canvas"></canvas>
```

```js
const canvas = document.getElementById("js-canvas");

// load the "Bitter" font from Google Fonts
const fontFile = new FontFace(
  "FontFamily Style Bitter",
  'url("https://fonts.gstatic.com/s/bitter/v7/HEpP8tJXlWaYHimsnXgfCOvvDin1pK8aKteLpeZ5c0A.woff2")',
);
document.fonts.add(fontFile);

fontFile.load().then(
  () => {
    // font loaded successfully!
    canvas.width = 650;
    canvas.height = 100;
    const ctx = canvas.getContext("2d");

    ctx.font = '36px "FontFamily Style Bitter"';
    ctx.fillText("Bitter font loaded", 20, 50);
  },
  (err) => {
    console.error(err);
  },
);
```

{{EmbedLiveSample('Examples')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}