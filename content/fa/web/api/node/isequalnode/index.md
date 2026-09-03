---
title: "Node: isEqualNode() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Node/isEqualNode"
---

---
title: "Node: isEqualNode() method"
short-title: isEqualNode()
slug: Web/API/Node/isEqualNode
page-type: web-api-instance-method
browser-compat: api.Node.isEqualNode
---

{{APIRef("DOM")}}

**`isEqualNode()`** 方法属于 {{domxref("Node")}} 接口，用于测试两个节点是否相等。
当两个节点具有相同的类型、相同的定义特征（对于元素而言，包括其 ID、子节点数量等）、相同的属性等，则认为它们相等。需要匹配的具体数据点集合会根据节点类型的不同而有所变化。

## 语法

```js-nolint
isEqualNode(otherNode)
```

### 参数

- `otherNode`
  - : 要与当前节点进行相等性比较的 {{domxref("Node")}}。
    > [!NOTE]
    > 此参数不是可选的，但可以设置为 `null`。

### 返回值

一个布尔值，如果两个节点相等则返回 `true`，否则返回 `false`。
如果 `otherNode` 为 `null`，则 `isEqualNode()` 始终返回 `false`。

## 示例

在此示例中，我们创建了三个 {{HTMLElement("div")}} 块。第一个和第三个具有相同的内容和属性，而第二个则不同。然后我们运行一些 JavaScript，使用 `isEqualNode()` 比较这些节点并输出结果。

### HTML

```html
<div>这是第一个元素。</div>
<div>这是第二个元素。</div>
<div>这是第一个元素。</div>

<p id="output"></p>
```

```css hidden
#output {
  width: 440px;
  border: 2px solid black;
  border-radius: 5px;
  padding: 10px;
  margin-top: 20px;
  display: block;
}
```

### JavaScript

```js
const output = document.getElementById("output");
const divList = document.getElementsByTagName("div");

output.innerText += `div 0 与 div 0 相等：${divList[0].isEqualNode(
  divList[0],
)}\n`;
output.innerText += `div 0 与 div 1 相等：${divList[0].isEqualNode(
  divList[1],
)}\n`;
output.innerText += `div 0 与 div 2 相等：${divList[0].isEqualNode(
  divList[2],
)}\n`;
```

### 结果

{{ EmbedLiveSample('Example', "100%", "210") }}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("Node.isSameNode()")}}