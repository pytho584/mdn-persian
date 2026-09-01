---
title: "HTMLAnchorElement: hash property"
short-title: hash
slug: Web/API/HTMLAnchorElement/hash
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.hash
---

{{ APIRef("HTML DOM") }}

**`hash`** 属性属于 {{domxref("HTMLAnchorElement")}} 接口，是一个字符串，包含 `"#"` 后跟 `<a>` 元素的 `href` 的片段标识符。如果 URL 没有片段标识符，此属性包含空字符串 `""`。

更多信息请参见 {{domxref("URL.hash")}}。

## 值

一个字符串。

## 示例

### 从锚链接获取 hash

给定以下 HTML：

```html
<a id="myAnchor" href="/en-US/docs/Web/API/HTMLAnchorElement/hash#examples">
  Examples
</a>
```

你可以这样获取锚点的 hash：

```js
const anchor = document.getElementById("myAnchor");
anchor.hash; // '#examples'
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 其所属的 {{domxref("HTMLAnchorElement")}} 接口。