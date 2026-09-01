---
title: "CSSMathProduct: values property"
short-title: values
slug: Web/API/CSSMathProduct/values
page-type: web-api-instance-property
browser-compat: api.CSSMathProduct.values
---

{{APIRef("CSS Typed Object Model API")}}{{AvailableInWorkers}}

**`values`** 是 {{domxref("CSSMathProduct")}} 接口的只读属性，返回一个 {{domxref("CSSNumericArray")}}，其中包含被相乘在一起的 {{domxref("CSSNumericValue")}} 对象。

## 值

一个 {{domxref('CSSNumericArray')}}。

## 示例

### 基本用法

以下代码创建了一个 `CSSMathProduct` 对象，并记录其 `values` 和长度。

```js
const product = new CSSMathProduct(CSS.px(10), CSS.percent(50));

console.log(product.values);
// CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, length: 2}
console.log(product.values.length); // 2
```

然后我们遍历 `values`，记录它们的类型、值、单位以及字符串化后的文本。每一项都与传入构造函数的 {{domxref("CSSNumericValue")}} 对象（或其表示的乘法/除法运算的项）顺序一致。

```js
for (const value of product.values) {
  console.log(
    `${value.constructor.name}: ${value.value} ${value.unit} (${value})`,
  );
}

// CSSUnitValue: 10 px (10px)
// CSSUnitValue: 50 percent (50%)
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}