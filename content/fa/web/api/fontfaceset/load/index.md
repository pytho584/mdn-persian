---
title: "FontFaceSet: load() method"
short-title: load()
slug: Web/API/FontFaceSet/load
page-type: web-api-instance-method
browser-compat: api.FontFaceSet.load
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

`load()` روش در {{domxref("FontFaceSet")}} همهٔ فونت‌های داده‌شده در پارامترها را مجبور به بارگذاری می‌کند.

## نحو (Syntax)

```js-nolint
load(font)
load(font, text)
```

### پارامترها

- `font`
  - : یک مشخصات فونت با استفاده از نحو مقدار CSS، به عنوان مثال `"italic bold 16px Roboto"`
- `text` {{optional_inline}}
  - : فونت‌ها را به آن‌هایی محدود می‌کند که محدودهٔ یونیکد آن‌ها حداقل یکی از نویسه‌های موجود در text را شامل شود. این [پوشش گلیف‌های فردی را بررسی نمی‌کند](https://lists.w3.org/Archives/Public/www-style/2015Aug/0330.html). پیش‌فرض آن رشته‌ای شامل یک نویسهٔ فاصله (`" "`) است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{jsxref("Array")}} از اشیاء {{domxref("FontFace")}} بارگذاری‌شده پر می‌شود. این promise زمانی که همهٔ فونت‌ها بارگذاری شوند پر می‌شود؛ اگر یکی از فونت‌ها در بارگذاری ناموفق باشد، رد می‌شود.

## مثال‌ها

مثال زیر یک promise برمی‌گرداند که بسته به موفقیت بارگذاری «MyFont» پر یا رد می‌شود. کد در `then()` می‌تواند فرض کند که آن فونت در دسترس است.

```js
document.fonts.load("12px MyFont", "ß").then(/* ... */);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}