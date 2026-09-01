---
title: "DOMTokenList: toggle() method"
short-title: toggle()
slug: Web/API/DOMTokenList/toggle
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.toggle
---

{{APIRef("DOM")}}

متد **`toggle()`** از رابط {{domxref("DOMTokenList")}} یک نشانهٔ موجود را از فهرست حذف می‌کند و `false` برمی‌گرداند. اگر نشانه وجود نداشته باشد، اضافه می‌شود و تابع `true` برمی‌گرداند.

## نحو

```js-nolint
toggle(token)
toggle(token, force)
```

### پارامترها

- `token`
  - : رشته‌ای است که نشانه‌ای را که می‌خواهید تغییر وضعیت دهید، مشخص می‌کند.
- `force` {{optional_inline}}
  - : در صورت ذکر شدن، عملیات تغییر وضعیت را به یک عملیات یک‌طرفه تبدیل می‌کند. اگر `false` باشد، `token` _فقط_ حذف می‌شود و اضافه نخواهد شد. اگر `true` باشد، `token` _فقط_ اضافه می‌شود و حذف نخواهد شد.

### مقدار بازگشتی

یک مقدار بولین، `true` یا `false`، که نشان می‌دهد پس از فراخوانی، `token` در فهرست وجود دارد یا نه.

## مثال‌ها

### تغییر وضعیت یک کلاس با کلیک

در مثال زیر، فهرست کلاس‌های تنظیم‌شده روی یک عنصر {{htmlelement("span")}} را با استفاده از {{domxref("Element.classList")}} به‌عنوان یک `DOMTokenList` دریافت می‌کنیم. سپس وضعیت یک نشانه را در فهرست تغییر می‌دهیم و فهرست را درون {{domxref("Node.textContent")}} آن `<span>` می‌نویسیم.

ابتدا، HTML:

```html
<span class="a b">classList is 'a b'</span>
```

حالا جاوااسکریپت:

```js
const span = document.querySelector("span");
const classes = span.classList;

span.addEventListener("click", () => {
  const result = classes.toggle("c");
  span.textContent = `'c' ${
    result ? "added" : "removed"
  }; classList is now "${classes}".`;
});
```

خروجی به این شکل است و هر بار که روی متن کلیک کنید تغییر می‌کند:

{{ EmbedLiveSample('Toggling_a_class_on_click', '100%', 60) }}

### تنظیم پارامتر force

پارامتر دوم را می‌توان برای تعیین اینکه آیا کلاس لحاظ شود یا نه به کار برد. این مثال تنها در صورتی کلاس 'c' را اضافه می‌کند که عرض پنجرهٔ مرورگر بیشتر از ۱۰۰۰ پیکسل باشد:

```js
span.classList.toggle("c", window.innerWidth > 1000);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}