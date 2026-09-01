---
title: CSSViewTransitionRule
slug: Web/API/CSSViewTransitionRule
page-type: web-api-interface
browser-compat: api.CSSViewTransitionRule
---

{{APIRef("CSSOM")}}

**`CSSViewTransitionRule`** 接口表示一条 CSS {{cssxref("@view-transition")}} [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)。

{{InheritanceDiagram}}

## 实例属性

_继承自其祖先 {{domxref("CSSRule")}} 的属性。_

- {{domxref("CSSViewTransitionRule.navigation", "navigation")}} {{readonlyinline}}
  - : 返回 `@view-transition` at-rule 的 `navigation` 描述符值。
- {{domxref("CSSViewTransitionRule.types", "types")}} {{readonlyinline}}
  - : 返回一个数组，包含 `@view-transition` at-rule 的 `types` 描述符值。

## 实例方法

_继承自其祖先 {{domxref("CSSRule")}} 的方法。_

## 示例

### 基本用法

样式表中包含一条 {{cssxref("@view-transition")}} [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)，并设置了 `navigation` 和 `types` 描述符：

```css
@view-transition {
  navigation: auto;
  types: slide, rotate;
}
```

在脚本中，我们通过 `document.styleSheets[0].cssRules` 获取对 `@view-transition` at-rule 的引用，然后将相应的 `CSSViewTransitionRule` 对象及其 `navigation` 和 `types` 属性记录到控制台。`types` 属性返回一个数组，包含为 `types` 描述符设置的值。

```js
let myRule = document.styleSheets[0].cssRules;
console.log(myRule[0]); // a CSSViewTransitionRule representing the @view-transition at-rule
console.log(myRule[0].navigation); // "auto"
console.log(myRule[0].types); // ["slide", "rotate"]
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{cssxref("@view-transition")}}
- [View Transition API](/en-US/docs/Web/API/View_Transition_API)