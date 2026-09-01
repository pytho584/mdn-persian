---
title: CSSValue
slug: Web/API/CSSValue
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.CSSValue
---

{{APIRef("CSSOM")}}{{Deprecated_Header}}{{non-standard_header}}

**`CSSValue`** 接口表示 CSS 属性的当前计算值。

> [!NOTE]
> 该接口曾是创建类型化 CSS 对象模型（Typed CSS Object Model）尝试的一部分。该尝试已被放弃，且大多数浏览器并未实现它。
>
> 为实现您的目的，您可以使用：
>
> - 被广泛支持的[非类型化 CSS 对象模型](/en-US/docs/Web/API/CSS_Object_Model)，或
> - 较新且支持较少的[现代 CSS 类型化对象模型 API](/en-US/docs/Web/API/CSS_Typed_OM_API)（仍被视为实验性）。

## 实例属性

- {{DOMxRef("CSSValue.cssText")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : 表示当前值的字符串。
- {{DOMxRef("CSSValue.cssValueType")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : 一个 `unsigned short`，表示定义值类型的代码。可能的值有：

    | 常量                 | 描述                                                                                                                                                                                                                          |
    | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | `CSS_CUSTOM`         | 该值为自定义值。                                                                                                                                                                                                              |
    | `CSS_INHERIT`        | 该值为继承值，且 `cssText` 包含 `"inherit"`。                                                                                                                                                                                 |
    | `CSS_PRIMITIVE_VALUE`| 该值为原始值，且可通过在 `CSSValue` 接口的此实例上使用绑定特定的类型转换方法，获得 {{DOMxRef("CSSPrimitiveValue")}} 接口的实例。                                                                                                |
    | `CSS_VALUE_LIST`     | 该值为一个 `CSSValue` 列表，且可通过在 `CSSValue` 接口的此实例上使用绑定特定的类型转换方法，获得 {{DOMxRef("CSSValueList")}} 接口的实例。                                                                                     |

## 规范

该特性最初定义在 [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) 规范中，但此后已从任何标准化工作中移除。

它已被一个现代但不兼容的、现已进入标准轨道的 [CSS 类型化对象模型 API](/en-US/docs/Web/API/CSS_Typed_OM_API) 所取代。

## 浏览器兼容性

{{Compat}}

## 参见

- {{DOMxRef("CSSPrimitiveValue")}}
- {{DOMxRef("CSSValueList")}}