---
title: "Element: insertAdjacentText() method"
short-title: insertAdjacentText()
slug: Web/API/Element/insertAdjacentText
page-type: web-api-instance-method
browser-compat: api.Element.insertAdjacentText
---

{{APIRef("DOM")}}

متد **`insertAdjacentText()`** از رابط {{domxref("Element")}}، با دریافت یک موقعیت نسبی و یک رشته، یک گره متنی جدید را در موقعیت داده‌شده نسبت به عنصری که از آن فراخوانی شده است، درج می‌کند.

## نحو (Syntax)

```js-nolint
insertAdjacentText(where, data)
```

### پارامترها

- `where`
  - : رشته‌ای که موقعیت نسبت به عنصر فراخوانی‌کننده متد را مشخص می‌کند؛ باید یکی از رشته‌های زیر باشد:
    - `'beforebegin'`: قبل از خود `element`.
    - `'afterbegin'': درست درون `element`، قبل از اولین فرزند آن.
    - `'beforeend'`: درست درون `element`، بعد از آخرین فرزند آن.
    - `'afterend'`: بعد از خود `element`.

- `data`
  - : رشته‌ای که از آن یک گره متنی جدید برای درج در موقعیت `where` نسبت به عنصر فراخوانی‌کننده متد ساخته می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر `where` یک مقدار مجاز نباشد، پرتاب می‌شود.

### نمایش بصری موقعیت‌ها

```html
<!-- beforebegin -->
<p>
  <!-- afterbegin -->
  foo
  <!-- beforeend -->
</p>
<!-- afterend -->
```

> [!NOTE]
> موقعیت‌های `beforebegin` و `afterend` تنها زمانی کار می‌کنند که گره در درخت (DOM) باشد و یک عنصر والد داشته باشد.

## مثال‌ها

```js
beforeBtn.addEventListener("click", () => {
  para.insertAdjacentText("afterbegin", textInput.value);
});

afterBtn.addEventListener("click", () => {
  para.insertAdjacentText("beforeend", textInput.value);
});
```

نمایش [insertAdjacentText.html](https://mdn.github.io/dom-examples/insert-adjacent/insertAdjacentText.html) را در GitHub ببینید (همچنین [کد منبع](https://github.com/mdn/dom-examples/blob/main/insert-adjacent/insertAdjacentText.html)). در اینجا یک پاراگراف ساده داریم. می‌توانید متنی را در عنصر فرم وارد کنید، سپس دکمه‌های _Insert before_ و _Insert after_ را فشار دهید تا آن را با استفاده از `insertAdjacentText()` قبل یا بعد از متن پاراگراف موجود درج کنید. توجه کنید که گره متنی موجود تغییر نمی‌کند – گره‌های متنی جدید حاوی افزوده‌های جدید ایجاد می‌شوند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("Element.insertAdjacentHTML()")}}