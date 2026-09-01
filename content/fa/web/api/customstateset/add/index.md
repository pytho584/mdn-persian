---
title: "CustomStateSet: add() method"
short-title: add()
slug: Web/API/CustomStateSet/add
page-type: web-api-instance-method
browser-compat: api.CustomStateSet.add
---

{{APIRef("Web Components")}}

`add` 方法属于 {{domxref("CustomStateSet")}} 接口，用于向 `CustomStateSet` 添加一个表示自定义状态的值。

具有特定状态的自定义元素可以通过 {{cssxref(":state()")}} 伪类进行选择，并将所需状态作为参数传递。

## 语法

```js-nolint
add(value)
```

### 参数

- `value`
  - : 表示自定义状态的字符串。

### 返回值

无（`undefined`）。

## 示例

以下函数将状态 `checked` 添加到 `CustomStateSet` 中。

```js
class MyCustomElement extends HTMLElement {
  set checked(flag) {
    if (flag) {
      this._internals.states.add("checked");
    }
  }
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}