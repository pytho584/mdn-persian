---
title: "MediaKeys: setServerCertificate() method"
short-title: setServerCertificate()
slug: Web/API/MediaKeys/setServerCertificate
page-type: web-api-instance-method
browser-compat: api.MediaKeys.setServerCertificate
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

**`setServerCertificate()`** 方法属于 {{domxref("MediaKeys")}} 接口，用于提供服务器证书，以便对发送到许可证服务器的消息进行加密。

## 语法

```js-nolint
setServerCertificate(serverCertificate)
```

### 参数

- `serverCertificate`
  - : 一个 {{jsxref("ArrayBuffer")}}、{{jsxref("TypedArray")}} 或 {{jsxref("DataView")}} 对象，包含服务器证书。
    其内容由密钥系统决定。它绝不能包含可执行代码。

### 返回值

一个 {{jsxref('Promise')}}，会兑现为一个布尔值。如果此对象的内容解密模块所代表的密钥系统实现不支持服务器证书，则返回一个兑现为 `false` 的 Promise。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}