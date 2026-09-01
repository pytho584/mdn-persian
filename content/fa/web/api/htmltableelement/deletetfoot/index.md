---
title: "HTMLTableElement: deleteTFoot() method"
---

---
title: "HTMLTableElement: deleteTFoot() method"
short-title: deleteTFoot()
slug: Web/API/HTMLTableElement/deleteTFoot
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.deleteTFoot
---

{{APIRef("HTML DOM")}}

**`HTMLTableElement.deleteTFoot()`** 方法将一个给定 {{HtmlElement("table")}} 中的 {{HTMLElement("tfoot")}} 元素移除。

## 语法

```js-nolint
deleteTFoot()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

此示例使用 JavaScript 删除表格的页脚。

### HTML

```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Bob</td>
      <td>541</td>
    </tr>
    <tr>
      <td>Jim</td>
      <td>225</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>Average</th>
      <td>383</td>
    </tr>
  </tfoot>
</table>
```

### JavaScript

```js
let table = document.querySelector("table");
table.deleteTFoot();
```

### 结果

{{EmbedLiveSample("Examples")}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}