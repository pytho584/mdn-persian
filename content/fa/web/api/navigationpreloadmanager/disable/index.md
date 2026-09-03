---
title: "NavigationPreloadManager: disable() method"
short-title: disable()
slug: Web/API/NavigationPreloadManager/disable
page-type: web-api-instance-method
browser-compat: api.NavigationPreloadManager.disable
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`disable()`** 方法属于 {{domxref("NavigationPreloadManager")}} 接口，用于停止先前通过 {{domxref("NavigationPreloadManager.enable()","enable()")}} 启动的由 service worker 管理的资源的自动预加载。它返回一个解析为 `undefined` 的 promise。

该方法可以在 service worker 的 `activate` 事件处理器中调用（在 `fetch` 事件处理器可以被调用之前）。

## 语法

```js-nolint
disable()
```

### 参数

无。

### 返回值

一个解析为 {{jsxref('undefined')}} 的 {{jsxref("Promise")}}。

### 异常

- `InvalidStateError` {{domxref("DOMException")}}
  - : 当没有与这个 {{domxref("NavigationPreloadManager")}} 所属的注册（registration）关联的活动 worker 时抛出。

## 示例

以下代码展示了如何禁用预加载，首先使用 {{domxref("ServiceWorkerRegistration.navigationPreload")}} 来测试其是否受支持。

```js
addEventListener("activate", (event) => {
  event.waitUntil(
    (async () => {
      if (self.registration.navigationPreload) {
        // Disable navigation preloads!
        await self.registration.navigationPreload.disable();
      }
    })(),
  );
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("NavigationPreloadManager.enable()")}}