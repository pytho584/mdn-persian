---
title: "GPUCommandEncoder: resolveQuerySet() method"
short-title: resolveQuerySet()
slug: Web/API/GPUCommandEncoder/resolveQuerySet
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.resolveQuerySet
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`resolveQuerySet()`** 方法属于 {{domxref("GPUCommandEncoder")}} 接口，用于编码一条命令，将 {{domxref("GPUQuerySet")}} 中的查询结果解析并复制到指定的 {{domxref("GPUBuffer")}} 中。

## 语法

```js-nolint
resolveQuerySet(querySet, firstQuery, queryCount, destination, destinationOffset)
```

### 参数

- `querySet`
  - : 一个 {{domxref("GPUQuerySet")}} 对象，表示要解析的查询集。
- `firstQuery`
  - : 第一个要复制到缓冲区的查询值的索引编号。
- `queryCount`
  - : 从 `firstQuery` 开始，要复制到缓冲区的查询数量。
- `destination`
  - : 一个 {{domxref("GPUBuffer")}} 对象，表示用于接收查询值的目标缓冲区。
- `destinationOffset`
  - : 一个数字，表示从缓冲区起始位置开始写入查询值的偏移量（以字节为单位）。

### 返回值

无（{{jsxref("undefined")}}）。

### 验证条件

调用 **`resolveQuerySet()`** 时必须满足以下条件，否则会生成一个 {{domxref("GPUValidationError")}}，并且该 {{domxref("GPUCommandEncoder")}} 将变为无效：

- `destination.buffer` 的 {{domxref("GPUBuffer.usage")}} 必须包含 `GPUBufferUsage.QUERY_RESOLVE` 标志。
- `firstQuery` 必须小于 `querySet` 中的查询总数。
- `firstQuery + queryCount` 必须小于或等于 `querySet` 中的查询总数。
- `destinationOffset` 必须是 256 的倍数。
- `destinationOffset + 8 × queryCount` 必须小于或等于 `destination.size`。

## 示例

```js
// …

const queryBuffer = device.createBuffer({
  size: 1024,
  usage: GPUBufferUsage.QUERY_RESOLVE,
});

const querySet = device.createQuerySet({
  type: "timestamp",
  count: 32,
});

// …

const commandEncoder = device.createCommandEncoder();

// 向 querySet 写入时间戳
commandEncoder.writeTimestamp(querySet, 0);
// …
commandEncoder.writeTimestamp(querySet, 1);
// 等等

// …

commandEncoder.resolveQuerySet(
  querySet,
  0, // 要写入的第一个查询
  16, // 要计数的查询数量
  queryBuffer,
  0, // 缓冲区偏移量
);

// …
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)