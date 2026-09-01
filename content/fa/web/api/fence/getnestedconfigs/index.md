---
title: "Fence: getNestedConfigs() method"
short-title: getNestedConfigs()
slug: Web/API/Fence/getNestedConfigs
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Fence.getNestedConfigs
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

**`getNestedConfigs()`** 方法属于 {{domxref("Fence")}} 接口，返回嵌入在当前 `<fencedframe>` 中的 `<fencedframe>` 所加载的 {{domxref("FencedFrameConfig")}} 配置列表。

## 语法

```js-nolint
getNestedConfigs()
```

### 参数

无。

### 返回值

`getNestedConfigs()` 有两种可能的返回值：

- 如果当前 `<fencedframe>` 的配置是使用支持嵌套配置的 API（例如 [Protected Audience](https://privacysandbox.google.com/private-advertising/protected-audience)）创建的，则返回包含 20 个 {{domxref("FencedFrameConfig")}} 对象的数组。在这 20 个配置中，前 N 个是经由该 API 注册的配置，其余为填充（padding）配置，它们将导航到 `about:blank`，从而隐藏配置数量，避免泄露任何信息。
- 如果当前 `<fencedframe>` 的配置是使用不支持嵌套配置的 API（例如 [Shared Storage](/en-US/docs/Web/API/Shared_Storage_API)）创建的，则返回 `null`。

## 示例

```js
// Run inside a <fencedframe>

// Retrieve the configs of embedded fenced frames
const configs = window.fence.getNestedConfigs();

// Set a new fenced frame's config to equal one of the retrieved configs
const frame = document.createElement("fencedframe");
frame.config = configs[0];
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) 位于 privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) 位于 privacysandbox.google.com