---
title: "HTMLTableCellElement: abbr property"
short-title: abbr
slug: Web/API/HTMLTableCellElement/abbr
page-type: web-api-instance-property
browser-compat: api.HTMLTableCellElement.abbr
---

{{ APIRef("HTML DOM") }}

**`abbr`** 是 {{domxref("HTMLTableCellElement")}} 接口的一个属性，表示与该单元格关联的缩写。如果单元格不是标题单元格 {{HTMLElement("th")}}，则忽略该属性。

它反映了 {{HTMLElement("th")}} 元素的 `abbr` 属性。

> [!NOTE]
> 此属性在浏览器中没有视觉效果。它提供的信息可帮助辅助技术（如屏幕阅读器）使用此缩写。

## 值

一个字符串。

## 示例

本示例在每个表格的第一列单元格中添加带有行标题相关联缩写的前缀。

### HTML

```html
<table>
  <thead>
    <tr>
      <th abbr="Maker">Manufacturer</th>
      <th abbr="Model">Car model</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Tesla</td>
      <td>3</td>
    </tr>
    <tr>
      <td>BYD</td>
      <td>Dolphin</td>
    </tr>
    <tr>
      <td>VW</td>
      <td>ID.3</td>
    </tr>
  </tbody>
</table>
```

```css hidden
table {
  border-collapse: collapse;
}

th,
td,
table {
  border: 1px solid black;
}

button {
  margin: 1em 1em 1em 0;
}
```

### JavaScript

```js
const rows = document.querySelectorAll("thead tr");
const cells = rows[0].cells;

for (const cell of cells) {
  cell.textContent = `${cell.textContent} (${cell.abbr})`;
}
```

### 结果

{{EmbedLiveSample("Examples", "100%", 220)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}