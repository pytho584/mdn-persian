---
title: "CSSPageRule: selectorText property"
short-title: selectorText
slug: Web/API/CSSPageRule/selectorText
page-type: web-api-instance-property
browser-compat: api.CSSPageRule.selectorText
---

{{APIRef("CSSOM")}}

**`selectorText`** 属性属于 {{domxref("CSSPageRule")}} 接口，用于获取和设置与 `CSSPageRule` 关联的选择器。

## 值

一个字符串。

## 示例

该样式表包含两条 {{cssxref("@page")}} 规则。`selectorText` 属性会将 `:first` 的字面选择器文本以字符串形式返回。

```css
@page {
  margin: 1cm;
}

@page :first {
  margin: 2cm;
}
```

```js
const myRules = document.styleSheets[0].cssRules; // Two myRules
console.log(myRules[1].selectorText); // ":first"
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}