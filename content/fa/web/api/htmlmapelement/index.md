---
title: "HTMLMapElement"
---

---
title: HTMLMapElement
slug: Web/API/HTMLMapElement
page-type: web-api-interface
browser-compat: api.HTMLMapElement
---

{{ APIRef("HTML DOM") }}

接口 **`HTMLMapElement`** 提供了特殊的属性和方法（除了其通过继承自普通对象 {{domxref("HTMLElement")}} 接口可用的那些之外），用于操作 map 元素的布局和呈现。

{{InheritanceDiagram}}

## 实例属性

_继承其父级 {{domxref("HTMLElement")}} 的属性。_

- {{domxref("HTMLMapElement.name")}}
  - : 一个字符串，表示 {{HTMLElement("map")}} 元素，用于在其他上下文中引用它。如果设置了 `id` 属性，则此属性的值必须与之相同；并且它不能为 `null` 或空字符串。
- {{domxref("HTMLMapElement.areas")}} {{ReadOnlyInline}}
  - : 一个实时的 {{domxref("HTMLCollection")}}，表示与此 {{HTMLElement("map")}} 关联的 {{HTMLElement("area")}} 元素。

## 实例方法

_没有特定方法；继承其父级 {{domxref("HTMLElement")}} 的方法。_

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 实现此接口的 HTML 元素：{{ HTMLElement("map") }}。