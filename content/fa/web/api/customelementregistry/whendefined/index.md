---
title: "CustomElementRegistry: whenDefined() method"
short-title: whenDefined()
slug: Web/API/CustomElementRegistry/whenDefined
page-type: web-api-instance-method
browser-compat: api.CustomElementRegistry.whenDefined
---

{{APIRef("Web Components")}}

متد **`whenDefined()`** از رابط {{domxref("CustomElementRegistry")}} یک {{jsxref("Promise")}} برمی‌گرداند که وقتی عنصر با نام مشخص شده تعریف شود، resolve می‌شود.

## نحو (Syntax)

```js-nolint
whenDefined(name)
```

### پارامترها

- `name`
  - : نام عنصر سفارشی.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با سازنده (constructor) [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) هنگامی که یک عنصر سفارشی با نام داده شده تعریف شود، fulfilled می‌شود.
اگر یک عنصر سفارشی قبلاً با این نام تعریف شده باشد، promise بلافاصله fulfilled می‌شود.

### استثناها (Exceptions)

- `SyntaxError` {{domxref("DOMException")}}
  - : [نام](#name) ارائه‌شده یک [نام عنصر سفارشی معتبر](/en-US/docs/Web/API/CustomElementRegistry/define#valid_custom_element_names) نیست.

## مثال‌ها

### استفاده پایه

این مثال از `whenDefined()` برای تشخیص زمان تعریف شدن عناصر سفارشی که یک منو را تشکیل می‌دهند استفاده می‌کند. منو تا زمانی که محتوای واقعی منو آماده نمایش نشده است، محتوای placeholder را نشان می‌دهد.

```html
<nav id="menu-container">
  <div class="menu-placeholder">در حال بارگذاری…</div>
  <nav-menu>
    <menu-item>آیتم ۱</menu-item>
    <menu-item>آیتم ۲</menu-item>
    …
    <menu-item>آیتم N</menu-item>
  </nav-menu>
</nav>
```

```js
const container = document.getElementById("menu-container");
const placeholder = container.querySelector(".menu-placeholder");
// همه فرزندان منو که هنوز تعریف نشده‌اند را دریافت کنید.
const undefinedElements = container.querySelectorAll(":not(:defined)");

async function removePlaceholder() {
  // عناصر را بر اساس localNameهای یکتا فیلتر کنید
  const tags = new Set(
    [...undefinedElements].map((button) => button.localName),
  );
  const promises = [...tags].map((tag) => customElements.whenDefined(tag));

  // منتظر بمانید تا همه فرزندان ارتقا یابند (upgraded)
  await Promise.all(promises);
  // سپس placeholder را حذف کنید
  container.removeChild(placeholder);
}

removePlaceholder();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}