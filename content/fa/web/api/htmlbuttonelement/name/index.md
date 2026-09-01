---
title: "HTMLButtonElement: name property"
short-title: name
slug: Web/API/HTMLButtonElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.name
---

{{ApiRef("HTML DOM")}}

**`name`** 属性属于 {{domxref("HTMLButtonElement")}} 接口，表示 {{HTMLElement("button")}} 元素的名称；如果元素没有名称，则为空字符串。它反映了元素的 [`name`](/en-US/docs/Web/HTML/Reference/Elements/button#name) 属性。

## 值

一个字符串，表示元素的名称。

## 示例

```js
const buttonElement = document.querySelector("#myButton");
console.log(`Element's name: ${buttonElement.name}`);
buttonElement.name = "newName";
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("HTMLButtonElement.value")}}
- {{domxref("HTMLButtonElement.type")}}
```