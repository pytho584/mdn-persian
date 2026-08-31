---
title: "CSSKeyframesRule: appendRule() method"
short-title: appendRule()
slug: Web/API/CSSKeyframesRule/appendRule
page-type: web-api-instance-method
browser-compat: api.CSSKeyframesRule.appendRule
---

{{APIRef("CSSOM")}}

**`appendRule()`** 方法属于 {{domxref("CSSKeyframeRule")}} 接口，用于将一条 {{domxref("CSSKeyFrameRule")}} 追加到规则列表的末尾。

## 语法

```js-nolint
appendRule(rule)
```

### 参数

- `rule`
  - : 一个包含关键帧规则的字符串。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

CSS 中包含一个关键帧 at-rule。它将是 `document.styleSheets[0].cssRules` 返回的第一个 {{domxref("CSSRule")}}。
`myRules[0]` 返回一个 {{domxref("CSSKeyframesRule")}} 对象。返回 `cssRules` 属性会得到一个包含一条规则的 {{domxref("CSSRuleList")}}。

使用 `appendRule` 追加另一条规则后，`cssRules` 属性返回的 {{domxref("CSSRuleList")}} 将包含两条规则。

```css
@keyframes slide-in {
  from {
    transform: translateX(0%);
  }
}
```

```js
let myRules = document.styleSheets[0].cssRules;
let keyframes = myRules[0]; // 一个 CSSKeyframesRule 对象
keyframes.appendRule("to {transform: translateX(100%);}");
console.log(keyframes.cssRules); // 一个包含两条规则的 CSSRuleList 对象
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}