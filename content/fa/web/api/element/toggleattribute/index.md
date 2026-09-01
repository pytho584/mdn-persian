---
title: "Element: toggleAttribute() method"
---

---
title: "Element: toggleAttribute() method"
short-title: toggleAttribute()
slug: Web/API/Element/toggleAttribute
page-type: web-api-instance-method
browser-compat: api.Element.toggleAttribute
---

{{APIRef("DOM")}}

متد **`toggleAttribute()`** از رابط {{domxref("Element")}} یک ویژگی بولین (Boolean attribute) را روی عنصر مورد نظر تغییر وضعیت می‌دهد؛ به این صورت که اگر ویژگی وجود داشته باشد آن را حذف می‌کند و اگر وجود نداشته باشد آن را اضافه می‌کند.

## نحو

```js-nolint
toggleAttribute(name)
toggleAttribute(name, force)
```

### پارامترها

- `name`: یک رشته که نام ویژگی مورد نظر برای تغییر وضعیت را مشخص می‌کند. وقتی `toggleAttribute()` روی یک عنصر HTML در یک سند HTML فراخوانی شود، نام ویژگی به‌طور خودکار به حروف کوچک تبدیل می‌شود.
- `force` {{optional_inline}}: یک مقدار بولین که اثرات زیر را دارد:
  - اگر اصلاً مشخص نشود، متد `toggleAttribute` ویژگی‌ای با نام `name` را «تغییر وضعیت» می‌دهد — اگر وجود داشته باشد آن را حذف می‌کند، و اگر وجود نداشته باشد آن را اضافه می‌کند.
  - اگر `true` باشد، متد `toggleAttribute` ویژگی‌ای با نام `name` اضافه می‌کند.
  - اگر `false` باشد، متد `toggleAttribute` ویژگی‌ای با نام `name` حذف می‌کند.

### مقدار بازگشتی

اگر ویژگی **`name`** در نهایت وجود داشته باشد، `true` و در غیر این صورت `false` بازگردانده می‌شود.

### استثناها

- `InvalidCharacterError` {{domxref("DOMException")}}: ویژگی `name` مشخص‌شده شامل یک یا چند نویسه است که در نام‌های ویژگی معتبر نیستند. `name` باید حداقل یک نویسه داشته باشد و نباید شامل فضای سفید ASCII، `NULL`، `/`، `=` یا `>` باشد (به ترتیب U+0000، U+002F، U+003D یا U+003E).

## مثال‌ها

### کاربرد پایه

در مثال زیر، از `toggleAttribute()` برای تغییر وضعیت ویژگی `disabled` در یک عنصر {{HTMLElement("input")}} استفاده شده است.

### HTML

```html
<input value="text" /> <button>toggleAttribute("disabled")</button>
```

### JavaScript

```js
const button = document.querySelector("button");
const input = document.querySelector("input");

button.addEventListener("click", () => {
  input.toggleAttribute("disabled");
});
```

### نتیجه

{{ EmbedLiveSample('Examples', '300', '50') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.hasAttribute()")}}
- {{domxref("Element.getAttribute()")}}
- {{domxref("Element.removeAttribute()")}}
- {{domxref("Element.setAttribute()")}}