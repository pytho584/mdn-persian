```yaml
---
title: "CSS: registerProperty() static method"
short-title: registerProperty()
slug: Web/API/CSS/registerProperty_static
page-type: web-api-static-method
browser-compat: api.CSS.registerProperty_static
---

{{APIRef("CSSOM")}}

متد استاتیک **`CSS.registerProperty()`**،
[ویژگی‌های سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) را ثبت می‌کند و امکان بررسی نوع ویژگی، مقدار پیش‌فرض، و ویژگی‌هایی که مقدار خود را به ارث می‌برند یا نمی‌برند را فراهم می‌سازد.

ثبت یک ویژگی سفارشی به مرورگر می‌گوید که آن ویژگی چگونه باید رفتار کند: چه نوع‌هایی مجاز هستند، آیا ویژگی سفارشی مقدار خود را به ارث می‌برد، و مقدار پیش‌فرض آن چیست.

## نحو (Syntax)

```js-nolint
CSS.registerProperty(propertyDefinition)
```

### پارامترها

- `propertyDefinition`
  - : یک شیء شامل ویژگی‌های زیر:
    - `name`
      - : یک رشته (string) که نام {{cssxref("dashed-ident")}} ویژگی تعریف‌شده را نشان می‌دهد.
    - `syntax` {{optional_inline}}
      - : یک رشته که نحو (syntax) مورد انتظار برای ویژگی تعریف‌شده را مشخص می‌کند. مقدار پیش‌فرض `"*"` است. به {{cssxref("@property/syntax", "syntax")}} مراجعه کنید.
    - `inherits`
      - : یک مقدار بولی (boolean) که تعیین می‌کند آیا ویژگی تعریف‌شده باید به ارث برده شود (`true`) یا خیر (`false`). مقدار پیش‌فرض `false` است.
    - `initialValue` {{optional_inline}}
      - : یک رشته که مقدار اولیه ویژگی تعریف‌شده را مشخص می‌کند.

### مقدار بازگشتی

`undefined`.

### استثناها (Exceptions)

- `InvalidModificationError` {{domxref("DOMException")}}
  - : `name` داده‌شده قبلاً ثبت شده است.
- `SyntaxError` {{domxref("DOMException")}}
  - : `name` داده‌شده یک نام ویژگی سفارشی معتبر نیست (با دو خط تیره شروع نمی‌شود، مثلاً `--foo`).
- {{jsxref("TypeError")}}
  - : اعضای ضروری `name` و/یا `inherits` ارائه نشده‌اند.

## مثال‌ها

در مثال زیر، یک [ویژگی سفارشی](/en-US/docs/Web/CSS/Reference/Properties/--*) به نام `--my-color` با استفاده از `registerProperty()` به عنوان یک رنگ (color) ثبت می‌شود، یک مقدار پیش‌فرض به آن داده می‌شود، و خاصیت ارث‌بری آن روی false تنظیم می‌شود:

```js
window.CSS.registerProperty({
  name: "--my-color",
  syntax: "<color>",
  inherits: false,
  initialValue: "#c0ffee",
});
```

در این مثال، ویژگی سفارشی `--my-color` با نحو `<color>` ثبت شده است. اکنون می‌توانیم از این ویژگی برای انتقال (transition) یک گرادیان در هنگام hover یا focus استفاده کنیم. توجه کنید که با ویژگی ثبت‌شده، انتقال کار می‌کند، اما با ویژگی ثبت‌نشده کار نمی‌کند!

```css
.registered {
  --my-color: #c0ffee;
  background-image: linear-gradient(to right, white, var(--my-color));
  transition: --my-color 1s ease-in-out;
}

.registered:hover,
.registered:focus {
  --my-color: #b4d455;
}

.unregistered {
  --unregistered: #c0ffee;
  background-image: linear-gradient(to right, white, var(--unregistered));
  transition: --unregistered 1s ease-in-out;
}

.unregistered:hover,
.unregistered:focus {
  --unregistered: #b4d455;
}
button {
  font-size: 3vw;
}
```

می‌توانیم این استایل‌ها را به چند دکمه اضافه کنیم:

```html
<button class="registered">Background Registered</button>
<button class="unregistered">Background Not Registered</button>
```

{{EmbedLiveSample("Examples", 320, 320)}}

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [استفاده از API ویژگی‌ها و مقادیر CSS](/en-US/docs/Web/API/CSS_Properties_and_Values_API/guide)
- {{DOMxRef("CSS")}}
- {{DOMxRef("CSS/supports_static", "CSS.supports()")}}
- {{DOMxRef("CSS/escape_static", "CSS.escape()")}}
- [توابع کارخانه‌ای CSS](/en-US/docs/Web/API/CSS/factory_functions_static)
- CSS {{cssxref("@property")}}
```