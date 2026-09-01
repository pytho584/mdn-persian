---
title: "ElementInternals: ariaControlsElements property"
short-title: ariaControlsElements
slug: Web/API/ElementInternals/ariaControlsElements
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaControlsElements
---

{{APIRef("DOM")}}

**`ariaControlsElements`** 属性是 {{domxref("ElementInternals")}} 接口的一个数组，其中包含由应用该属性的元素所控制的一个或多个元素。
例如，可以在 [combobox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)（组合框）上设置该属性，以指示其弹出的元素；或在 [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)（滚动条）上设置，以指示其控制的元素的 ID。

关于如何正确使用该属性与特性的更多信息，请参阅 [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) 主题。

## 值

一个由 {{domxref("HTMLElement")}} 子类组成的数组，表示由该元素控制的元素。

读取时，返回的数组是静态且只读的。
写入时，所赋的数组会被复制：之后对该数组的修改不会影响此属性的值。

## 描述

该属性是使用 [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) 特性来设置受控元素的一种灵活替代方案。
与 `aria-controls` 不同，赋给此属性的元素不需要具有 [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) 特性。

当 [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) 特性存在时，此属性会反映该特性，但仅限于与作用域内有效元素匹配的、被列出的引用 `id` 值。
如果设置了此属性，则对应的特性会被清除。
有关反映的元素引用和作用域的更多信息，请参阅 _反射特性_ 指南中的 [元素引用反射](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) 特性
- {{domxref("Element.ariaControlsElements")}}
- _特性反射_ 指南中的 [元素引用反射](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)