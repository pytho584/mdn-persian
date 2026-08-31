---
title: "CSSCounterStyleRule: system property"
short-title: system
slug: Web/API/CSSCounterStyleRule/system
page-type: web-api-instance-property
browser-compat: api.CSSCounterStyleRule.system
---

{{APIRef("CSSOM")}}

**`system`** 属性属于 {{domxref("CSSCounterStyleRule")}} 接口，用于获取和设置 {{cssxref("@counter-style/system", "system")}} 描述符的值。如果描述符未设置值，该属性将返回空字符串。

## 值

一个字符串。

## 示例

以下示例展示了一个 {{cssxref("@counter-style")}} 规则。在 JavaScript 中，`myRules[0]` 指代这条 `@counter-style` 规则，访问 `system` 将返回 "fixed"。

```css
@counter-style box-corner {
  system: fixed;
  symbols: ◰ ◳ ◲ ◱;
  suffix: ": ";
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].system); // "fixed"
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}