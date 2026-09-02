---
title: "Navigation: traverseTo() method"
slug: Web/API/Navigation/traverseTo
page-type: web-api-instance-method
browser-compat: api.Navigation.traverseTo
---

{{APIRef("Navigation API")}}

**`traverseTo()`** 方法属于 {{domxref("Navigation")}} 接口，用于导航到由给定 {{domxref("NavigationHistoryEntry.key", "key")}} 标识的 {{domxref("NavigationHistoryEntry")}}。

## 语法

```js-nolint
traverseTo(key)
traverseTo(key, options)
```

### 参数

- `key`
  - : 要导航到的 {{domxref("NavigationHistoryEntry")}} 的 `key`。
- `options` {{optional_inline}}
  - : 一个选项对象，包含以下属性：
    - `info` {{optional_inline}}
      - : 开发人员定义的信息，会传递给 {{domxref("Navigation/navigate_event", "navigate")}} 事件，并在 {{domxref("NavigateEvent.info")}} 中可用。该值可以是任意数据类型。例如，您可能希望根据导航方式（左滑、右滑或返回主页）以不同的动画显示新导航到的内容。可以在 `info` 中传入一个表示要使用哪种动画的字符串。

### 返回值

一个包含以下属性的对象：

- `committed`
  - : 一个 {{jsxref("Promise")}}，当可见 URL 发生变化且已创建新的 {{domxref("NavigationHistoryEntry")}} 时兑现。
- `finished`
  - : 一个 {{jsxref("Promise")}}，当 `intercept()` 处理程序返回的所有 Promise 都兑现时兑现。这等价于 {{domxref("NavigationTransition.finished")}} Promise 在 {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} 事件触发时兑现。

如果导航因某种原因失败，这两个 Promise 中的任何一个都会拒绝。

### 异常

- `InvalidStateError` {{domxref("DOMException")}}
  - : 如果 {{domxref("Navigation.currentEntry")}} 的 {{domxref("NavigationHistoryEntry.index")}} 值为 -1（表示当前 {{domxref("Document")}} 尚未激活），或者导航历史列表中不包含具有指定 `key` 的 {{domxref("NavigationHistoryEntry")}}，或者当前 {{domxref("Document")}} 正在卸载，则抛出该异常。

## 示例

### 设置主页按钮

```js
function initHomeBtn() {
  // 获取第一个加载条目的 key，
  // 以便用户始终可以回到此视图。
  const { key } = navigation.currentEntry;
  backToHomeButton.onclick = () => {
    navigation.traverseTo(key);
  };
}
// 拦截导航事件（例如链接点击），
// 并将其替换为单页导航
navigation.addEventListener("navigate", (event) => {
  event.intercept({
    async handler() {
      // 导航到不同视图，
      // 但“主页”按钮始终有效。
    },
  });
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [现代客户端路由：Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API 解释器](https://github.com/WICG/navigation-api/blob/main/README.md)