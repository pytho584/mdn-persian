---
title: "HTMLElement: attributeStyleMap property"
short-title: attributeStyleMap
slug: Web/API/HTMLElement/attributeStyleMap
page-type: web-api-instance-property
browser-compat: api.HTMLElement.attributeStyleMap
---

{{APIRef("CSSOM")}}

**`attributeStyleMap`** 是 {{domxref("HTMLElement")}} 接口的只读属性，返回一个实时的 {{domxref("StylePropertyMap")}} 对象，其中包含元素内联 `style` 属性中定义的样式属性列表，或通过脚本使用 {{domxref("HTMLElement")}} 接口的 {{domxref("HTMLElement.style", "style")}} 属性赋值的样式属性。

简写属性会被展开。例如，如果你设置 `border-top: 1px solid black`，实际设置的是对应的详细属性：{{cssxref("border-top-color")}}、{{cssxref("border-top-style")}} 和 {{cssxref("border-top-width")}}。

{{domxref("HTMLElement.style", "style")}} 属性与 `attributeStyleMap` 属性的主要区别在于：`style` 属性返回 {{domxref("CSSStyleDeclaration")}} 对象，而 `attributeStyleMap` 属性返回 {{domxref("StylePropertyMap")}} 对象。

虽然该属性本身不可写，但你可以通过它返回的 {{domxref("StylePropertyMap")}} 对象来读写内联样式，就像通过 `style` 属性返回的 {{domxref("CSSStyleDeclaration")}} 对象一样。

## 值

一个实时的 {{domxref("StylePropertyMap")}} 对象。

## 示例

以下代码片段展示了 `style` 属性与 `attributeStyleMap` 属性之间的关系：

```html
<div id="el" style="border-top: 1px solid blue; color: red;">
  An example element
</div>
<div id="output"></div>
```

```css
#el {
  font-size: 16px;
}

#output {
  white-space: pre-line;
}
```

```js
const element = document.getElementById("el");
const output = document.getElementById("output");

for (const property of element.attributeStyleMap) {
  output.textContent += `${property[0]} = ${property[1][0].toString()}\n`;
}
```

{{EmbedLiveSample("Examples", "200", "200")}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("HTMLElement.style")}}
- {{domxref("SVGElement.attributeStyleMap")}}
- {{domxref("MathMLElement.attributeStyleMap")}}