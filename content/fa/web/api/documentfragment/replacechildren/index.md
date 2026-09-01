---
title: "DocumentFragment: replaceChildren() method"
short-title: replaceChildren()
slug: Web/API/DocumentFragment/replaceChildren
page-type: web-api-instance-method
browser-compat: api.DocumentFragment.replaceChildren
---

{{APIRef("DOM")}}

**`DocumentFragment.replaceChildren()`** 方法用一组指定的新子节点替换 `DocumentFragment` 现有的子节点。这些新子节点可以是字符串或 {{domxref("Node")}} 对象。

## 语法

```js-nolint
replaceChildren(param1)
replaceChildren(param1, param2)
replaceChildren(param1, param2, /* …, */ paramN)
```

### 参数

- `param1`, …, `paramN`
  - : 一组 {{domxref("Node")}} 对象或字符串，用于替换 `DocumentFragment` 现有的子节点。如果未指定任何替换对象，则 `DocumentFragment` 的所有子节点都将被清空。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : 当违反[节点树的约束](https://dom.spec.whatwg.org/#concept-node-tree)时抛出。

## 示例

### 清空文档片段

`replaceChildren()` 提供了一种非常便捷的机制，用于清空文档片段中的所有子节点。你可以在不指定任何参数的情况下对文档片段调用它：

```js
let fragment = new DocumentFragment();
let div = document.createElement("div");
let p = document.createElement("p");
fragment.append(p);
fragment.prepend(div);

fragment.children; // HTMLCollection [<div>, <p>]

fragment.replaceChildren();

fragment.children; // HTMLCollection []
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("DocumentFragment.prepend()")}}
- {{domxref("DocumentFragment.append()")}}