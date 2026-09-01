---
title: "HTMLSelectElement: showPicker() method"
short-title: showPicker()
slug: Web/API/HTMLSelectElement/showPicker
page-type: web-api-instance-method
browser-compat: api.HTMLSelectElement.showPicker
---

{{ APIRef("HTML DOM") }}

متد **`HTMLSelectElement.showPicker()`**، انتخاب‌گر (picker) مرورگر را برای یک عنصر `select` نمایش می‌دهد.

این همان انتخاب‌گری است که معمولاً هنگام انتخاب عنصر نمایش داده می‌شود، اما می‌تواند با فشار دادن دکمه یا تعامل کاربر دیگر فعال شود.

## Syntax

```js-nolint
showPicker()
```

### Parameters

هیچکدام.

### Return value

هیچکدام ({{jsxref("undefined")}}).

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر عنصر قابل تغییر نباشد، یعنی کاربر نتواند آن را تغییر دهد و/یا نتواند به صورت خودکار پیش‌پر شود، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر به طور صریح توسط یک اقدام کاربر مانند ژست لمسی یا کلیک ماوس فعال نشود (انتخاب‌گر نیاز به {{Glossary("Transient activation", "فعال‌سازی گذرا")}} دارد)، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر عنصر مرتبط با انتخاب‌گر رندر نشود، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر در یک iframe با منشأ متفاوت (cross-origin) فراخوانی شود، پرتاب می‌شود.

## ملاحظات امنیتی

فعال‌سازی کاربر گذرا (Transient user activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این ویژگی کار کند. این متد فقط در iframeهای هم‌منشأ (same-origin) مجاز به فراخوانی است؛ اگر در یک iframe با منشأ متفاوت فراخوانی شود، یک استثنا پرتاب می‌شود.

## مثال‌ها

### تشخیص ویژگی

کد زیر نحوه بررسی پشتیبانی از `showPicker()` را نشان می‌دهد:

```js
if ("showPicker" in HTMLSelectElement.prototype) {
  // showPicker() is supported.
}
```

### راه‌اندازی انتخاب‌گر

این مثال نشان می‌دهد که چگونه از یک دکمه برای راه‌اندازی انتخاب‌گر برای یک عنصر `<select>` با دو گزینه استفاده کنیم.

#### HTML

```html
<p>
  <select>
    <option value="1">One</option>
    <option value="2">Two</option>
  </select>
  <button type="button">Show Picker</button>
</p>
```

#### JavaScript

کد عنصر `<button>` را دریافت می‌کند و یک شنونده برای رویداد `click` آن اضافه می‌کند. کنترل‌کننده رویداد، عنصر `<select>` را دریافت می‌کند و `showPicker()` را روی آن فراخوانی می‌کند.

```js
const button = document.querySelector("button");
button.addEventListener("click", (event) => {
  const select = event.srcElement.previousElementSibling;
  try {
    select.showPicker();
  } catch (error) {
    window.alert(error);
  }
});
```

<!-- A live example cannot be shown here because they run in a cross-origin frame, and would cause a SecurityError -->

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{ HTMLElement("select") }}
- {{ domxref("HTMLSelectElement") }}
- {{ domxref("HTMLInputElement.showPicker()") }}