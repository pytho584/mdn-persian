---
title: "ElementInternals: states property"
short-title: states
slug: Web/API/ElementInternals/states
page-type: web-api-instance-property
browser-compat: api.ElementInternals.states
---

{{APIRef("Web Components")}}

ویژگی فقط‌خواندنی **`states`** از رابط {{domxref("ElementInternals")}} یک {{domxref("CustomStateSet")}} برمی‌گرداند که وضعیت‌های ممکن عنصر سفارشی را نشان می‌دهد.

## مقدار

یک {{domxref("CustomStateSet")}} که یک {{jsxref("Set")}} از رشته‌هاست.

## نمونه‌ها

تابع زیر وضعیت `--checked` را به یک `CustomStateSet` اضافه و حذف می‌کند، و سپس با علامت‌زدن یا برداشتن علامت چک‌باکس سفارشی، `true` یا `false` را در کنسول چاپ می‌کند.

```js
class MyElement extends HTMLElement {
  set checked(flag) {
    if (flag) {
      this._internals.states.add("--checked");
    } else {
      this._internals.states.delete("--checked");
    }

    console.log(this._internals.states.has("--checked"));
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}