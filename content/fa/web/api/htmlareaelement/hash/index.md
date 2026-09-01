---
title: "HTMLAreaElement: hash property"
short-title: hash
slug: Web/API/HTMLAreaElement/hash
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.hash
---

{{ APIRef("HTML DOM") }}

**`hash`** 属性属于 {{domxref("HTMLAreaElement")}} 接口，是一个字符串，包含 `"#"` 后跟 `<area>` 元素的 `href` 中的片段标识符。如果 URL 中没有片段标识符，则该属性包含空字符串 `""`。

更多信息请参见 {{domxref("URL.hash")}}。

## 值

一个字符串。

## 示例

### 从 area 链接中获取 hash

给定以下 HTML：

```html
<map name="infographic">
  <area
    id="mdn-circle"
    shape="circle"
    coords="130,136,60"
    href="https://developer.mozilla.org/#ExampleSection"
    alt="MDN" />
</map>

<img
  usemap="#infographic"
  src="/media/examples/mdn-info.png"
  alt="MDN infographic" />
```

你可以这样获取 area 链接的 hash：

```js
const area = document.getElementById("mdn-circle");
area.hash; // '#ExampleSection'
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 其所属的 {{domxref("HTMLAreaElement")}} 接口。