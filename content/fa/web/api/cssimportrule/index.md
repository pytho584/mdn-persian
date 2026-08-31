---
title: CSSImportRule
slug: Web/API/CSSImportRule
page-type: web-api-interface
browser-compat: api.CSSImportRule
---

{{APIRef("CSSOM")}}

**`CSSImportRule`** 接口表示一个 {{cssxref("@import")}} [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)。

{{InheritanceDiagram}}

## 实例属性

_继承其祖先 {{domxref("CSSRule")}} 的属性。_

- {{domxref("CSSImportRule.href")}} {{ReadOnlyInline}}
  - : 返回 {{cssxref("@import")}} 规则指定的 URL。
- {{domxref("CSSImportRule.layerName")}} {{ReadOnlyInline}}
  - : 返回 {{cssxref("@import")}} 规则中声明的[级联层](/en-US/docs/Web/CSS/Reference/At-rules/@layer)的名称；如果级联层是匿名的，则返回空字符串；如果规则未声明任何级联层，则返回 `null`。
- {{domxref("CSSImportRule.media")}}
  - : 返回关联样式表的 `media` 属性的值。
- {{domxref("CSSImportRule.styleSheet")}} {{ReadOnlyInline}}
  - : 返回关联的样式表。
- {{domxref("CSSImportRule.supportsText")}} {{ReadOnlyInline}}
  - : 返回 {{cssxref("@import")}} 规则指定的 supports 条件。

## 实例方法

_继承其祖先 {{domxref("CSSRule")}} 的方法。_

## 示例

该文档包含一个样式表，其中包含一条 {{cssxref("@import")}} 规则。因此，CSS 规则列表中的第一项将是一个 `CSSImportRule`。

```css
@import "style.css" screen;
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0]); // 一个 CSSImportRule 实例对象
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}