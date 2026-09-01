---
title: "CSSPrimitiveValue: setFloatValue() method"
short-title: setFloatValue()
slug: Web/API/CSSPrimitiveValue/setFloatValue
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPrimitiveValue.setFloatValue
---

{{APIRef("CSSOM")}}{{deprecated_header}}{{non-standard_header}}

**`setFloatValue()`** 方法属于 {{domxref("CSSPrimitiveValue")}} 接口，用于设置一个浮点数值。如果绑定到该值的属性无法接受指定的单位或该浮点值，则值不会改变，并会抛出一个 {{domxref("DOMException")}}。

> [!NOTE]
> 此方法曾是构建类型化 CSS 对象模型（Typed CSS Object Model）尝试的一部分。该尝试已被放弃，大多数浏览器未实现此方法。
>
> 为了实现你的目标，你可以使用：
>
> - 被广泛支持的 [CSS 对象模型](/en-US/docs/Web/API/CSS_Object_Model)（非类型化），或
> - 较新的 [CSS 类型化对象模型 API](/en-US/docs/Web/API/CSS_Typed_OM_API)（支持较少，且被视为实验性）。

## 语法

```js-nolint
setFloatValue(unitType, floatValue)
```

### 参数

- `unitType`
  - : 一个 `unsigned short`，表示单位类型的编码，用于指定返回数值的单位。有效值为：

    | 常量              | 描述                                                                                                                  |
    | ----------------- | --------------------------------------------------------------------------------------------------------------------- |
    | `CSS_CM`          | 值为以厘米（centimeters）为单位的 {{cssxref("&lt;length&gt;")}}。                                                      |
    | `CSS_DEG`         | 值为以度（degrees）为单位的 {{cssxref("&lt;angle&gt;")}}。                                                             |
    | `CSS_DIMENSION`   | 值为带有未知尺寸的 {{cssxref("&lt;number&gt;")}}。                                                                     |
    | `CSS_EMS`         | 值为以 em 为单位的 {{cssxref("&lt;length&gt;")}}。                                                                     |
    | `CSS_EXS`         | 值为以 ex 为单位的 {{cssxref("&lt;length&gt;")}}。                                                                     |
    | `CSS_GRAD`        | 值为以百分度（grads）为单位的 {{cssxref("&lt;angle&gt;")}}。                                                           |
    | `CSS_HZ`          | 值为以赫兹（Hertz）为单位的 {{cssxref("&lt;frequency&gt;")}}。可使用 `getFloatValue` 方法获取该值。                    |
    | `CSS_IN`          | 值为以英寸（inches）为单位的 {{cssxref("&lt;length&gt;")}}。                                                           |
    | `CSS_KHZ`         | 值为以千赫兹（Kilohertz）为单位的 {{cssxref("&lt;frequency&gt;")}}。                                                   |
    | `CSS_MM`          | 值为以毫米（millimeters）为单位的 {{cssxref("&lt;length&gt;")}}。                                                      |
    | `CSS_MS`          | 值为以毫秒（milliseconds）为单位的 {{cssxref("&lt;time&gt;")}}。                                                       |
    | `CSS_NUMBER`      | 值为一个简单的 {{cssxref("&lt;number&gt;")}}。                                                                         |
    | `CSS_PC`          | 值为以派卡（picas）为单位的 {{cssxref("&lt;length&gt;")}}。                                                            |
    | `CSS_PERCENTAGE`  | 值为一个 {{cssxref("&lt;percentage&gt;")}}。                                                                            |
    | `CSS_PT`          | 值为以磅（points）为单位的 {{cssxref("&lt;length&gt;")}}。                                                              |
    | `CSS_PX`          | 值为以像素（pixels）为单位的 {{cssxref("&lt;length&gt;")}}。                                                             |
    | `CSS_RAD`         | 值为以弧度（radians）为单位的 {{cssxref("&lt;angle&gt;")}}。                                                           |
    | `CSS_S`           | 值为以秒（seconds）为单位的 {{cssxref("&lt;time&gt;")}}。                                                              |

- `floatValue`
  - : 一个 `float`，表示新的浮点数值。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col"><strong>类型</strong></th>
      <th scope="col"><strong>描述</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>DOMException</code></td>
      <td>
        如果 CSS 值不包含浮点数值，或者字符串值无法转换为指定的单位，则会抛出
        <code>INVALID_ACCESS_ERR</code> 错误。<br />如果该属性是只读的，则会抛出
        <code>NO_MODIFICATION_ALLOWED_ERR</code> 错误。
      </td>
    </tr>
  </tbody>
</table>

## 规范

此功能最初在 [DOM Style Level 2](https://www.w3.org/TR/DOM-Level-2-Style/) 规范中定义，但此后已从所有标准化工作中移除。

它已被一个现代但不兼容的 [CSS 类型化对象模型 API](/en-US/docs/Web/API/CSS_Typed_OM_API) 所取代，该 API 目前正在标准轨道上。

## 浏览器兼容性

{{Compat}}