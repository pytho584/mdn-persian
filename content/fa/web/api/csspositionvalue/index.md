```yaml
---
title: CSSPositionValue
slug: Web/API/CSSPositionValue
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPositionValue
```

{{deprecated_header}}{{APIRef("CSS Typed Object Model API")}}{{Non-standard_header}}

رابط **`CSSPositionValue`** از [API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Object_Model#css_typed_object_model) مقادیر مربوط به ویژگی‌هایی را نشان می‌دهد که یک موقعیت را دریافت می‌کنند، برای مثال {{cssxref('object-position')}}.

## سازنده

- {{domxref("CSSPositionValue.CSSPositionValue", "CSSPositionValue()")}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - یک شیء `CSSPositionValue` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref('CSSPositionValue.x')}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - موقعیت آیتم را در امتداد محور افقی صفحه وب برمی‌گرداند.
- {{domxref('CSSPositionValue.y')}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - موقعیت آیتم را در امتداد محور عمودی برمی‌گرداند.

## روش‌های نمونه

هیچکدام.

## نمونه‌ها

مثال زیر یک عنصر ظرف `<div>` را ۵ پیکسل از بالا و ۱۰ پیکسل از چپ صفحه قرار می‌دهد.

```js
const replacedEl = document.getElementById("image");
const position = new CSSPositionValue(CSS.px(35), CSS.px(40));

replacedEl.attributeStyleMap.set("object-position", position);
console.log(position.x.value, position.y.value);
console.log(replacedEl.computedStyleMap().get("object-position"));
```

ما ویژگی {{cssxref('object-position')}} را تنظیم می‌کنیم، سپس مقادیر بازگشتی را بررسی می‌کنیم.

```css hidden
#image {
  width: 300px;
  height: 300px;
  border: 1px solid black;
  background-color: #dededf;
  object-fit: none;
}
```

```html hidden
<p>
  Check the developer tools to see the log in the console and to inspect the
  style attribute on the image.
</p>
<img id="image" src="mdn.svg" alt="MDN Logo" />
```

{{EmbedLiveSample("Examples", 300, 300)}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('CSSImageValue')}}
- {{domxref('CSSKeywordValue')}}
- {{domxref('CSSNumericValue')}}
- {{domxref('CSSTransformValue')}}
- {{domxref('CSSUnparsedValue')}}
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)