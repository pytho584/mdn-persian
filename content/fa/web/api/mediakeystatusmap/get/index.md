---
title: "MediaKeyStatusMap: get() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MediaKeyStatusMap/get"
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

**`get()`** 方法属于 {{domxref("MediaKeyStatusMap")}} 接口，返回与给定键关联的状态值；如果不存在，则返回 `undefined`。

该状态值指示特定密钥是否可用于解密。

## 语法

```js-nolint
get(key)
```

### 参数

- `key`
  - : 需要返回其值的键。

### 返回值

一个字符串，指定与给定键关联的状态值；如果不存在，则为 `undefined`。

允许以下状态值：

- `usable`
  - : 该密钥当前可用于解密。
- `expired`
  - : 由于已超过到期时间，该密钥不再可用于解密。
- `released`
  - : 该密钥已被释放，CDM 不再可以使用它。但关于该密钥的信息仍然可用，例如许可证销毁的记录。
- `output-restricted`
  - : 基于指定的策略，该密钥存在输出限制。使用此密钥解密后的媒体数据可能会被阻止呈现。该状态表示源与输出（例如计算机与外接显示器）之间的连接不受信任。这可能表示源、中间设备和输出之间存在 HDCP 版本不匹配，或者 HDMI 线缆、视频分配器等中间连接设备损坏或不合规。应用程序可能会选择使用更高版本的 HDCP，或使用不需要如此高版本的内容。你还应检查中间设备和线缆是否支持 HDCP、是否牢固连接以及是否损坏。
- `output-downscaled`
  - : 基于指定的策略，该密钥存在输出限制，但如果以较低质量播放内容，这些限制可能会放宽。如果返回此值，应用程序可以以较低分辨率播放内容，也可以选择使用更高版本的 HDCP，或使用不需要如此高 HDCP 版本的其他内容。
- `usable-in-future`
  - : 一旦到达开始时间，该密钥将在未来可用于解密。
- `status-pending`
  - : 该密钥的状态尚不确定，正在确定中。
- `internal-error`
  - : 由于 CDM 中的错误，该密钥当前无法用于解密。应用程序无法处理此情况。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}