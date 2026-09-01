---
title: "HTMLInputElement: showPicker() method"
short-title: showPicker()
slug: Web/API/HTMLInputElement/showPicker
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.showPicker
---

{{ APIRef("HTML DOM") }}

متد **`HTMLInputElement.showPicker()`** انتخابگر (picker) مرورگر را برای یک عنصر `input` نمایش می‌دهد.

این همان انتخابگری است که معمولاً هنگام انتخاب عنصر نمایش داده می‌شود، اما می‌تواند از طریق فشار دادن دکمه یا تعامل کاربری دیگر نیز فعال شود.

مرورگرها معمولاً این متد را برای ورودی‌های از انواع زیر پیاده‌سازی می‌کنند: `"date"`، `"month"`، `"week"`، `"time"`، `"datetime-local"`، `"color"` یا `"file"`.
همچنین می‌توان آن را با مواردی از یک عنصر {{htmlelement("datalist")}} یا ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) از پیش پر کرد.

به‌طور کلی، این متد در حالت ایده‌آل باید انتخابگر را برای هر عنصر ورودی در پلتفرم که دارای انتخابگر است نمایش دهد.

## نحو (Syntax)

```js-nolint
showPicker()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر عنصر قابل تغییر نباشد پرتاب می‌شود، به این معنی که کاربر نمی‌تواند آن را تغییر دهد و/یا نمی‌تواند به‌طور خودکار از پیش پر شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر به‌صراحت توسط یک اقدام کاربر مانند ژست لمسی یا کلیک ماوس فعال نشده باشد پرتاب می‌شود (انتخابگر به {{Glossary("Transient activation")}} نیاز دارد).
- `SecurityError` {{domxref("DOMException")}}
  - : اگر در یک iframe با مبدأ متفاوت (cross-origin) فراخوانی شود پرتاب می‌شود، به‌جز انتخابگرهای فایل و رنگ (که به دلایل تاریخی معاف هستند).

## امنیت

[فعال‌سازی گذرای کاربر](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این ویژگی کار کند.

## مثال‌ها

### تشخیص ویژگی (Feature Detection)

کد زیر نحوه بررسی پشتیبانی از `showPicker()` را نشان می‌دهد:

```js
if ("showPicker" in HTMLInputElement.prototype) {
  // showPicker() پشتیبانی می‌شود.
}
```

### انتخابگرهای ورودی معمولی

این مثال نحوه استفاده از این ویژگی را برای انتخابگرهای ورودی `color` و `file` نشان می‌دهد.

> [!NOTE]
> انتخابگرهای `date`، `datetime-local`، `month`، `time`، `week` به همین روش راه‌اندازی می‌شوند.
> آن‌ها در اینجا قابل نمایش نیستند زیرا مثال‌های زنده در یک فریم با مبدأ متفاوت اجرا می‌شوند و باعث [`SecurityError`](#securityerror) می‌شوند.

#### HTML

```html
<p>
  <input type="color" />
  <button id="color">Show the color picker</button>
</p>

<p>
  <input type="file" />
  <button id="file">Show the file picker</button>
</p>
```

#### جاوااسکریپت

کد به سادگی عنصر قبلی دکمه انتخاب‌شده را دریافت می‌کند و `showPicker()` را روی آن فراخوانی می‌کند.

```js
document.querySelectorAll("button").forEach((button) => {
  button.addEventListener("click", (event) => {
    const input = event.srcElement.previousElementSibling;
    try {
      input.showPicker();
    } catch (error) {
      console.log(error);
    }
  });
});
```

#### نتیجه

برای نمایش انتخابگر، روی دکمه کنار هر نوع ورودی کلیک کنید.

{{EmbedLiveSample("Normal input pickers", "100%", "140px")}}

### showPicker() برای ورودی datalist

`showPicker()` می‌تواند انتخابگر فهرستی از گزینه‌های تعریف‌شده در یک [`<datalist>`](/en-US/docs/Web/HTML/Reference/Elements/datalist) را راه‌اندازی کند.

ابتدا یک `<datalist>` در HTML شامل تعدادی مرورگر اینترنتی، یک ورودی از نوع `text` که از آن استفاده می‌کند، و یک دکمه تعریف می‌کنیم.

```html
<datalist id="browsers">
  <option value="Chrome"></option>
  <option value="Firefox"></option>
  <option value="Opera"></option>
  <option value="Safari"></option>
  <option value="Microsoft Edge"></option>
</datalist>

<input type="text" list="browsers" />
<button>Select browser</button>
```

کد زیر یک شنونده رویداد اضافه می‌کند که هنگام کلیک روی دکمه، `showPicker()` را فراخوانی می‌کند.

```js
const button = document.querySelector("button");
const browserInput = document.querySelector("input");

button.addEventListener("click", () => {
  try {
    browserInput.showPicker();
  } catch (error) {
    // Fall back to another picker mechanism
  }
});
```

مانند سایر انتخابگرها، نمی‌توانیم این کد را به‌صورت مثال زنده اجرا شده نشان دهیم زیرا در یک فریم با مبدأ متفاوت اجرا می‌شود و باعث [`SecurityError`](#securityerror) می‌شود.

### showPicker() برای autocomplete

`showPicker()` می‌تواند انتخابگر را برای یک ورودی با ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) راه‌اندازی کند.

در اینجا ورودی‌ای تعریف می‌کنیم که گزینه autocomplete از نوع "name" را می‌گیرد.

```html
<input autocomplete="name" /> <button>Show autocomplete options</button>
```

کد زیر هنگام کلیک روی دکمه، انتخابگر را برای ورودی نشان می‌دهد.

```js
const button = document.querySelector("button");
const browserInput = document.querySelector("input");

button.addEventListener("click", () => {
  try {
    browserInput.showPicker();
  } catch (error) {
    // Fall back to another picker mechanism
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ HTMLElement("input") }}
- {{ domxref("HTMLInputElement") }}
- {{ domxref("HTMLSelectElement.showPicker()") }}
- {{htmlelement("datalist")}}
- [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)