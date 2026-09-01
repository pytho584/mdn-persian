---
title: "DOMException: DOMException() constructor"
short-title: DOMException()
slug: Web/API/DOMException/DOMException
page-type: web-api-constructor
browser-compat: api.DOMException.DOMException
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

سازنده‌ی **`DOMException()`** یک شیء {{domxref("DOMException")}} با پیام و نام مشخص شده بازمی‌گرداند.

## نحو

```js-nolint
new DOMException()
new DOMException(message)
new DOMException(message, name)
```

### پارامترها

- `message` {{optional_inline}}
  - : توضیحی از استثنا. اگر وجود نداشته باشد، رشته‌ی خالی `''` استفاده می‌شود.
- `name` {{optional_inline}}
  - : یک رشته. اگر نام مشخص شده یک [نام خطای استاندارد](/en-US/docs/Web/API/DOMException#error_names) باشد، دریافت ویژگی [`code`](/en-US/docs/Web/API/DOMException/code) شیء `DOMException` کد عددی متناظر با آن نام را برمی‌گرداند. اگر وجود نداشته باشد، رشته‌ی `'Error'` استفاده می‌شود.

### مقدار بازگشتی

یک شیء {{domxref("DOMException")}} تازه ایجاد شده.

## مثال‌ها

در این مثال، فشار دادن دکمه باعث پرتاب یک `DOMException` سفارشی می‌شود که سپس گرفته شده و پیام خطای سفارشی در یک هشدار نمایش داده می‌شود.

### HTML

```html
<button>Trigger DOM Exception</button>

<p id="output"></p>
```

### JavaScript

```js
const button = document.querySelector("button");

button.onclick = () => {
  try {
    throw new DOMException("Custom DOM Exception Triggered.");
  } catch (error) {
    document.querySelector("#output").textContent = `Error: ${error.message}`;
  }
};
```

### نتیجه

{{ EmbedLiveSample('Examples', '100%', 100) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [یک polyfill از سازنده‌ی `DOMException`](https://github.com/zloirock/core-js#domexception) در [`core-js`](https://github.com/zloirock/core-js) موجود است.