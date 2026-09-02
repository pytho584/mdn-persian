---
title: "MediaDevices: getSupportedConstraints() method"
short-title: getSupportedConstraints()
slug: Web/API/MediaDevices/getSupportedConstraints
page-type: web-api-instance-method
browser-compat: api.MediaDevices.getSupportedConstraints
---

{{APIRef("Media Capture and Streams")}}{{SecureContext_Header}}

**`getSupportedConstraints()`** 方法属于 {{domxref("MediaDevices")}} 接口，它返回一个基于 {{domxref("MediaTrackSupportedConstraints")}} 字典的对象，该对象的每个成员字段分别指定了 {{Glossary("user agent")}}（用户代理）所理解的一个可约束属性。

## 语法

```js-nolint
getSupportedConstraints()
```

### 参数

无。

### 返回值

返回一个新的对象，它基于 {{domxref("MediaTrackSupportedConstraints")}} 字典，列出用户代理支持的约束。由于列表中只包含用户代理支持的约束，因此这些布尔属性中的每一个都具有值 `true`。

## 示例

此示例输出浏览器支持的约束列表。

```html hidden
<p>The following media constraints are supported by your browser:</p>

<ul id="constraintList"></ul>
```

```css hidden
body {
  font:
    15px "Arial",
    sans-serif;
}
```

```js
const constraintList = document.querySelector("#constraintList");
const supportedConstraints = navigator.mediaDevices.getSupportedConstraints();

for (const constraint of Object.keys(supportedConstraints)) {
  const elem = document.createElement("li");
  elem.appendChild(document.createElement("code")).textContent = constraint;
  constraintList.appendChild(elem);
}
```

### 结果

{{ EmbedLiveSample('Examples', 600, 350) }}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}