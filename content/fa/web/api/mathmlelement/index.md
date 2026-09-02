---
title: MathMLElement
slug: Web/API/MathMLElement
page-type: web-api-interface
browser-compat: api.MathMLElement
---

{{APIRef("MathML")}}

رابط **`MathMLElement`** نمایانگر هر عنصر [MathML](/en-US/docs/Web/MathML) است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌ها را از والد خود، {{DOMxRef("Element")}}، به ارث می‌برد._

- {{DOMxRef("MathMLElement.attributeStyleMap")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("StylePropertyMap")}} که اعلان‌های ویژگی `style` عنصر را نمایش می‌دهد.
- {{DOMxRef("MathMLElement.autofocus")}}
  - : مشخص می‌کند که آیا کنترل باید هنگام بارگذاری صفحه، یا وقتی یک {{htmlelement("dialog")}} یا [popover](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) نمایش داده می‌شود، فوکوس شود یا خیر.
- {{DOMxRef("MathMLElement.dataset")}} {{ReadOnlyInline}}
  - : یک شیء {{DOMxRef("DOMStringMap")}} که فهرستی از جفت‌های کلید/مقدار را برای ویژگی‌های داده نامدار فراهم می‌کند. این ویژگی‌ها با [ویژگی‌های داده سفارشی](/en-US/docs/Web/HTML/How_to/Use_data_attributes) متصل به عنصر متناظرند و با ویژگی‌های سراسری [`data-*`](/en-US/docs/Web/MathML/Reference/Global_attributes/data-*) در MathML مطابقت دارند.
- {{DOMxRef("MathMLElement.nonce")}}
  - : عدد رمزنگاری یکبارمصرف (nonce) را برمی‌گرداند که Content Security Policy برای تعیین اینکه آیا به یک واکشی مشخص اجازه ادامه داده می‌شود یا خیر، از آن استفاده می‌کند.
- {{DOMxRef("MathMLElement.style")}}
  - : یک {{DOMxRef("CSSStyleDeclaration")}} که اعلان‌های ویژگی `style` عنصر را نمایش می‌دهد.
- {{DOMxRef("MathMLElement.tabIndex")}}
  - : موقعیت عنصر در ترتیب پیمایش با Tab.

## متدهای نمونه

_این رابط همچنین متدها را از والد خود، {{DOMxRef("Element")}}، به ارث می‌برد._

- {{DOMxRef("MathMLElement.blur()")}}
  - : فوکوس صفحه‌کلید را از عنصر دارای فوکوس فعلی حذف می‌کند.
- {{DOMxRef("MathMLElement.focus()")}}
  - : عنصر را به فوکوس کنونی صفحه‌کلید تبدیل می‌کند.

## مثال‌ها

### MathML

```html
<math>
  <msqrt>
    <mi>x</mi>
  </msqrt>
</math>
```

### JavaScript

```js
document.querySelector("msqrt").constructor.name; // MathMLElement
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("Element")}}
- {{DOMxRef("HTMLElement")}}
- {{DOMxRef("SVGElement")}}
