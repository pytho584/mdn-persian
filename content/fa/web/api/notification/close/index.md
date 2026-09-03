---
title: "Notification: close() method"
short-title: close()
slug: Web/API/Notification/close
page-type: web-api-instance-method
browser-compat: api.Notification.close
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

**`close()`** 方法用于关闭/移除先前显示的通知，该接口属于 {{domxref("Notification")}}。

> [!NOTE]
> 此 API 不应当仅用于在固定延迟后将通知从屏幕上移除，因为此方法还会将通知从任何通知托盘中移除，从而阻止用户与通知进行交互。此 API 的合理用途是移除不再相关的通知（例如，在消息应用中用户已在网页上阅读了通知，或在音乐应用中下一首歌已经开始播放）。

## 语法

```js-nolint
close()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

在下面的代码片段中，我们有一个函数，当被调用时会创建一个 `options` 对象，然后创建一个新通知。在函数末尾，它还在 {{domxref("EventTarget.addEventListener","addEventListener()")}} 函数内调用 `close()`，以便在网页上相关内容被阅读后移除该通知。

```js
function spawnNotification(theBody, theIcon, theTitle) {
  const options = {
    body: theBody,
    icon: theIcon,
  };

  const n = new Notification(theTitle, options);
  document.addEventListener("visibilitychange", () => {
    if (document.visibilityState === "visible") {
      // The tab has become visible so clear the now-stale Notification.
      n.close();
    }
  });
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用通知 API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)