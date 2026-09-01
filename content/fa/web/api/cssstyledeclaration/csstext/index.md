---
title: "CSSStyleDeclaration: cssText property"
short-title: cssText
slug: Web/API/CSSStyleDeclaration/cssText
page-type: web-api-instance-property
browser-compat: api.CSSStyleDeclaration.cssText
---

{{APIRef("CSSOM")}}

ویژگی **`cssText`** در رابط {{domxref("CSSStyleDeclaration")}}، متنِ اعلان استایل **درونخطی (inline)** عنصر را بازمی‌گرداند یا تنظیم می‌کند.

برای تنظیم پویای یک قانون **stylesheet**، به [استفاده از اطلاعات استایل پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information) مراجعه کنید.

این ویژگی را با {{domxref("CSSRule.cssText")}} که مربوط به قانون‌های استایل در stylesheet است اشتباه نگیرید.

## مقدار

یک رشته (string) شامل متنِ اعلان استایل درونخطی عنصر.

## مثال

```html
<span id="s1" style="color: red;">Some text</span>
```

```js
const elem = document.getElementById("s1");
console.log(elem.style.cssText); // "color: red;"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}