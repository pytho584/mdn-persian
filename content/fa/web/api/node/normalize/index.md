---
title: "Node: normalize() method"
short-title: normalize()
slug: Web/API/Node/normalize
page-type: web-api-instance-method
browser-compat: api.Node.normalize
---

{{APIRef("DOM")}}

**`normalize()`** 方法属于 {{domxref("Node")}} 接口，会将指定节点及其整个子树规范化为 _规范化_ 形式。在规范化的子树中，子树中的文本节点不会为空，也不会存在相邻的文本节点。

## 语法

```js-nolint
normalize()
```

### 参数

无。

### 返回值

无。

## 示例

```html
<output id="result"></output>
```

```js
const wrapper = document.createElement("div");

wrapper.appendChild(document.createTextNode("Part 1 "));
wrapper.appendChild(document.createTextNode("Part 2 "));

let node = wrapper.firstChild;
let result = "Before normalization:\n";
while (node) {
  result += ` ${node.nodeName}: ${node.nodeValue}\n`;
  node = node.nextSibling;
}

wrapper.normalize();

node = wrapper.firstChild;
result += "\n\nAfter normalization:\n";
while (node) {
  result += ` ${node.nodeName}: ${node.nodeValue}\n`;
  node = node.nextSibling;
}

const output = document.getElementById("result");
output.innerText = result;
```

{{ EmbedLiveSample("Example", "100%", "170")}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("Text.splitText()")}}，其作用与此方法相反。