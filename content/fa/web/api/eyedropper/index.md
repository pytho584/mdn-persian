---
title: EyeDropper
slug: Web/API/EyeDropper
page-type: web-api-interface
status:
  - experimental
browser-compat: api.EyeDropper
---

{{securecontext_header}}{{APIRef("EyeDropper API")}}{{SeeCompatTable}}

رابط **`EyeDropper`** نمونه‌ای از ابزار قطره‌چکان را نشان می‌دهد که می‌توان آن را باز کرد و کاربر می‌تواند از آن برای انتخاب رنگ از روی صفحه استفاده کند.

## سازنده

- {{DOMxRef("EyeDropper.EyeDropper", "EyeDropper()")}} {{Experimental_Inline}}
  - : یک نمونه جدید از `EyeDropper` را بازمی‌گرداند.

## متدهای نمونه

_رابط `EyeDropper` هیچ متدی را به ارث نمی‌برد._

- {{DOMxRef("EyeDropper.open()")}} {{Experimental_Inline}}
  - : یک Promise برمی‌گرداند که به شیئی که دسترسی به رنگ انتخاب‌شده را فراهم می‌کند، resolve می‌شود.

## مثال‌ها

### باز کردن ابزار قطره‌چکان و نمونه‌برداری از یک رنگ

این مثال نشان می‌دهد که چگونه یک ابزار قطره‌چکان را باز کنید و منتظر بمانید تا کاربر یا یک پیکسل از صفحه را انتخاب کند یا کلید <kbd>Escape</kbd> را بفشارد تا حالت قطره‌چکان لغو شود.

#### HTML

```html
<button id="start-button">Open the eyedropper</button> <span id="result"></span>
```

#### JavaScript

```js
document.getElementById("start-button").addEventListener("click", () => {
  const resultElement = document.getElementById("result");

  if (!window.EyeDropper) {
    resultElement.textContent =
      "Your browser does not support the EyeDropper API";
    return;
  }

  const eyeDropper = new EyeDropper();

  eyeDropper
    .open()
    .then((result) => {
      resultElement.textContent = result.sRGBHex;
      resultElement.style.backgroundColor = result.sRGBHex;
    })
    .catch((e) => {
      resultElement.textContent = e;
    });
});
```

#### نتیجه

{{EmbedLiveSample("Opening the eyedropper tool and sampling a color")}}

### لغو حالت قطره‌چکان

این مثال نشان می‌دهد که حالت قطره‌چکان را می‌توان پیش از انتخاب رنگ توسط کاربر یا فشار دادن <kbd>Escape</kbd> نیز لغو کرد.

#### HTML

```html
<button id="start-button">Open the eyedropper</button> <span id="result"></span>
```

#### JavaScript

```js
document.getElementById("start-button").addEventListener("click", () => {
  const resultElement = document.getElementById("result");

  if (!window.EyeDropper) {
    resultElement.textContent =
      "Your browser does not support the EyeDropper API";
    return;
  }

  const eyeDropper = new EyeDropper();
  const abortController = new AbortController();

  eyeDropper
    .open({ signal: abortController.signal })
    .then((result) => {
      resultElement.textContent = result.sRGBHex;
      resultElement.style.backgroundColor = result.sRGBHex;
    })
    .catch((e) => {
      resultElement.textContent = e;
    });

  setTimeout(() => {
    abortController.abort();
  }, 2000);
});
```

#### نتیجه

{{EmbedLiveSample("Aborting the eyedropper mode")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
