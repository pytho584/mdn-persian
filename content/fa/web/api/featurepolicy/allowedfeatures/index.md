---
title: "FeaturePolicy: allowedFeatures() method"
short-title: allowedFeatures()
slug: Web/API/FeaturePolicy/allowedFeatures
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.FeaturePolicy.allowedFeatures
---

{{APIRef("Feature Policy API")}}{{SeeCompatTable}}{{non-standard_header}}

**`allowedFeatures()`** 方法属于 {{DOMxRef("FeaturePolicy")}} 接口，返回一个包含所有被 [权限策略](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) 允许的功能指令名称的列表。这使得我们可以检查其所运行的权限策略中的各个指令。因此，`allowedFeatures()` 方法返回的是 {{DOMxRef("FeaturePolicy.features", "features()")}} 所返回指令的一个子集。

## 语法

```js-nolint
allowedFeatures()
```

### 参数

无。

### 返回值

一个字符串数组，表示调用该方法的权限策略所允许的权限策略指令名称。

## 示例

以下示例会记录当前文档所有被允许的指令。请注意，如果用户尚未授予相应的权限，这些功能可能仍会受到 Permissions API 的限制。

```js
// 首先，获取权限策略对象
const featurePolicy = document.featurePolicy;

// 然后查询特定功能
const allowed = featurePolicy.allowedFeatures();

for (const directive of allowed) {
  console.log(directive);
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}