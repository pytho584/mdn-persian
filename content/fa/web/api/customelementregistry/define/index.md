---
title: "CustomElementRegistry: define() method"
short-title: define()
slug: Web/API/CustomElementRegistry/define
page-type: web-api-instance-method
browser-compat: api.CustomElementRegistry.define
---

{{APIRef("Web Components")}}

متد **`define()`** از رابط {{domxref("CustomElementRegistry")}} یک تعریف برای عنصر سفارشی به ثبت عنصر سفارشی اضافه می‌کند و نام آن را به سازنده‌ای که برای ایجاد آن استفاده خواهد شد نگاشت می‌کند.

## Syntax

```js-nolint
define(name, constructor)
define(name, constructor, options)
```

### Parameters

- `name`
  - : نامی برای عنصر سفارشی جدید. باید یک [نام معتبر عنصر سفارشی](#valid_custom_element_names) باشد.
- `constructor`
  - : سازنده‌ای برای عنصر سفارشی جدید.
- `options` {{optional_inline}}
  - : شیئی که نحوه تعریف عنصر را کنترل می‌کند. در حال حاضر یک گزینه پشتیبانی می‌شود:
    - `extends`
      - : رشته‌ای که نام یک عنصر داخلی (built-in) را برای گسترش مشخص می‌کند. برای ایجاد یک عنصر داخلی سفارشی‌سازی‌شده استفاده می‌شود.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر شرایط زیر رخ دهد پرتاب می‌شود:
    - {{domxref("CustomElementRegistry")}} از قبل دارای یک ورودی با همان نام یا همان سازنده باشد (یا به نحوی از قبل تعریف شده باشد).
    - گزینه `extends` مشخص شده باشد و آن یک [نام معتبر عنصر سفارشی](#valid_custom_element_names) باشد (یعنی بخواهید یک عنصر سفارشی را گسترش دهید).
    - گزینه `extends` مشخص شده باشد اما عنصری که سعی در گسترش آن دارید یک عنصر ناشناخته باشد.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر [name](#name) ارائه‌شده یک [نام معتبر عنصر سفارشی](#valid_custom_element_names) نباشد پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر سازنده ارجاع‌داده‌شده یک سازنده نباشد پرتاب می‌شود.

## Description

متد `define()` تعریفی از یک عنصر سفارشی را به ثبت عناصر سفارشی اضافه می‌کند؛ به این ترتیب نام عنصر به سازنده‌ای که برای ایجاد آن به کار می‌رود نگاشت می‌شود.

دو نوع عنصر سفارشی وجود دارد که می‌توانید ایجاد کنید:

- _عناصر سفارشی مستقل (Autonomous custom elements)_ عناصری مستقل هستند که از عناصر داخلی HTML ارث‌بری نمی‌کنند.
- _عناصر داخلی سفارشی‌سازی‌شده (Customized built-in elements)_ عناصری هستند که از عناصر داخلی HTML ارث‌بری می‌کنند و آن‌ها را گسترش می‌دهند.

برای تعریف یک عنصر سفارشی مستقل، باید پارامتر `options` را حذف کنید.

برای تعریف یک عنصر داخلی سفارشی‌سازی‌شده، باید پارامتر `options` را با ویژگی `extends` آن برابر با نام عنصر داخلی‌ای که در حال گسترش آن هستید عبور دهید؛ همچنین این نام باید با واسطی که تعریف کلاس عنصر سفارشی شما از آن ارث‌بری می‌کند مطابقت داشته باشد. برای مثال، برای سفارشی‌سازی عنصر {{htmlelement("p")}}، باید `{extends: "p"}` را به `define()` بدهید و تعریف کلاس عنصر شما باید از {{domxref("HTMLParagraphElement")}} ارث‌بری کند.

### Valid custom element names

نام‌های عناصر سفارشی باید:

- با یک حرف کوچک ASCII (a-z) شروع شوند
- شامل یک خط تیره (hyphen) باشند
- شامل هیچ حرف بزرگ ASCII نباشند
- شامل فاصله خالی ASCII، `NULL`، `/` یا `>` نباشند (به ترتیب U+0000، U+002F یا U+003E)
- هیچ‌کدام از موارد زیر نباشند:
  - "annotation-xml"
  - "color-profile"
  - "font-face"
  - "font-face-src"
  - "font-face-uri"
  - "font-face-format"
  - "font-face-name"
  - "missing-glyph"

## Examples

### تعریف یک عنصر سفارشی مستقل

کلاس زیر یک عنصر سفارشی مستقل حداقلی را پیاده‌سازی می‌کند:

```js
class MyAutonomousElement extends HTMLElement {
  constructor() {
    super();
  }
}
```

این عنصر هیچ کاری انجام نمی‌دهد؛ یک عنصر مستقل واقعی عملکرد خود را در سازنده و در بازخوردهای چرخه عمر (lifecycle callbacks) ارائه‌شده توسط استاندارد پیاده‌سازی می‌کند. برای کار با عناصر سفارشی، به [پیاده‌سازی یک عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) در راهنمای ما مراجعه کنید.

با این حال، تعریف کلاس بالا الزامات متد `define()` را برآورده می‌کند، بنابراین می‌توانیم آن را با کد زیر تعریف کنیم:

```js
customElements.define("my-autonomous-element", MyAutonomousElement);
```

سپس می‌توانیم آن را در یک صفحه HTML به این شکل استفاده کنیم:

```html
<my-autonomous-element>Element contents</my-autonomous-element>
```

### تعریف یک عنصر داخلی سفارشی‌سازی‌شده

کلاس زیر یک عنصر داخلی سفارشی‌سازی‌شده را پیاده‌سازی می‌کند:

```js
class MyCustomizedBuiltInElement extends HTMLParagraphElement {
  constructor() {
    super();
  }
}
```

این عنصر، عنصر داخلی {{htmlelement("p")}} را گسترش می‌دهد.

در این مثال حداقلی، عنصر هیچ سفارشی‌سازی‌ای را پیاده‌سازی نمی‌کند، بنابراین دقیقاً مانند یک عنصر معمولی `<p>` رفتار خواهد کرد. با این حال، الزامات `define()` را برآورده می‌کند، بنابراین می‌توانیم آن را به این شکل تعریف کنیم:

```js
customElements.define(
  "my-customized-built-in-element",
  MyCustomizedBuiltInElement,
  {
    extends: "p",
  },
);
```

سپس می‌توانیم آن را در یک صفحه HTML به این شکل استفاده کنیم:

```html
<p is="my-customized-built-in-element"></p>
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements)