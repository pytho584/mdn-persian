---
title: "CSSCounterStyleRule: suffix property"
short-title: suffix
slug: Web/API/CSSCounterStyleRule/suffix
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.suffix
---

{{APIRef("CSSOM")}}

**`suffix`** 属性属于 {{domxref("CSSCounterStyleRule")}} 接口，用于获取和设置 {{cssxref("@counter-style/suffix","suffix")}} 描述符的值。如果该描述符没有设置值，此属性返回空字符串。

## 值

一个字符串。

## 示例

以下示例展示了一条 {{cssxref("@counter-style")}} 规则。在 JavaScript 中，`myRules[0]` 就是这条 `@counter-style` 规则，访问 `suffix` 会返回值 ": "。

```css
@counter-style box-corner {
  system: fixed;
  symbols: ◰ ◳ ◲ ◱;
  suffix: ": ";
  negative: "-";
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].suffix); // ": "
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}