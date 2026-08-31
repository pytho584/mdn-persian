---
title: "CloseWatcher: destroy() method"
short-title: destroy()
slug: Web/API/CloseWatcher/destroy
page-type: web-api-instance-method
browser-compat: api.CloseWatcher.destroy
---

{{APIRef("HTML DOM")}}

**`destroy()`** 方法属于 {{domxref("CloseWatcher")}} 接口，用于停用关闭监视器（close watcher）。当相关 UI 元素以除“关闭”之外的其他方式被拆除时，应调用此方法。

停用之后，这个 `CloseWatcher` 将不再接收 `cancel` 或 `close` 事件，并且可以创建新的独立 `CloseWatcher` 实例。

## 语法

```js-nolint
destroy()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

### 使用 `destroy()` 方法

使用 `destroy()` 方法釋放监视器实例以进行清理。

```js
watcher.destroy();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}